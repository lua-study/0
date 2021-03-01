# SelfSignalR
SignalR聊天室
Asp.net SignalR是微软为实现实时通信的一个类库。一般情况下，SignalR会使用JavaScript的长轮询(long polling)的方式来实现客户端和服务器通信，随着Html5中WebSockets出现，SignalR也支持WebSockets通信。另外SignalR开发的程序不仅仅限制于宿主在IIS中，也可以宿主在任何应用程序，包括控制台，客户端程序和Windows服务等，另外还支持Mono，这意味着它可以实现跨平台部署在Linux环境下。
SignalR内部有两类对象：
Http持久连接(Persisten Connection)对象：用来解决长时间连接的功能。还可以由客户端主动向服务器要求数据，而服务器端不需要实现太多细节，只需要处理PersistentConnection 内所提供的五个事件：OnConnected, OnReconnected, OnReceived, OnError 和 OnDisconnect 即可。
Hub（集线器）对象：用来解决实时(realtime)信息交换的功能，服务端可以利用URL来注册一个或多个Hub，只要连接到这个Hub，就能与所有的客户端共享发送到服务器上的信息，同时服务端可以调用客户端的脚本。
　　SignalR将整个信息的交换封装起来，客户端和服务器都是使用JSON来沟通的，在服务端声明的所有Hub信息，都会生成JavaScript输出到客户端，.NET则依赖Proxy来生成代理对象，而Proxy的内部则是将JSON转换成对象。
  
  从上面的介绍可以看出，SignalR既然是为实时而生的，这样就决定了其使用场所。具体适用情景有如下几点：

1、聊天室，如在线客服系统，IM系统等
2、股票价格实时更新
3、消息的推送服务
4、游戏中人物位置的实时推送

我的这个项目中主要介绍第一条。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)