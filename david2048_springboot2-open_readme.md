

# 个人准备开源的快速开发框架(实现小程序商城)[带宽有限,加载可能比较慢]

项目演示 (admin/admin):    

登录用户和密码:`admin/admin`

基于springboot2+mybatis plus+shiro+redis+jwt+vue2+bootstrap3+mysql实现

功能包括:

- 前后端分离
- 安全认证 权限管理
- 代码生成器
- selenium实现自动化测试

...........项目开发中,有兴趣参与的联系本人

# Spring Boot2基础教程

## 介绍

> 基于springboot2开发教程
>
> 目标：收集网上的springboot博文，码出一系列最详尽的开源项目，帮助广大码农。
>
> 计划三个月内完成所有源码的开源和博客编写，你的star是作者的最大支持
>
> 有志同道合可以加群：`966969685 `

## 框架

> 
>
> **springboot2.1+jdk1.8+各种第三方框架**
>
> 



##  Spring Boot 基础教程

### 入门配置

| 项目                         | 说明                                                         | 备注                                                         |
| ---------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| open-base-log（已完成）      | [Springboot2日志配置和动态日志等级设置](https://blog.csdn.net/cowbin2012/article/details/85235931) | 支持两种方法动态修改日志等级                                 |
| open-base-config（已完成）   | [Springboot2属性配置讲解和自定义属性配置](https://blog.csdn.net/cowbin2012/article/details/85237502) | 多环境的配置方法 @value支持的7种内容注入，还List，Map类型的注入,设置默认值的方法 @ConfigurationProperties，@Profile的使用 |
| open-base-static（已完成）   | [Springboot2静态资源处理](https://blog.csdn.net/cowbin2012/article/details/85237760) | 讲解了静态的配置                                             |
| open-base-controller(已完成) | [Springboot2Controller控制层讲解](https://blog.csdn.net/cowbin2012/article/details/85237857) | 讲解@Controller&@RestController&@RequestMapping @PathVaribale & @RequestParam & @RequestBody |
| open-base-swagger(已完成)    | [Springboot2集成swagger2](https://blog.csdn.net/cowbin2012/article/details/86711362) | 集成swagger2构建RESTful API文档                              |
| open-base-enable(已完成)     | [自定义@Enable模块装配]( https://blog.csdn.net/cowbin2012/article/details/89338738 ) | 介绍自定义@Enable模块装配的两种方式                          |
| open-base-https              | [https方式部署](   通过ResourceHandlers实现静态资源的地址映射  通过MessageConverter实现fastJson消息转换器 通过addCorsMappings实现ajax跨域请求 通过addInterceptors添加拦截器 |
| open-web-intercptor（已完成）       | [轻松搞定Interceptor（拦截器）](https://blog.csdn.net/cowbin2012/article/details/85194393) | 样例：实现拦截器拦截所有请求，并打印相应信息                 |
| open-web-filter（已完成）           | [轻松搞定自定义Filter（过滤器）](https://blog.csdn.net/cowbin2012/article/details/85194431) | 两种不种的实现方式                                           |
| open-web-listener（已完成）         | [轻松搞定Listener(监听器)](https://blog.csdn.net/cowbin2012/article/details/85194460) | 监听器的实现                                                 |
| open-web-cors（已完成）             | [轻松搞定跨域访问（CORS）](https://blog.csdn.net/cowbin2012/article/details/85194492) | 4种实现方式： 方式1：返回新的CorsFilter 方式2：重写WebMvcConfigurer 方式3：使用注解（@CrossOrigin） 方式4：手工设置响应头（HttpServletResponse） |
| open-web-exception（已完成）        | [轻松搞定统一异常处理](https://blog.csdn.net/cowbin2012/article/details/85194555) | 实现全局的异常处理                                           |
| open-web-upload（已完成）           | [轻松搞定文件上传](https://blog.csdn.net/cowbin2012/article/details/85247053) | 实现文件上传的配置                                           |
| open-web-vaild（已完成）            | [轻松搞定数据验证](https://blog.csdn.net/cowbin2012/article/details/85247333) | 讲解了 hibernate的校验实现 自定义验证器实现            |
| open-web-event（已完成）            | [轻松搞定自定义事件监听](https://blog.csdn.net/cowbin2012/article/details/85247875) | 实现事件监听的功能                                           |
| open-web-async（已完成）            | [异步调用Async](https://blog.csdn.net/cowbin2012/article/details/85248381) | 自定义的Executor 异步调用实现                             |
| open-web-resttemplate（已完成）     | [轻松搞定RestTemplate](https://blog.csdn.net/cowbin2012/article/details/85250855) | 包括RestTemplate的post,get请求，HTTP请求头的设置，发送文件，下载文件 |

###  常用功能

| 项目                     | 说明                                                         | 备注 |
| ------------------------ | ------------------------------------------------------------ | ------------------------ |
| open-common-actuator（已完成） | [运行状态监控使用 Actuator](https://blog.csdn.net/cowbin2012/article/details/85251524) | 编写自定义HealthIndicators |
| open-common-aop（已完成）   | [轻松搞定AOP](https://blog.csdn.net/cowbin2012/article/details/85251655) | 实现AOP的样例 |
| open-common-cache(已完成) | [轻松搞定数据缓存](https://blog.csdn.net/cowbin2012/article/details/85220033) | 实现的缓存的样例 |
| open-common-schedule（已完成） | [Spring定时任务](https://blog.csdn.net/cowbin2012/article/details/85219887) | 样例 1.说明schedule串行和并行的设置 2.动态设置schedule的cros,并支持新建、更新、删除定时任务 |
| open-common-websocket（已完成） | [轻松搞定WebSocket](https://blog.csdn.net/cowbin2012/article/details/85220055) | 样例 1.实现了简单网页聊天功能 2.实现了WEB远程连接Linux的功能（类Xshell） |
| open-common-mail（已完成）    | [轻松整合mail](https://blog.csdn.net/cowbin2012/article/details/85252433) | 实现带附件的邮件，模板邮件，html邮件的发送 |

###  数据访问

| 项目                  | 说明                 | 备注 |
| --------------------- | -------------------- | --------------------- |
| open-db-mybatis（已完成） | [Springboot2（22）Mybatis拦截器实现](https://blog.csdn.net/cowbin2012/article/details/85256360) | 实现mybatis跟mysql的集成 实现mybatis插件的四种拦截方法 |
| open-db-mycat（已完成）   |                      |  |
| open-db-readwrite（已完成） |                      |  |
| open-db-sharding-jdbc（已完成） |                      |  |
| open-db-canal(已完成) | [集成canal]( https://blog.csdn.net/cowbin2012/article/details/89362508 ) | 实现 注入接口实现的方式监听对应的事件 |
| open-db-tx(已完成) | [注解事务声明式事务]( https://blog.csdn.net/cowbin2012/article/details/90751044 ) | 实现 xml声明式事务和注解事务  讲解事务的传播 |
| open-db-flyway(已完成) | [集成flyway进行数据库版本管理]( https://blog.csdn.net/cowbin2012/article/details/90764495 ) | 使用Flyway来管理数据库版本 |
| open-db-jpa(已完成) | [集成jpa]( https://blog.csdn.net/cowbin2012/article/details/93739717 ) | jpa的一些使用方法 |

###  安全管理

| 项目                          | 说明                 | 备注 |
| ----------------------------- | -------------------- | ----------------------------- |
| open-security-shiro（已完成）     | [Springboot2（23）轻松整合shiro(带验证码)](https://blog.csdn.net/cowbin2012/article/details/85266174) | 实现shiro登录认证和权限认证。 后续加上“记住我”的功能，分布式session的功能 |
| open-security-shiro-jwt      |                      |  |
| open-security-springsecurity | [集成Security5]( https://blog.csdn.net/cowbin2012/article/details/93983159 ) | 实现基本的登录认证和权限认证 |
| open-security-oauth2          |                      |  |

### 缓存框架

| 项目                | 说明                 | 备注 |
| ------------------- | -------------------- | ------------------- |
| open-cache-redis-jedis（已完成） | [Springboot2（32）集成redis(jedis)](https://blog.csdn.net/cowbin2012/article/details/86376105) | 集成redis(jedis) |
| open-cache-mongodb（已完成） | [Springboot2（33）集成mongodb](https://blog.csdn.net/cowbin2012/article/details/86494997) | 集成mongodb |
| open-cache-redis-redisson（已完成） | [Springboot2（46）集成redis(reddisson)]( https://blog.csdn.net/cowbin2012/article/details/89707301 ) | 集成redis(redission) |

### 微服务

| 项目                  | 说明                 | 备注 |
| --------------------- | -------------------- | --------------------- |
| open-ms-zookeeper(已完成) | [Springboot2（29）集成zookeeper](https://blog.csdn.net/cowbin2012/article/details/85337250)   [Zookeeper基本命令](https://blog.csdn.net/cowbin2012/article/details/85337413) | 实现zookeeper节点的增删改查、节点监听、 分布式读写锁、分布式计数器 |
| open-ms-dubbo(已完成)   | [集成dubbo整合--三种实现方法和一些常用配置讲解](https://blog.csdn.net/cowbin2012/article/details/85777055) | 项目分为：open-ms-dubbo-consumer和open-ms-dubbo-provider  |
| open-ms-cloud-eureka  | [[springcloud]集成Eureka](https://blog.csdn.net/cowbin2012/article/details/86713138) | Eureke集群配置和服务注册 |
| open-ms-cloud-gateway |                      |  |
| open-ms-cloud-hystrix |                      |  |
| open-ms-cloud-zipkin  |                      |  |
| open-ms-cloud-zuul   |                      |  |
| open-ms-dubbo-txlcn(代码已经上传) | 博客有时间再整理 | 实现分布式事务 |
| open-ms-springcloud-sentinel | [集成阿里sentinel]( https://blog.csdn.net/cowbin2012/article/details/90769370 ) | 实现限流降级功能 |

### 分布式中间件

| 项目                  | 说明                 | 备注 |
| --------------------- | -------------------- | --------------------- |
| open-mc-rabbitmq（暂完成，有后续） | [rabbitmq实现延时消息](https://blog.csdn.net/cowbin2012/article/details/85330585) | 项目：open-mc-rabbitmq-consumer和open-mc-rabbitmq-privider 实现的消息的发布和订阅，还实现延时消息的发送。 实现发送确认和消息确认和持久化 后续：RPC和rabbitmq集群 |
| open-mc-kafka(已完成)   | [集成kafka](https://blog.csdn.net/cowbin2012/article/details/85407495) | 项目：open-mc-kafka-consumer和open-mc-kafka-privider 实现Topic的增删改查，监听Topic中指定的分区，注解方式获取消息头及消息体， 使用Ack机制确认，消费实现消息转发等功能 |
| open-mc-activemq      | [集成activemq](https://blog.csdn.net/cowbin2012/article/details/89318005 ) | 实现消息生产和消息 |
| open-mc-elasticsearch(已完成) | [集成elasticSearch6.x](https://blog.csdn.net/cowbin2012/article/details/86673812) | 实现elasticsearch基本操作 |
| open-mc-solrcloud(已完成) | [集成solr，solrCloud]( https://blog.csdn.net/cowbin2012/article/details/89495190 ) | 实现solrCloud增删改查等基本操作 |
| open-mc-netty(已经完成) | [netty实现http服务](https://blog.csdn.net/cowbin2012/article/details/85289248) [netty实现文件传输](https://blog.csdn.net/cowbin2012/article/details/85290876)  [netty实现websocket通讯](https://blog.csdn.net/cowbin2012/article/details/85297547)   [实现反向代理（内网穿透）](https://blog.csdn.net/cowbin2012/article/details/85298975) | 1.集成netty实现http服务（类似SpingMvc的contoller层实现） 2.完成文件下载功能 3.完成websocket功能 4.完成反向代理功能  |
| open-mc-fastdfs       |                      |  |
| open-mc-activiti      |                      |  |
| open-mc-rocketmq(已完成) | [Springboot2（34）集成rocketmq4.4](https://blog.csdn.net/cowbin2012/article/details/86671927) | 1.讲解三种消息类型的发送 2.消息的过滤 |

### 大数据

| 项目                 | 说明                 |  |
| -------------------- | -------------------- | -------------------- |
| open-bigdata-hadoop(已完成) | [集成hadoop](https://blog.csdn.net/cowbin2012/article/details/86680202) | hadoop的基本操作,上传下载删除文件 |
| open-bigdata-hbase(已完成) | [集成hbase](https://blog.csdn.net/cowbin2012/article/details/86710812) | hbase基本操作 |
| open-bigdata-hive(已完成) | [集成hive](https://blog.csdn.net/cowbin2012/article/details/86685543) | hive的基本操作 |
| open-bigdata-spark(代码已经上传) | 博客有时间再整理 | 实现从hbase获取数据计算 集成kafka流式计算单词数 从hdfs上获取数据计算后保存到mysql |
| open-flume | [自定义的Sources,Sinks,Interceptor]( https://blog.csdn.net/cowbin2012/article/category/8922810 ) | 实现自定义的Sources,Sinks,Interceptor |

## 项目现况

> 本人已经完成大部分项目的编码，由于当时编码只是为了编码而编码，缺乏文档支持，代码比较难懂，所以打算重新整理，编写博客说明每一个模块。

![](https://note.youdao.com/yws/api/personal/file/206D566AB5474BCA915931C13B06A740?method=download&shareKey=c7b7543ac5cbc4c62facf02f27dadfcc)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)