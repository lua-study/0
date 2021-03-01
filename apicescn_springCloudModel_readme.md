### README


   这是SpringCloudModel是作者初学SpringCloud的一个样例，集中包含了EUREKA单机配置与集群配置方法，Config配置服务中心的配置以及config-Client客户端的配置。
   其中web-server是config-Client客户端应用,集成事件消息总线服务BUS，是一个典型的Web应用端。
   cloud-Ribbone为服务消费者与hystrix容错管理,断路器,延迟和故障服务的应用.
   集成了SpringCloud大部分的组件与子项目，同时数据库采用集成mongoDB与oracle11G结合。

### 更新说明:

- 版本V1.05

    增加Docker功能，实现Docker部署。（在使用eureka集群的Dockerfile时，需注意使用-net参数来进行，否则服务将不能自动注册到集群的 Eureka中，只能注册到其中一个.）

``
- 版本V1.04

    增加安全认证模块，OAuth2的功能，实现web用户的权限认证(未完成！)。
    
``    
- 版本V1.03
    
    增加cloud-Hystrix工程，是实现hystrix Dashboard及Turbine仪表图展示功能，不过在启动该应用时需要运行一次接口访问，否则Turbine将只会看到一个ping，Turbine将会报连接不上。

``
- 版本V1.02
    
    增加kafka与Zookeeper的绑定与依赖，其中在config-service与web-service中加入，此两项运行时，需要启动kafka与Zookeeper服务端方可使用，学习初期可先注释这两块内容。
    kafka与Zookeeper服务端的搭建与启动不在本教程范围，请自行查阅其他资料。

``
- 版本V1.01

    增加了Kafka配置，在Config-service中增加，进行全局消息总线服务。
    同时在config-service启用eureka健康检查，解决Eureka的自我保护模块的警告信息；同时解决当微服务失效时Eureka服务自动将其踢出。
    （本实例参照[http://bbs.springcloud.cn/d/1-dd-spring-cloud](http://bbs.springcloud.cn/d/1-dd-spring-cloud)的七篇教程进行自身项目特点结合实际数据库Oracle进行真实数据的操作）。

``

### 你可通过如下的方式反馈问题，反馈前你可以阅读 FAQ：


### 邮件:
 apicescn@hotmail.com
 
### QQ:

 31464780 (备注：Spring Cloud开发爱好者)

您的每一份帮助都将支持我做的更好，走的更远！

SpringCloudModel正在为你开放更多....

### 待开发事项

1.代码的继续完善；2、Web应用的开发。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)