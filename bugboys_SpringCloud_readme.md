# SpringCloud分布式组件集成及脚手架项目
随着SpringBoot越来越流行甚至普及，以SpringBoot为基础的Spring Cloud未来也将流行起来，它提供了分布式系统完整的解决方案，以下是官网对它的描述:

微服务架构集大成者，云计算最佳业务实践 —— **SpringCloud**

本项目主要搭建了**SpringCloud**中常用组件，以供开发中学习和使用，以下是项目中涉及到组件说明:

* **Eureka**，服务注册中心，特性有失效剔除、服务保护

* **Zuul**，API服务网关，功能有路由分发和过滤

* **Config**，分布式配置中心，支持本地仓库、SVN、Git、Jar包内配置等模式

* **Ribbon**，客户端负载均衡，特性有区域亲和、重试机制

* **Hystrix**，客户端容错保护，特性有服务降级、服务熔断、请求缓存、请求合并、依赖隔离

* **Feign**，声明式服务调用，本质上就是Ribbon+Hystrix

* **Stream**，消息驱动，有Sink、Source、Processor三种通道，特性有订阅发布、消费组、消息分区

* **Bus**，消息总线，配合Config仓库修改的一种Stream实现

* **Sleuth**，分布式服务追踪，需要搞清楚TraceID和SpanID以及抽样，如何与ELK整合

* **Turbine**，集群收集器，服务于Dashboard

* **Dashboard**，Hystrix仪表盘，监控集群模式和单点模式，其中集群模式需要收集器Turbine配合，侧重故障诊断

* **Zipkin**，服务追踪组件，侧重性能优化


## 技术讨论 & [博客地址](https://www.jacknolfskin.top/)
如果对项目有任何疑问或者建议,欢迎到我的博客留言及交流!

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)