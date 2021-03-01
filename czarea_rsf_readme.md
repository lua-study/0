#RSF

&emsp;&emsp;一个高可用、高性能、轻量级的分布式服务框架。支持容灾、负载均衡、集群。一个典型的应用场景是，将同一个服务部署在多个`Server`上提供 request、response 消息通知。

&emsp;&emsp;使用RSF可以点对点调用，也可以分布式调用。部署方式上：可以搭配注册中心，也可以独立使用。

----------
### 工作原理
![工作原理](http://project.hasor.net/resources/224933_BV6Q_1166271.jpg)

----------
### RSF架构设计
![RSF架构](http://project.hasor.net/resources/002011_mz60_1166271.jpg)

----------
### Center架构设计
![RsfCenter架构设计](http://project.hasor.net/resources/002011_mz60_1166271.jpg)

----------
### Demo
	 
	 
		 net.hasor 
		 rsf-core 
		 1.0.0-SNAPSHOT 
	 

	 
	 
		 
		 
			 
				 rsf://127.0.0.1:2177  
			 
		 
	 

	//Server
	Hasor.createAppContext("server-config.xml", new RsfModule() {
	    @Override
	    public void loadRsf(RsfContext rsfContext) throws Throwable {
	        RsfBinder rsfBinder = rsfContext.binder();
	        rsfBinder.rsfService(EchoService.class).toInstance(new EchoServiceImpl()).register();
	    }
	});

	//Client
	AppContext clientContext = Hasor.createAppContext("client-config.xml", new RsfModule() {
	    @Override
	    public void loadRsf(RsfContext rsfContext) throws Throwable {
	        RsfBinder rsfBinder = rsfContext.binder();
	        rsfBinder.rsfService(EchoService.class).register();
	    }
	});
	RsfClient client = clientContext.getInstance(RsfClient.class);
	EchoService echoService = client.wrapper(EchoService.class);
	String res = echoService.sayHello("Hello Word");
	System.out.println(res);

----------
### 相关连接

* WebSite：[http://www.hasor.net](http://www.hasor.net)
* Issues：[http://git.oschina.net/teams/hasor/issues](http://git.oschina.net/teams/hasor/issues)
* Team：[http://team.oschina.net/hasor](http://team.oschina.net/hasor)
* QQ群：193943114

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)