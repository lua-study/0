# spring-cloud
微服务是系统架构上的一种设计风格，它的主旨是将一个原本独立的系统拆分成多个小型系统，这些小型服务都在各自独立的进程中运行，
服务之间通过基于HTTP的RESTful API进行通信协作。

#Spring Cloud 组件介绍

Spring Cloud Netflix (核心组件)

Eureka:服务化治理组件，包含服务注册中心、服务注册与服务发现机制实现。

Ribbon:客服端负载均衡的服务调用组件。

Hystrix:容错管理组件，实现断路器模式，具备服务降级、服务熔断、线程和信号量隔离、请求缓存、请求合并以及服务监控等强大功能。

Feign：基于Ribbon和Hystrix的声明式服务调用组件。

Zuul：网关组件，提供智能路由，访问过滤等功能(结合Hystrix功能更强大)。

Actuator:端点健康模块。
     
Spring Cloud Config 配置管理工具、支持动态刷新、加解密配置内容等。

Spring Cloud Bus：消息总线。

Spring Cloud Sleuth:分布式服务跟踪，可以完美整合Zipkin(分布式监控)。

Spring Cloud Stream:消费微服务，流式处理。




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)