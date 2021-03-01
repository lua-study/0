# message-trunk
====================

![License](https://img.shields.io/cocoapods/l/TWPhotoPicker.svg)
![Platform](https://img.shields.io/badge/platform-java-yellow.svg)
> **message-trunk**是基于java开发的轻量级消息总线框架。 

框架开发宗旨：项目内的轻量级消息队列。
框架开发目的：在项目内部，我们常常需要做异步操作，常规的做法是提交给线程池去做，这样会导致一些：

* 线程池大小不可控，任务可能因为线程池满了被抛弃。
* 任务执行失败没有重试机制。
* 任务执行失败没有统一的异常处理。

为了解决如上问题，基于redis的队列开发了该消息队列，具有如下特点： 

* 足够轻量级，队列配置简单，只要使用redis即可，不需要额外部署环境；
* 支持分布式，任务提交后由多台机器分布式处理，机器资源分配合理；
* 处理效率高，任务交给多线程并发处理； 
* 处理有重试机制，并且可自定义错误处理。
* 对于小型数据入队列，出队列效率高。

  
## Installation
maven依赖：
```
 
 
     wang.moshu 
     mt-framework 
     0.0.2 
 
```


## DEMO

运行mt-demo，打开index.jsp运行测试例子。演示地址：
简单测试：http://123.206.202.189:8080/mt-demo/index.jsp
性能测试(1核1G小机器，亲请别测试性能，已经被玩挂N次了，下载到机器上测试性能哦)：http://localhost:8080/mt-demo/index-benchmark.jsp

## Requirements

* java 6.0+ 


## License

message-trunk is available under the Apache license, see the LICENSE file for more information.

## 使用指南

### 1.消息入队列
获取消息队列全局对象MessageTrunk（可以用spring注入），put入消息即可。

```
        // 获取MessageTrunk实例
        MessageTrunk mt = (MessageTrunk) SpringBeanUtils.getBean("messageTrunk");

        Message  message = new Message (MessageType.DEMO_MESSAGE, new DemoMessage(value));
        // 消息入MT
        mt.put(message);
```

### 2. 处理消息
消息处理器：继承AbstarctMessageHandler抽象类。

```
	public class DemoHandler extends AbstarctMessageHandler 
{
	private static Log logger = LogFactory.getLog(DemoHandler.class);

	public DemoHandler()
	{
		// 说明该handler监控的消息类型
		super(MessageType.DEMO_MESSAGE);
	}

	/**
	 * 监听到消息后处理方法
	 */
	@Override
	public void handle(DemoMessage message)
	{
        // do handle
	}

	@Override
	public void handleFailed(DemoMessage obj)
	{
		// handle failed
	}

}
```

## 实现原理
基本原理是redis的阻塞取命令： Blpop，该命令移出并获取列表的第一个元素， 如果列表没有元素会阻塞列表直到等待超时或发现可弹出元素为止。

## 性能测试（[测试链接][1]）
测试环境：本人开发机器，4核i5，16GB内存，tomcat和redis在同一台机器
测试结果：最高写入消息速度为57208 ops
![输入图片说明](http://git.oschina.net/uploads/images/2017/0328/233047_3182d86b_50648.png "在这里输入图片标题")


  [1]: http://123.206.202.189:8080/mt-demo/index-benchmark.jsp

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)