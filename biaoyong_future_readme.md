# future-service

#### 前言
#### 项目介绍
springboot gradle项目：dubbo rpc；druid数据源连接池；mybatis配置集成，多数据源；jmx监控MBean；定时任务配置；aop配置；测试；Metrics监控；参数验证；跨域处理；shiro权限控制；zookeeper/nacos服务注册,发现；redis分布式锁；SPI服务机制；cat监控；netty服务代理；
websocket；disconf；RocketMq集成；日志集成[logback.xml](future-utils/src/main/resources/logback.xml)
自动按天切割,同时长连接上报到elk,存储到搜索引擎elasticsearch,基于该架构提供自动化生成代码,包括前后端分开代码;


##### 开源的目的
     1.该架构是通过某公司大用量的验证;基于该架构提供自动化生成代码,包括前后端分开代码;
     2.解决初创公司技术架构薄弱,搭建的架构难用,开发效率低,研发成本高,其实很多很好的产品,因为研发成本问题而没有到来,为大家生活提供更的方便;
     3.自动化生成代码,可用性高,性能高,可以满足业务的60%,从而减少公司的研发成本,也很好的规范了每个人的编写代码风格,有利代码维护和管理;
     4.通过多年的技术积累,也想帮助下那些热充技术想提高自己能力的小伙伴们,提供一份参考与学习的样板,
     5.帮助了别人多少,别人的成就也会成就了我,谢谢您们~~~

###### [文档从到top-suven/doc 目录下](doc)
###### [数据库脚本top-suven/db 目录下](db)

###### 项目展示效果图:

* 1.[kafka 展示效果图](doc/imgage/kafka.png)
* 2.[elk 展示效果图](doc/imgage/elk.png)
* 3.[cat 展示效果图](doc/imgage/cat.png)
* 4.[rocketMq 展示效果图](doc/imgage/rocketMq.png)
* 5.[admin后台管理系统 展示效果图](doc/imgage/admin.png)


#### 软件架构
软件架构说明
 * [服务接口说明文档,运行项目:http://IP:port/top/docs.html](doc/http/http-index.md)
 * [代码构架目录说明文档](doc/Code_structure.md)
 * [服务部署说明文档](doc/project.md)
 * [中间键ELK说明文档](doc/elk_installation.md)
 * [中间键fastDFS安装说明文档](doc/fastDFS_installation.md)
 * [中间键Redis安装说明文档](doc/redis_installation.md)
 * [监控端点说明文档](doc/metric.md)
 * [哨兵服务限流降级说明文档](doc/Sentinel.md)
 * [服务注册与发现说明文档](doc/nacos.md)
 * [服务应用部署启动说明文档](doc/project.md)
 * [参数配置明文档](doc/project-config-info.md)
 
  
  


 
技术架构：
-----------------------------------
#### 开发环境

- 语言：Java 8

- IDE(JAVA)： IDEA / Eclipse

- IDE(前端)： WebStorm,Visual Studio Code 或者 IDEA 

- 依赖管理：Gradle

- 数据库：MySQL8.x+  &  Oracle 11g & Sqlserver2017

- 缓存：Redis


### 技术选型

#### 后端技术: 基于独创的基础架构,实现自动化成业务模块;实现前后台端分享,
技术 | 名称 | 官网
----|------|----
Dubbo | 分布式服务框架  | [http://dubbo.apache.org/en-us/index.html](http://dubbo.apache.org/en-us/index.html)
Jetty| 服务运行容器  | [https://www.eclipse.org/jetty/](https://www.eclipse.org/jetty/), [ API Docs 说明文档](https://www.eclipse.org/jetty/javadoc/current/)
Spring Framework | 容器  | [http://projects.spring.io/spring-framework/](http://projects.spring.io/spring-framework/)
SpringMVC | MVC框架  | [http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#mvc](http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#mvc)
Nacos  | 分布式协调服务  | [https://nacos.io/en-us/](https://nacos.io/en-us/)
Sentinel   | 服务限流降级  | [https://github.com/alibaba/Sentinel/wiki/%E4%BB%8B%E7%BB%8D](https://github.com/alibaba/Sentinel/wiki/%E4%BB%8B%E7%BB%8D)
ZooKeeper | 分布式协调服务  | [http://zookeeper.apache.org/](http://zookeeper.apache.org/)
Redis | 分布式缓存数据库  | [https://redis.io/](https://redis.io/)
RocketMQ | 消息队列  | [https://rocketmq.apache.org/](https://rocketmq.apache.org/)
Cat(大众点评监控) | 微服务连路监控  | [https://github.com/dianping/cat](https://github.com/dianping/cat)
Kafka | 消息队列  | [http://kafka.apache.org/](http://kafka.apache.org/)
JStorm | 实时流式计算框架  | [http://jstorm.io/](http://jstorm.io/)
FastDFS | 分布式文件系统  | [https://github.com/happyfish100/fastdfs](https://github.com/happyfish100/fastdfs)
Solr & Elasticsearch | 分布式全文搜索引擎  | [http://lucene.apache.org/solr/](http://lucene.apache.org/solr/) [https://www.elastic.co/cn/products/elasticsearch](https://www.elastic.co/cn/products/elasticsearch)
Logstash | 服务器端数据采摘 | [https://www.elastic.co/cn/products/logstash](https://www.elastic.co/cn/products/logstash)
Kibana | Elastic Stack的窗口 | [https://www.elastic.co/cn/products/kibana](https://www.elastic.co/cn/products/kibana)
MyBatis | ORM框架  | [http://www.mybatis.org/mybatis-3/zh/index.html](http://www.mybatis.org/mybatis-3/zh/index.html)
MyBatis-plus | ORM框架  | [https://mybatis.plus/](https://mybatis.plus/)
PageHelper | MyBatis物理分页插件  | [https://github.com/pagehelper/Mybatis-PageHelper](https://github.com/pagehelper/Mybatis-PageHelper)
Druid | 数据库连接池  | [https://github.com/alibaba/druid](https://github.com/alibaba/druid)
Logback & slf4j-log4j12| 日志组件  | [http://logback.qos.ch/](http://logback.qos.ch/) [http://www.slf4j.org/](http://www.slf4j.org/)
Protobuf & json | 数据序列化  | [https://github.com/google/protobuf](https://github.com/google/protobuf)
Swagger2 | 接口测试框架  | [http://swagger.io/](http://swagger.io/)
Apache Shiro | 安全框架  | [http://shiro.apache.org/](http://shiro.apache.org/)
Thymeleaf | 模板引擎  | [http://www.thymeleaf.org/](http://www.thymeleaf.org/)
Velocity | 模板引擎  | [http://velocity.apache.org/](http://velocity.apache.org/)
sequence | 分布式高效ID生产  | [http://git.oschina.net/yu120/sequence](http://git.oschina.net/yu120/sequence)
AliOSS & Qiniu & QcloudCOS | 云存储  | [https://www.aliyun.com/product/oss/](https://www.aliyun.com/product/oss/) [http://www.qiniu.com/](http://www.qiniu.com/) [https://www.qcloud.com/product/cos](https://www.qcloud.com/product/cos)
Jenkins | 持续集成工具  | [https://jenkins.io/index.html](https://jenkins.io/index.html)
Gradle | 项目构建管理  | [https://gradle.org/](https://gradle.org/)
Seata | 高性能微服务分布式事务  | [https://github.com/seata/seata](https://github.com/seata/seata)
Alibaba Cloud OSS | 阿里云对象存储服务  | [https://www.aliyun.com/product/oss](https://www.aliyun.com/product/oss)
Alibaba Cloud SMS | 阿里云短信服务  | [https://www.aliyun.com/product/sms](https://www.aliyun.com/product/sms)



## 主要功能
    
* **服务限流降级**：默认支持 WebServlet、WebFlux, OpenFeign、RestTemplate、Spring Cloud Gateway, Zuul, Dubbo 和 RocketMQ 限流降级功能的接入，可以在运行时通过控制台实时修改限流降级规则，还支持查看限流降级 Metrics 监控。
* **服务注册与发现**：适配 Spring Cloud 服务注册与发现标准，默认集成了 Ribbon 的支持。
* **分布式配置管理**：支持分布式系统中的外部化配置，配置更改时自动刷新。
* **消息驱动能力**：基于 Spring Cloud Stream 为微服务应用构建消息驱动能力。
* **分布式事务**：使用 @GlobalTransactional 注解， 高效并且对业务零侵入地解决分布式事务问题。。
* **阿里云对象存储**：阿里云提供的海量、安全、低成本、高可靠的云存储服务。支持在任何应用、任何时间、任何地点存储和访问任意类型的数据。
* **分布式任务调度**：提供秒级、精准、高可靠、高可用的定时（基于 Cron 表达式）任务调度服务。同时提供分布式的任务执行模型，如网格任务。网格任务支持海量子任务均匀分配到所有 Worker（schedulerx-client）上执行。
* **阿里云短信服务**：覆盖全球的短信服务，友好、高效、智能的互联化通讯能力，帮助企业迅速搭建客户触达通道。


更多功能请参考 [Roadmap](https://github.com/alibaba/spring-cloud-alibaba/blob/master/Roadmap-zh.md)。


#### 前端

#### 安装教程

序号 | 操作名称 | 执行脚本
----|------|----
1.| 克隆项目: |git clone https://gitee.com/suvenw/future.git
2.|进入项目目录: |   cd future
3.| 清除项目缓存:  |  gradle clean
4.| 编译项目: |   gradle idea
5.|打包项目jar: |   gradle copyLib
6.|打包项目配置文件: | gradle copyEtc
7.|打包项目源码包: | gradle sourcesJar





### 使用说明 
  1. maven dependency

```
 
     0.0.1 
 
    
 
     
         top.suven.future 
         future-generator 
         ${future.version} 
     
     
         top.suven.future 
         future-http 
         ${future.version} 
     
     
         top.suven.future 
         future-utils 
         ${future.version} 
     
     
         top.suven.future 
         future-cat 
         ${future.version} 
     
     
         top.suven.future 
         future-global 
         ${future.version} 
         
 

```
  2. gradle  dependency
  
 ```
 
 compile 'top.suven.future:future-generator:0.0.1'
 compile 'top.suven.future:future-http:0.0.1'
 compile 'top.suven.future:future-utils:0.0.1'
 compile 'top.suven.future:future-cat:0.0.1'
 compile 'top.suven.future:future-global:0.0.1'
 
```

#### git开发分支管理与流程
序号 | 分支名称          | 分支作用      | 分支来源 | 备注 
----|------            |----          |----      |----
1.  | develop          | 开发          | master   | 受保护
2.  | release          | 聚成与灰度     | master   | 受保护
3.  | master           | 线上发版       | release  | 受保护
4.  | feature_develop  | 业务开发分支    | develop  | 
5.  | hotfix_release   | 灰度取成bug分支 |  release | 
6.  | hotfix_master    | 线上bug分支     | master   | 

#### 码云特技

1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)