![输入图片说明](http://assets.processon.com/chart_image/5e85e93be4b034045678eb0d.png "体系架构")

(1) Server
Server表示整个的Catalina Servlet容器。Tomcat提供了Server接口的一个默认实现，这通
常不需要用户自己去实现。在Server容器中，可以包含一个或多个Service组件。

(2) Service
Service是存活在Server内部的中间组件，它将一个或多个连接器（Connector）组件绑定到
一个单独的引擎（Engine）上。在Server中，可以包含一个或多个Service组件。Service也
很少由用户定制，Tomcat提供了Service接口的默认实现，而这种实现既简单又能满足应
用。

(3) Connector
连接器（Connector）处理与客户端的通信，它负责接收客户请求，以及向客户返回响应结
果。在Tomcat中，有多个连接器可以使用。

(4) Engine
在Tomcat中，每个Service只能包含一个Servlet引擎（Engine）。引擎表示一个特定的
Service的请求处理流水线。作为一个Service可以有多个连接器，引擎从连接器接收和处理
所有的请求，将响应返回给适合的连接器，通过连接器传输给用户。用户允许通过实现
Engine接口提供自定义的引擎，但通常不需要这么做。

(5) Host
Host表示一个虚拟主机，一个引擎可以包含多个Host。用户通常不需要创建自定义的
Host，因为Tomcat给出的Host接口的实现（类StandardHost）提供了重要的附加功能。

(6) Context
一个Context表示了一个Web应用程序，运行在特定的虚拟主机中。什么是Web应用程序
呢？在Sun公司发布的Java Servlet规范中，对Web应用程序做出了如下的定义：“一个Web
应用程序是由一组Servlet、HTML页面、类，以及其他的资源组成的运行在Web服务器上的
完整的应用程序。它可以在多个供应商提供的实现了Servlet规范的Web容器中运行”。一个
Host可以包含多个Context（代表Web应用程序），每一个Context都有一个唯一的路径。用
户 通 常 不 需 要 创 建 自 定 义 的 Context ， 因 为 Tomcat 给 出 的 Context 接 口 的 实 （ 类
StandardContext）提供了重要的附加功能。
凡是实现了Servlet规范的都可以成为Servlet容器

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)