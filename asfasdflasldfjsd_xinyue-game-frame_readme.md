# xinyue-game-frame

## 心悦游戏框架
------------------------------------------------------------------------------------------------------------------------
### 主要使用的技术框架

unity3d,protobuf
Spring Boot,Spring cloud,Netty,RocketMQ,Protobuf

### 客户端实现（game-frame-client）  
1. 客户端基本Unity3d开发，unity版本是2019.3.1f
2. 实现了的Http Json通信，可以方便的发送和解析与服务器交互的Json数据
3. 实现了长连接Socket通信，与网关建立Socket连接。
4. 使用Protobuf做为协议编码。
6. 实现了心跳管理网络连接的各个状态：正在连接，连接成功，连接失败，重新连接
7. 与服务器一同使用，实现了用户的登陆与注册功能
8. 与服务器一同使用，实现了角色创建的功能

### 服务器实现(game-frame-server)

1. 服务器基于Spring Cloud框架实现分布式服务，可以动态扩展，
2. 使用Nacos实现服务治理，服务启动时自动注册。
3. 使用RocketMQ消息队列实现服务器内部服务通信。
4. 与客户端一起使用，实现了用户的登陆与注册
5. 与客户端一起使用，实现了角色的创建
6. 数据库是Mongodb和redis，redis做为二级缓存，数据先从redis中获取，如果redis不存在所要的数据，再从数据库查询。
7. 网关基于Netty实现,实现了Socket通信，断包粘包处理，心跳管理,消息分发
8. 实现了网关的负载均衡，可以部署多个网关。
9. 数据库连接基于spring-data-mongodb实现
10. 服务端业务架构已实现了消息的顺序处理，引入项目之后，可以直接接收客户端请求，并处理业务内容。

### 通信层-Protobuf编码

使用Protobuf编码协议，实现了通信消息的对象封装，可以方便的定义网络通信协议，不需要关心底层网络的实现，数据对象可以直接在业务中使用。


### 项目工程介绍

* Web服务网关(xinyue-game-web-gateway)

1. 实现请求服务的跳转。 
2. 实现登陆用户统一权限验证
3. 可以独立启动

* 游戏中心服务(xinyue-game-center)

1. 实现用户的注册与登陆，生成用户的token。 
2. 实现多游戏网关的管理，用户进入游戏时，负载网关的负载均衡。
3. 可以独立启动

* 游戏网关(xinyue-game-gateway)

1. 与客户端建立长连接，并对连接进行认证。
2. 实现通信内容加密和解密(待添加)
3. 负责客户端请求的路由和转发
4. 客户端请求限流(待添加)
5. 可以独立启动

* 系统负载均衡管理(xinyue-game-server-balance)

  主要负责用户请求的目标服务的负载均衡，支持同一个服务的多实例服务。

* 协议对象封装(xinyue-game-network-message)

  实现网络通信协议消息的封装，包括网关与客户端的交互协议和网关与内部服务交互的协议。

* 消息和分布式事件系统(xinyue-game-mq-system)

  基于RocketMQ消息队列组件，实现服务端内部系统之间的网络通信。

* 数据存储封装(xinyue-game-dao)

1. 实现Redis做为二级缓存的封装，数据访问的时候先访问redis，如果redis中没有，再访问数据库。
2. 实现数据库配置的封装。并实现数据库异步访问的封装。方便项目中的使用。

* 游戏服务框架(xinyue-game-logic-frame)

1. 实现与网关的相互通信。
2. 实现用户请求的线程封装，让同一个用户的请求都在同一个线程中处理。
3. 实现客户端消息处理的分发，将协议消息和处理方法映射起来，让开发者直接处理业务内容而不用关心底层通信的实现。

* 公共项目(xinyue-game-common)

实现基本的公共工具类集合，方便多个项目依赖和使用，减少重复代码。

### 服务整体架构

![服务整体架构](https://images.gitee.com/uploads/images/2020/0322/223737_3e419f4e_23677.png "屏幕截图.png")

## 项目部署方式

### 安装基础服务

1. 安装Nacos-服务发现与注册服务
2. 安装RocketMQ-消息服务
3. 安装MongoDB
4. 安装Redis

### 单服务方式

![单服务部署](https://images.gitee.com/uploads/images/2020/0322/224126_e73a9df1_23677.png "屏幕截图.png")

### 终极部署方式

![终极部署方式](https://images.gitee.com/uploads/images/2020/0322/225552_cd07e9d1_23677.png "屏幕截图.png")



更多信息，可以关注公众号获取

![欢迎关注公众号](https://images.gitee.com/uploads/images/2020/0307/145153_d26d192a_23677.png "QQ截图20191104223446.png")

QQ群交流：66728073，197321069

基于此框架实现的一款小游戏源码：[https://gitee.com/wgslucky/fishing-hunter](https://gitee.com/wgslucky/fishing-hunter)

游戏案例下载体验：[http://www.xinyues.com](http://www.xinyues.com)


 **_谢赏_** 

 

![微信赏](https://images.gitee.com/uploads/images/2020/0307/154538_834a1c88_23677.png "weixinpay.png")
![支付宝赏](https://images.gitee.com/uploads/images/2020/0307/154557_1c872fd7_23677.png "zhifubaopay.png")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)