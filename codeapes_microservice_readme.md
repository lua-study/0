# microservice

#### 介绍
微服务框架自学习版本

- 注册中心采用：Nacos
- 配置中心采用：Nacos Config
- 路由网关采用：Spring cloud gateway
- 应用容器采用：Undertow

#### 实现辅助功能
- 基于Nacos的路由网关配置监听，当Nacos配置中心相关Data变更时，会自动更新网关路由指向
- 基于Controller上的GatewayRoute注解，便于在编写相关服务时就直接指定路由信息，并且在应用启动的时候会自动注册相关路由信息至Nacos配置中心，之后会触发路由网关的自更新

#### 其他说明
- 相关文件夹中包含application的就说明它是一个入口类应用，其他的都为辅助模块

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)