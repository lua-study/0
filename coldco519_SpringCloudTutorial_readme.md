# SpringCloud 教程
-

## 一、简介

``` 

```


## 二、各微服务占用端口列表
|章		| 微服务模块名称     														| 端口	| 功能描述		|
|:-----:	| :---------------------------------------------------------------------|:-----:|:------------	|
|001	| [springms-simple-provider-user](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-simple-provider-user)| 8000 	|简单用户微服务 	|
|002	| [springms-simple-consumer-movie](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-simple-consumer-movie) | 8005 	|简单电影微服务 	|
|003	| [springms-discovery-eureka](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-discovery-eureka)| 8761 	|服务发现服务端EurekaServer微服务 	|
|004	| [springms-provider-user](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-provider-user)	| 7900 	|用户服务类，已注册 Eureka 	|
|005	| [springms-consumer-movie](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-consumer-movie) | 8005 	|电影微服务，已注册 Eureka 	|
|006	| [springms-consumer-movie-ribbon](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-consumer-movie-ribbon)| 8010 	|电影微服务，使用 Ribbon 在客户端进行负载均衡  	|
|007	| [springms-consumer-movie-ribbon-custom](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-consumer-movie-ribbon-custom) | 8020 	|电影微服务，定制 Ribbon 在客户端进行负载均衡 	|
|008	| [springms-consumer-movie-ribbon-properties](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-consumer-movie-ribbon-properties) | 8030 	|电影微服务，配置 Ribbon 在客户端进行负载均衡 	|
|009	| [springms-simple-quartz](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-simple-quartz)| 8390 	|简单Quartz微服务，不支持分布式 	|
|010	| [springms-simple-quartz-cluster](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-simple-quartz-cluster) | 8395 	|简单Quartz分布式集群, 可动态修改任务执行时间 	|
|011	| [springms-consumer-movie-ribbon-properties-without-eureka](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-consumer-movie-ribbon-properties-without-eureka)     			| 8040 	|电影Ribbon微服务，脱离Eureka使用 	|
|012	| [springms-consumer-movie-feign](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-consumer-movie-feign)| 7910 	|电影 Feign 微服务，支持客户端负载均衡 	|
|013	| [springms-consumer-movie-feign-custom](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-consumer-movie-feign-custom)| 8050 	|电影微服务，定制Feign可负载均衡并认证Eureka 	|
|014	| [springms-consumer-movie-ribbon-with-hystrix](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-consumer-movie-ribbon-with-hystrix)| 8070 	|电影Ribbon微服务，集成 Hytrix 断路器功能 	|
|015	| [springms-consumer-movie-ribbon-with-hystrix-propagation](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-consumer-movie-ribbon-with-hystrix-propagation)| 8100 	|电影Ribbon微服务，集成 Hytrix 测试隔离策略 	|
|016	| [springms-consumer-movie-feign-custom-without-hystrix](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-consumer-movie-feign-custom-without-hystrix)| 8110 	|电影微服务，定制Feign，禁用 Feign 使用 Hystrix	|
|017	| [springms-consumer-movie-feign-with-hystrix-factory](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-consumer-movie-feign-with-hystrix-factory)	| 8115 	|电影Feign微服务，用fallbackFactory触发熔断降级	|
|018	| [springms-gateway-zuul](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-gateway-zuul)| 8150 	|Zuul 服务 API 网关微服务之代理与反向代理	|
|019	| [springms-gateway-zuul-attribute](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-gateway-zuul-attribute)| 8155 	|Zuul 网关微服务的一些属性应用测试	|
|020	| [springms-gateway-zuul-cluster](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-gateway-zuul-cluster)| 8165 	|Zuul添加listOfServers属性实现客户端负载均衡	|
|021	| [springms-gateway-zuul-filter](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-gateway-zuul-filter)	| 8215 	|Zuul 的过滤器 ZuulFilter 的使用	|
|022	| [springms-gateway-zuul-reg-exp](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-gateway-zuul-reg-exp)| 8185 	|Zuul 网关微服务的 regexmapper 属性测试	|
|023	| [springms-file-upload](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-file-upload)	| 8190 	|简单文件上传微服务	|
|024	| [springms-gateway-zuul-file-upload](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-gateway-zuul-file-upload)| 8195 	|简单文件上传微服务加入zuul微服务上传文件	|
|025	| [springms-gateway-zuul-fallback](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-gateway-zuul-fallback)	| 8200 	|Zuul 提供了一种回退机制来应对熔断处理	|
|026	| [springms-node-service](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-node-service)| 8205 	|简单异构系统之 nodejs 微服务	|
|027	| [springms-sidecar](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-sidecar)| 8210 	|集成异构微服务系统到 SpringCloud 生态圈中	|
|028	| [springms-config-server](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-config-server)	| 8220 	|ConfigServer 配置微服务	|
|029	| [springms-config-client](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-config-client)| 8225 	|配置客户端ConfigClient接入配置服务端	|
|030	| [springms-config-server-encrypt](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-config-server-encrypt)| 8255 	|ClientServer对内容进行对称加解密	|
|031	| [springms-config-client-encrypt](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-config-client-encrypt)| 8260 	|ConfigClient链接经过对称加解密的服务	|
|032	| [springms-config-server-encrypt-rsa](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-config-server-encrypt-rsa)| 8265 	|ClientServer对内容进行RSA加解密	|
|033	| [springms-config-client-encrypt-rsa](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-config-client-encrypt-rsa)| 8270 	|ConfigClient链接经过RSA加解密的服务	|
|034	| [springms-config-server-authc](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-config-server-authc)| 8275 	|ClientServer对设置安全认证机制	|
|035	| [springms-config-client-authc](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-config-client-authc)| 8280 	|ConfigClient链接经过安全认证的服务	|
|036	| [springms-config-client-refresh](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-config-client-refresh)| 8295 	|单点手动动态刷新配置服务客户端配置	|
|037	| [springms-config-client-refresh-bus](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-config-client-refresh-bus)| 8300 	|通过bus/refresh半自动刷新ConfigClient配置|
|038	| [springms-simple-provider-user-devtools](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-simple-provider-user-devtools)| 8305 	|idea环境热部署微服务开发|
|039	| [springms-provider-user-mysql-jparepository](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-provider-user-mysql-jparepository)| 8310 	|通过JpaRepository编写数据库访问|
|040	| [springms-provider-user-mysql-crudrepository](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-provider-user-mysql-crudrepository)| 8320 	|通过CrudRepository编写数据库访问|
|041	| [springms-provider-user-mysql-jdbctemplate](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-provider-user-mysql-jdbctemplate)| 8315 	|通过JdbcTemplate编写数据库访问|
|042	| [springms-provider-user-mysql-jdbctemplate-transactional](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-provider-user-mysql-jdbctemplate-transactional)| 8335 	|通过JdbcTemplate编写数据库访问且支持事物|
|043	| [springms-provider-user-mysql-mybatis](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-provider-user-mysql-mybatis)| 8325 	|简单的集成Mybatis框架访问数据库|
|044	| [springms-provider-user-mysql-mybatis-mapper](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-provider-user-mysql-mybatis-mapper)| 8330 	|集成Mybatis框架采用MapperXml访问数据库|
|045	| [springms-provider-user-mysql-mybatis-mapper-ehcache](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-provider-user-mysql-mybatis-mapper-ehcache)| 8385 	|集成Mybatis\ehcache采用MapperXml访问数据库|
|046	| [springms-schedule](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-schedule)| 8340 	|注解式Schedule配置定时任务|
|047	| [springms-async](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-async)| 8345 	|注解式Async配置异步任务|
|048	| [springms-aop-weblog](https://gitee.com/ylimhhmily/SpringCloudTutorial/tree/master/springms-aop-weblog)| 8350 	|使用AOP统一处理Web请求日志|
|049	| [Netflix Eureka 源码深入剖析](https://gitee.com/ylimhhmily/SpringCloudTutorial/blob/master/doc/flow-analysis/Eureka.md)| xxxx 	|Netflix Eureka 源码深入剖析|





## 三、功能模块

-
-


## 四、交流沟通

![微信二维码交流群](https://i.imgur.com/KClb6ap.png)

































 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)