# SpringCloud 教程
-

## 一、简介

``` 

```


## 二、各微服务占用端口列表
|章		| 微服务模块名称     														| 端口	| 功能描述		|
|:-----:	| :---------------------------------------------------------------------|:-----:|:------------	|
|001	| springms-simple-provider-user      									| 8000 	|简单用户微服务 	|
|002	| springms-simple-consumer-movie      									| 8005 	|简单电影微服务 	|
|003	| springms-discovery-eureka      										| 8761 	|服务发现服务端EurekaServer微服务 	|
|004	| springms-provider-user													| 7900 	|用户服务类，已注册 Eureka 	|
|005	| springms-consumer-movie      											| 8005 	|电影微服务，已注册 Eureka 	|
|006	| springms-consumer-movie-ribbon      									| 8010 	|电影微服务，使用 Ribbon 在客户端进行负载均衡  	|
|007	| springms-consumer-movie-ribbon-custom      							| 8020 	|电影微服务，定制 Ribbon 在客户端进行负载均衡 	|
|008	| springms-consumer-movie-ribbon-properties     							| 8030 	|电影微服务，配置 Ribbon 在客户端进行负载均衡 	|
|009	| springms-simple-quartz     									 		| 8390 	|简单Quartz微服务，不支持分布式 	|
|010	| springms-simple-quartz-cluster     									| 8395 	|简单Quartz分布式集群, 可动态修改任务执行时间 	|
|011	| springms-consumer-movie-ribbon-properties-without-eureka     			| 8040 	|电影Ribbon微服务，脱离Eureka使用 	|
|012	| springms-consumer-movie-feign     			                        	| 7910 	|电影 Feign 微服务，支持客户端负载均衡 	|
|013	| springms-consumer-movie-feign-custom     			                	| 8050 	|电影微服务，定制Feign可负载均衡并认证Eureka 	|
|014	| springms-consumer-movie-ribbon-with-hystrix		                	| 8070 	|电影Ribbon微服务，集成 Hytrix 断路器功能 	|
|015	| springms-consumer-movie-ribbon-with-hystrix-propagation				| 8100 	|电影Ribbon微服务，集成 Hytrix 测试隔离策略 	|
|016	| springms-consumer-movie-feign-custom-without-hystrix					| 8110 	|电影微服务，定制Feign，禁用 Feign 使用 Hystrix	|
|017	| springms-consumer-movie-feign-with-hystrix-factory						| 8115 	|电影Feign微服务，用fallbackFactory触发熔断降级	|
|018	| springms-gateway-zuul													| 8150 	|Zuul 服务 API 网关微服务之代理与反向代理	|
|019	| springms-gateway-zuul-attribute										| 8155 	|Zuul 网关微服务的一些属性应用测试	|
|020	| springms-gateway-zuul-cluster											| 8165 	|Zuul添加listOfServers属性实现客户端负载均衡	|
|021	| springms-gateway-zuul-filter											| 8215 	|Zuul 的过滤器 ZuulFilter 的使用	|
|022	| springms-gateway-zuul-reg-exp											| 8185 	|Zuul 网关微服务的 regexmapper 属性测试	|
|023	| springms-file-upload													| 8190 	|简单文件上传微服务	|
|024	| springms-gateway-zuul-file-upload										| 8195 	|简单文件上传微服务加入zuul微服务上传文件	|
|025	| springms-gateway-zuul-fallback											| 8200 	|Zuul 提供了一种回退机制来应对熔断处理	|
|026	| springms-node-service													| 8205 	|简单异构系统之 nodejs 微服务	|
|027	| springms-sidecar														| 8210 	|集成异构微服务系统到 SpringCloud 生态圈中	|
|028	| springms-config-server													| 8220 	|ConfigServer 配置微服务	|





## 三、功能模块








































 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)