**znet是NIO通讯小框架，功能上有点类似netty与mina，是zbus消息总线的通讯基础项目，**

##为什么没有选择netty或者mina？

个人观点：netty与mina过于庞大，需要学习的成本比较高，debug中的chain过长，自己不方便改写

##znet对JAVA NIO通讯做了个简单的封装
核心目标：
 
* 1) **具备多线程单机扩容能力--尽量吃完CPU**
* 2) **应用上层简单扩展，快速搞定高效Server与同步异步Client**

尽管这两个目标也是netty与mina的目标之一，但是znet将更加简洁，方便二次个性化修改

## 性能欢迎大家给数据:)，跟机器有关

[性能ISSUE](http://git.oschina.net/rushmore/znet/issues/1 "perf") 

[性能测试代码](http://git.oschina.net/rushmore/znet/tree/master/src/test/java/org/zstacks/znet/perf "perf_code") 


##znet应用项目

[zbus消息队列、服务总线](http://git.oschina.net/rushmore/zbus "zbus") 

[zwall DMZ安全隔离](http://git.oschina.net/rushmore/zwall "zwall") 




##设计概要

Dispatcher管理SelectorThread线程生命周期，通过IoAdaptor暴露编码解码消与网络事件处理。

Dispatcher+SelectorThread+Session组成的 **引擎** 提供了 “【目标1】多线程单机扩容能力”

IoAdaptor扩展应用提供了“【目标2】快速搞定高效Server与同步异步Client”.

![znet-archit](http://git.oschina.net/uploads/images/2015/0520/092839_1bf13569_7458.png "ZNET概念设计图")

默认提供IoAdaptor的实现，默认采用HTTP兼容协议--KV头部+Binary消息体。一般来说应用只需要个性化IoAdaptor。比如zbus消息总线就是一个案例。


## maven依赖

	 
		 org.zstacks 
		 znet 
		 6.1.0 
	 



## 示例： 简单编写一个高性能NIO Server
	

	public class MyRemotingServer extends RemotingServer{ 
		public MyRemotingServer(int port, Dispatcher dispatcher) throws IOException {  
			super(port, dispatcher);
			this.initHandlers();
		} 
		//个性化定义Message中的那部分解释为命令，这里为了支持浏览器直接访问，把Message中的path理解为command
		@Override
		public String findHandlerKey(Message msg) { 
			String cmd = msg.getCommand();
			if(cmd == null){
				cmd = msg.getPath();
			}
			return cmd;
		}
		private void initHandlers(){
			//注册命令处理Callback
			this.registerHandler("hello", new MessageHandler() {
				public void handleMessage(Message msg, Session sess) throws IOException {
					//System.out.println(msg);
					msg.setStatus("200");   
					msg.setBody("hello world");
					sess.write(msg);
				}
			});
		} 
		@SuppressWarnings("resource")
		public static void main(String[] args) throws Exception {    
			Dispatcher dispatcher = new Dispatcher()
				.selectorCount(1)   //Selector线程数配置
				.executorCount(16); //Message后台处理线程数配置
			
			MyRemotingServer server = new MyRemotingServer(80, dispatcher);
	    	server.start(); 
	    	//dispatcher.close(); 
		}
	}
	
上面这段代码就完成了一个简单的高性能NIO Server的编写，并且可以在浏览器中直接调用 http://localhost/hello 因为znet的MessageCodec直接兼容了HTTP协议。

## 示例： 简单编写一个高性能NIO Client

	public class MyRemotingClient {
		@SuppressWarnings("resource")
		public static void main(String[] args) throws Exception { 
			//1)创建Dispatcher
			final Dispatcher dispatcher = new Dispatcher(); 
			//2)建立链接
			final RemotingClient client = new RemotingClient("127.0.0.1:80", dispatcher);
			
			Message msg = new Message();
			msg.setCommand("hello");
			msg.setBody("hello world");
			
			client.invokeAsync(msg, new ResultCallback() {
				@Override
				public void onCompleted(Message result) { 
					System.out.println(result); 
				}
			});
		}
	}

## 同步异步客户端，连接池等应用代码示例

[UseCase](http://git.oschina.net/rushmore/znet/tree/master/src/test/java/org/zstacks/znet/usecase "usecase") 



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)