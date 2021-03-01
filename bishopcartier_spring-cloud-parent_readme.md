# spring-cloud-parent

#### 项目介绍
spring cloud 的一个简单的学习  

|项目名|描述|  
|--------|---------|  
|eureka-server|eureka-server的单机服务端，增加security保护服务端,关闭自我保护，具体操作见日志|  
|eureka-client|eureka-client的单机客户端|  
|eureka-server-ha|服务端的高可用配置|  
|ribbon|ribbon的简单使用|  
|feign|feign的简单使用|  
|feign-conf|feign的各种配置的使用|  
|hystrix|和hystrix相关的使用|  
|hystrix-dashboard-turbine|hystrix的dashboard和turbine|  
|zuul|服务网关的使用| 
|config|配置中心的使用| 
|monitor|服务监控| 


~~~
spring-cloud-parent
│ |- 父项目
├─eureka-server [博客](http://huan1993.iteye.com/blog/2423631)
│ |- 项目中用到的eureka server 注册中心
│ │     >> 开启注册中心的权限验证
│ │     >> 关闭eureka 的自我保护（开发环境修改，正式环境不要修改）
│ │     >> 修改清除节点的时间（开发环境修改，正式环境不要修改）
│ │     >> 修改instanceId的值
│ │     >> 显示ip地址，而不是使用主机名
├─eureka-client
│ |- 一个单独的服务提供者模版
│ │     >> 如何连接到有权限的服务段
│ │     >> 减小客户端和服务端的心跳和租约（开发环境修改，正式环境不要修改）
├─eureka-server-ha [博客](http://huan1993.iteye.com/blog/2423635)
│  ├─eureka-server-ha-8764
│  │ |- 8764注册中心   
│  ├─eureka-server-ha-8765
│  │ |- 8765注册中心 
│  ├─eureka-client-8766
│  │    >> 演示如何注册到高可用的注册中心上 
│  │    >> 本地测试需要配置虚拟域名
│  │    >> 本地测试需要注意prefer-ip-address的值，看eureka server界面上显示是否正确，即有没有显示当前节点的复制节点
├─ribbon [博客](http://huan1993.iteye.com/blog/2423850)
│  ├─product-provider-8777
│  ├─product-provider-8778
│  ├─product-provider-8779
│  ├─product-provider-8780
│  ├─order-consumer
│  │    >> 为具体的某个服务单独配置策略，比如修改负载均衡策略等
│  │    >> 需要注意全局和局部配置的区别
│  │    >> 使用配置文件进行配置(略)
├─feign [博客](http://huan1993.iteye.com/blog/2423924)
│  ├─product-provider-8083
│  ├─product-provider-8084
│  ├─product-consumer-8082
│  │    >> 演示 feign 的调用远程服务的各种参数的调用形式
│  │    >> 演示 feign 调用方法参数的各种坑
├─feign-conf [博客](http://huan1993.iteye.com/blog/2424108)
│  ├─product-provider-8085
│  ├─product-provider-8086
│  ├─product-provider-8087
│  ├─product-provider-8088
│  ├─product-consumer-8089
│  │    >> feign 的默认配置类 (FeignClientsConfiguration)
│  │    >> 单独对某个客户端修改配置
│  │    >> 修改默认的契约
│  │    >> 修改feign的日志级别
│  │    >> 根据url直接进行调用，和增加自定义请求头  （如果使用了hystrix,那么在RequestInterceptor中要想使用ThreadLocal的值，隔离策略需要修改成信号量隔离）
│  │    >> 增加压缩
│  │    >> 增加超时时间的配置
│  │    >> 配置重试
│  │    >> yml 文件中对feign的各种配置
│  │
├─hystrix [回退](http://huan1993.iteye.com/blog/2424282)
│  ├─product-provider-8091
│  ├─product-consumer-feign-hystrix-8093
│  │    >> feign 中使用 fallback 实现回退
│  │    >> feign 中使用 fallbackFactory 实现回退，拿到回退的原因
│  │    >> 修改feign的日志级别
│  ├─product-consumer-feign-hystrix-isolation-dashboard-8094
│  │    >> 使用 hystrix 的 dashboard 监控单个微服务的各种参数
│  │    >> 配置全局的隔离策略
│  │    >> 配置某个具体方法的隔离策略
│  │    >> 修改HystrixCommad命令的超时时间
│  │    >> 修改回退的最大并发
│  │    >> 修改局部或全局的Thread隔离时最大的线程并发数
│  │    >> 修改 fallback 最大的并发数
│  │    >> 修改 feign 中默认使用 HttpUrlConnection 进行远程方法请求，修改成 apache httpclient
│  │        ** 需要增加 feign-httpclient 依赖，其余默认可以不用修改，也可以修改一些httpclient的参数
│  │  >> 请求缓存（略)
│  │  >> 请求合并(略) => 当某个请求在极短的时间内大量请求可以使用请求合并来提高效率
├─hystrix-dashboard-turbine [hystrix图表监控](http://huan1993.iteye.com/blog/2424491)
│  ├─hystrix-dashboard
│  │   >> 监控单个工程（指的时同一个服务消费者部署一个，监控这一个的数据）
│  ├─hystrix-single-cluster-turbine
│  │   >> 监控单个集群（指的是同一个服务消费者部署多个，监控这一整个的数据）
│  ├─hystrix-more-cluster-turbine
│  │   >> 监控多个集群（指的是存在多个服务消费者，且多个服务消费者可能都部署了多个，监控这多个的数据）    
│  ├─hystrix-all-cluster-turbine
│  │   >> 监控默认的集群
├─zuul [zuul的各种配置](http://huan1993.iteye.com/blog/2424491)
│  ├─product-provider-8202
│  ├─product-provider-8203
│  │   >> 服务提供者
│  ├─product-consumer-8201
│  │   >> 服务消费者
│  ├─product-gateway-8204
│  │   >> 网关程序
│  │   >> 查看 zuul 中配置好的路由和过滤器信息
│  │   >> 忽略所有微服务或某些微服务
│  │   >> 忽略所有为服务，只路由指定的微服务
│  │   >> 通过path和url访问到具体的某台机器上
│  │   >> 脱离eureka进行访问，并使之具有负载均衡和隔离的机制等
│  │   >> 转发前是否去掉路由前缀
│  │   >> 为所有路由都增加一个通过的前缀
│  │   >> 忽略某些路径不进行路由
│  │   >> 敏感头的传递（比如Cookie等）全局设置和某个微服务设置
│  │   >> 忽略头
│  │   >> spring security 在classpath 下会忽略的头
│  │   >> 本地调换和路由的优先级
│  │   >> 网关(zuul)的超时配置，看网关中yml中的配置
│  │   >> 重写 Location 头
│  │   >> 文件上传处理
│  │   >> zuul 中使用ribbon进行负载均衡调用，ribbon是在第一次调用时由Spring Cloud延时加载，现在修改成程序启动时就立即加载
│  ├─product-gateway-filters-8205
│  │   >> 使用 pre 过滤器进行权限的校验
│  │   >> 使用 post 过滤器添加额外的响应头
│  │   >> 禁用过滤器
│  ├─product-gateway-fallbackprovider-8206
│  │   >> zuul 服务网关的回退，即zuul访问某个微服务访问不到时的 fallback 处理
│  │   >> 单个服务回退 getRoute() 直接返回那个服务的serviceId的值，为所有的回退，直接返回 null 或 *
│  ├─product-gateway-aggregation-swagger2-8207
│  │   >> 聚合各个工程的 swagger api 接口文档
├─config [spring cloud config 的使用](http://huan1993.iteye.com/blog/2425032)
│  ├─config-server-8301
│  │   >> config server 端的编写并注册到eureka上
│  │   >> config server 端增加 basic 认证
│  │   >> config server 配置路径查找规则
│  │   >> config server 的加密和解密端点
│  │   >> 配置进行加密处理
│  │   >> 其它的一些配置见具体的配置文件上
│  ├─product-provider-config-client-8302
│  │   >> config client 端
│  ├─config-bus-webhook [spring cloud config 结合 spring cloud bus实现配置自定的刷新](http://huan1993.iteye.com/blog/2425170)
│  ├────config-server-bus-8305
│  │       >> config server 服务端，整合spring cloud bus 实现配置自动刷新
│  ├────product-provider-config-client-bus-webhook-8303
│  ├────product-provider-config-client-bus-webhook-8304
│  │       >> config client 客户端，git 的webhook请求config server的 /bus/refresh完成各个客户端配置的自动刷新
├─monitor 
│  ├─admin [spring boot admin 的使用](http://huan1993.iteye.com/blog/2425265)
│  │   >> 使用spring boot admin 进行监控
│  │────spring-boot-admin-server-8401
│  │      >> 在 spring boot 1.5.x 后，要监控端点，需要management.security.enabled=false
│  │      >> 引入 spring security 后，就可以使用 spring security 保护admin server
│  │      >> 引入 spring security 保护admin server
│  │      >> 作为一个服务发现者注册到 eureka 上
│  │      >> 给 admin server 提供一个表单登录
│  │      >> 服务的下上线进行邮件的通知
│  │────client-product-provider-8402
│  │      >> 动态控制日志级别
│  │      >> 当设置了management.context-path，如何进行配置
│  │      >> 显示版本号
│  │      >> 客户端使用了 spring security 做了权限保护，admin server如何访问
│  │      >> 整合 hystrix ui 
│  ├─zipkin 
│  │   >> 使用 zipkin 进行分布式服务追踪，分析服务调用耗时、服务之间的依赖
│  │────product-consumer-feign-hystrix-zipkin-8502
│  │────product-provider-zipkin-8501
│  │────zipkin-server-8503
│  │      >> 以上三个应用程序为一组，实现 zipkin 数据存储在 mysql 中
│  │      >> 如何进行配置参考 spring-cloud-parent -- monitor -- readme.txt 文件
~~~
    
    


##### 1、eureka的自我保护，生产环境中不建议关闭，测试环境中可以关闭。  
##### 2、当使用了feign的 RequestInterceptor 向下游服务传递消息头，比如Cookie等时，如果启用了 Hystrix ,如果想在 RequestInterceptor 中使用到 ThreadLocal 中的值，必须要将隔离策略修改成信号量隔离。  
##### 3、spring config client 的和注册中心的配置以及client config的配置必须要写在 bootstrap.yml 配置文件中


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)