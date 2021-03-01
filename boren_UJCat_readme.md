![](https://img.shields.io/badge/jdk-1.8-green.svg)  ![](https://img.shields.io/badge/Netty-4.0.52-orange.svg)
# UJCat
基于netty4的极简易上手网络框架
## 说明
- 自己的项目需要网络通讯，但不会socket 怎么办？没问题

除了设置ip和端口外，该框架在使用的时候几乎不用去管网络层，这款框架的目的在于让使用者尽量写自己的业务逻辑，而网络层就算完全不会也没有任何问题。适用于socket通讯初学者或者需要socket通讯的小项目。
## 如何操作
- 会不会很难操作或对接自己项目？

当然不会，该框架的网络层和业务层使用反射的方式去对接，使用者只需要继承其**业务类**就可以了， 这里的**业务类**不是什么特别难的东西，你只需要注意三个回调事件就可以了，这三个分别作用是：

- **msgService(String var1, String var2)** ： 当收到消息后 会调用这个方法 其中**var1**是消息的协议码，对你没看错都是string，该框架传输的数据类型是以string作为基础的，**var2**是消息具体内容，也就是说，当UJCat收到消息后会主动执行这个方法并传入消息的内容，你可以将你的处理消息的模块放到里面。

- **exception(int var1)** ： 当连接发生了故障后自动执行，其中传入的参数是故障类型，其实你只需要知道当有人拔网线，断网，主动断开等就会自动执行这个方法。

- **active()** ： 当连接成功后会自动执行该方法。

除了以上3个必须实现的方法外，还有一个发送消息的方法：**sendMsg(String head, String body)** ,你想要发送消息只需要调用次方法就可以了，传参不用多说，head是消息头可以用来写你的消息协议，body是消息内容。以上是基本方法，此外有一个属性可以值得使用者关注，那就是每一个继承了该业务类都只要连接成功都会由一个唯一的key，你可以通过这个**userKey**去管理你的网络连接对象或者说你的服务器用户。

## 代码示例

这里以一个简单的服务器为例，这个服务器规则很简单收到用户消息后直接返回给用户，要注意的是服务器的业务类是**MessageSelect** 你的业务逻辑需要继承它，客户端的业务类名称是**ClientService** 同样的 他是一个业务类，特性都是一样的，你只需要注意什么时候继承哪一个就好，下面是代码：

       public class TestServerSelect extends MessageSelect {
        
            @Override
        	public void msgService(String var1, String var2) {
        		System.out.println("用户 " + userKey + " 发送了消息: [消息头] " + var1 + "   [消息内容] " + var2);
        		sendMsg("0", "服务器以收到你的消息! : " + var2);
        	}
        
        	@Override
    	public void exception(int var1) {
    		System.out.println("用户 " + userKey + " 与服务器断开");
    	}
    
        	@Override
        	public void active() {
        		System.out.println("用户 " + userKey + " 以连接到服务器");
        	}
        }

以上就是一个服务器所有所有代码，是不是很简单？？

现在我们的服务器写好了，开始运行一下，一下是网络框架启动的代码示例：

    public static void main(String[] args) throws InterruptedException {
        //创建一个服务器对象
    	UJServer b = new UJServer();
        //设置端口，同时将刚才写好的服务器业务类 添加进来
        b.setServer(8099, TestServerSelect.class);
        //启动服务器
        b.ServiceStart();
    }

这里我们的服务器监听8099端口，同时将刚才写好的类的class文件传入进去让后启动就大功告成!!，下面我用客户端测试一下服务器效果，客户端代码我就不贴出来了，思路和服务器端一样，也是写一个业务层，添加到客户端类然后启动。
![启动服务器][1]


  ![当客户端连接进来][2]


  ![当客户端发送消息并且退出][3]


  [1]: https://s1.ax1x.com/2017/11/22/2xrKe.png "启动服务器"
  [2]: https://s1.ax1x.com/2017/11/22/2xybd.png "当客户端连接进来"
  [3]: https://s1.ax1x.com/2017/11/22/2xcVA.png "当客户端发送消息并且退出"
  
  以上就是一个简单的应答服务器。
  
## 需要注意的
该通讯框架的客户端与服务器之间有一个加密验证环节，加密器解密器都包含在了项目中，如果你只用其中的服务器或客户端，你的另外一端需要写加密解密验证。

## 最后
该服务器由于限制用户最底层的消息类型是string而方便操作但是也因此效率相对变低了，由于基于Netty4，所以在多用户高并发上面比较稳定，一般的小项目或者新手想自己写一些带有网络通讯的项目都可以用该框架，目前这是一个早期版本，还有很多需要优化，会变得越来越稳定和简单易用，Unity版本的客户端过一段时间会更新，同时api也会慢慢完善。希望大家支持！

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)