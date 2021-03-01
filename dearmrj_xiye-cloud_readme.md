### 项目简介
 XIYE-CLOUD  
 
    
    
    
    
 

- Eureka 云端服务发现，一个基于 REST 的服务，用于定位服务，以实现云端中间层服务发现和故障转移
- Config 配置管理工具包，让你可以把配置放到远程服务器，集中化管理集群配置，目前支持本地存储、Git以及Subversion
- Zuul 是在云平台上提供动态路由,监控,弹性,安全等边缘服务的框架。Zuul 相当于是设备和 Netflix 流应用的 Web 网站后端所有请求的前门
- Hystrix 熔断器，容错管理工具，旨在通过熔断机制控制服务和第三方库的节点,从而对延迟和故障提供更强大的容错能力
- Feign 子项目之间的请求调用
- shiro管理session并缓存到redis缓存服务器,进行集群共享session
- Mybatis 个人习惯直接写sql，所以没有整合一些自动生成SQL语句的功能
- 数据库采用的Oracle 11g，当然了，你也可以自行改为Mysql数据库。至于为什么不采用Mysql，青菜萝卜各有所爱！
- 日志目前默认是定义在拦截请求开始和请求结束后进行日志打印，后台服务会保存到redis缓存服务器当中。
- elk日志分析系统服务我的做法是运行后直接从redis缓存服务器中日志对应的key进行value拉取并保存在elasticsearch，
  成功后从redis缓存中删掉相应的日志记录
- 前端采用vue的iView Admin模板
- 登录账号admin，密码随便填，为了测试方便先在后台写死了
- 配置中心可以远程和本地2选1，看你心情。远程配置中心自己Fork到自己的项目中进行修改

### 前端[xiye-cloud-vue](https://gitee.com/xiyecode/xiye-cloud-vue)、远程配置中心[xiye-config](https://gitee.com/xiyecode/xiye-config)

### 后端项目样图
 
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
 

### 前端所用技术
- Vue 2.5.x、iView1.3.1、iview-admin、iview-area、Vuex、Vue Router、webpack、axios、echarts、cookie等
- 前台为基于Vue+iView的独立项目请跳转至 [xiye-cloud-vue](https://gitee.com/xiyecode/xiye-cloud-vue) 项目仓库查看
### 后端所用技术
##### 各框架依赖版本都尽可能的采用了目前最新的版本
- [x] Spring Boot 2.0.4.RELEASE
- [x] [Swagger-Bootstrap-UI 1.8.1](https://gitee.com/xiaoym/swagger-bootstrap-ui)：Api文档生成，整合作者萧明的Swagger-Bootstrap-UI开源的前端样式，版本1.8.1（最低1.8.0，之前的版本跟作者确认过，在网关访问子项目接口测试时不会自动带上子项目名）
- [x] [Maven 3.5.4](http://maven.apache.org/download.cgi)：版本3.5.4
- [x] [Pinpoint 1.5.1](https://github.com/naver/pinpoint)：链路跟踪,1.7.3和1.8的有点问题，暂时先挑个相对稳定的版本，后续有空再升级高版本
- [x] [Zipkin 2.11.1](https://github.com/openzipkin/zipkin)：分布式链路跟踪。版本zipkin-server-2.11.1-exec
- [x] [RabbitMQ 3.7.7](http://www.rabbitmq.com)：消息队列。版本3.7.7
- [x] [ELK日志分析 6.3.2](https://www.elastic.co/cn/downloads)：ELK日志分析。版本6.3.2
    - [Elasticsearch 6.3.2](https://www.elastic.co/downloads/elasticsearch)：基于Lucene的搜索引擎，版本6.3.2
    - [Logstash 6.3.2](https://www.elastic.co/downloads/logstash)：分析log日志，版本6.3.2
    - [Kibana 6.3.2](https://www.elastic.co/downloads/kibana)：开源的分析与可视化平台,设计出来用于和Elasticsearch一起使用的，版本6.3.2
- [x] [Spring Boot Admin 2.0.2](https://github.com/codecentric/spring-boot-admin)：服务监控，用于监控版本号、服务在线状态、Logging日志级别管理、JMX beans管理、Threads会话和线程管理、Trace应用请求跟踪、应用运行参数信息（Java 系统属性、Java 环境变量属性、内存信息、Spring 环境属性)。版本2.0.2
- [x] [MyBatis](http://www.mybatis.org/mybatis-3/zh/index.html)
- [x] [Oracle 11g](https://www.oracle.com/index.html)：尽量先不要升级到Oracle 12c，12c删除了一些本项目今后会采用的函数，比如WM_CONCAT。
- [x] [Redis](https://redis.io/)：缓存服务器
- [x] [Druid](http://druid.io/)：阿里高性能数据库连接池
- [x] [Logback](https://logback.qos.ch/)：Logback是由log4j创始人设计的又一个开源日志组件，可以理解log4j的升级版，详情自行百度
- [x] [Jasypt](https://github.com/ulisesbocchio/jasypt-spring-boot)：配置文件加密
- [x] [IM](https://gitee.com/leiyuxi/cy-chat-room)：整合站内作者chenyi的cy-chat-room的开源项目2次开发
- [ ] [七牛云文件存储服务](https://developer.qiniu.com/kodo/sdk/1239/java)：后续采用七牛云进行图片存储（目前尚未完成）

- 项目可能用到的开发工具
    - 开发工具：[Intellij Idea](https://www.jetbrains.com/)、[Eclipse](http://www.eclipse.org/downloads/eclipse-packages/)
        - Intellij Idea和Eclipse我就不多介绍了。建议用Intellij Idea，从入行开始最初的MyEclipse到用了好多年的Eclipse。
        - 心血来潮尝试了一下Intellij Idea，起初只是尝试一下。最初的一周简直各种不习惯。经过了一周调整个性化设置后欲罢不能，现彻底放弃Eclipse
        - Intellij Idea收费，Eclipse免费。如果可以请支持正版~  
    - Redis可视化工具：[RedisDesktopManager](https://redisdesktop.com/download)可视化的redis操作用具，简单、粗暴、有效！并且更新频率很不错！
    - 数据库工具：[PLSQL Developer](https://www.allroundautomations.com/bodyplsqldevreg.html)、[Navicat](http://www.navicat.com.cn/)
        - 如果你用Oracle数据库，推荐用PLSQL Developer，这个工具可以自定义快捷替换，自定义快捷键。缺点是只能连Oracle。当然还有其他工具Toad、Oracle SQL Developer等，看你心情！
        - 如果你用Mysql，推荐用Navicat。这个工具可以可视化操作多种数据库，但是自定义个性化习惯方面差点意思（也可能我没用明白）。
    - 接口调试：[Postman](https://www.getpostman.com/apps)

### 项目结构说明
``` lua
xiye-cloud
├── xiye-eureka   -- 服务注册与发现[8888]
├── xiye-admin    -- 服务监控[8880]
├── xiye-config   -- 配置中心[8887]
├── xiye-zuul     -- ZUUL网关[9000]
├── xiye-common   -- 系统公共模块(各种公共实体、工具类、插件) 
├── xiye-system   -- 系统管理[9001]（未完）
├── xiye-office   -- OA办公[9002]（待开展）
├── xiye-company  -- 企业管理[9003]（待开展）
├── xiye-wechat   -- 微信管理[9004]（待开展）
├── xiye-cms      -- CMS管理[9005]（待开展）
└── xiye-im       -- 即时通信[9006，9106]（完成）

--服务监控（完成）
├── Spring Boot Admin 2.0.2 -- 服务监控[8880]
├── ELK 6.3.2 -- ELK日志分析[5601]
├── RabbitMQ 3.7.7-- 消息队列[15672]
├── Zipkin 2.11.1 -- 链路追踪[9411]
├── Swagger-Bootstrap-UI 1.8.1 -- 接口文档[localhost:9000/doc.html(需要登录后再访问，不然会被挡在门外)] 
├── Hbase 1.2.6-- Hbase数据库访问地址[16010]
└── Pinpoint 1.5.1   -- 链路追踪[28080]

服务监控先暂时就弄这些了，有时间再弄。这些服务并不在项目内，请自行去各自的官网下载相应的版本并配置调试。
```
### 项目结构图（图有点大，对付看吧，不行就down到电脑里看~。~）
 
       
 

### 项目进度图
 
       
 

### 数据库表结构
 
       
 

### 项目运行部署
- 安装并配置[JDK](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)及环境变量，JDK1.8及以上！
- 安装并启动[Redis](https://redis.io/)尽量带密码启动
- 安装并配置[Maven](http://maven.apache.org/download.cgi)尽量配置本地仓库，修改conf/settings.xml指定路径
- 修改配置文件 `bootstrap.yml` 相应的oracle、redis连接配置，改成自己的
- 附件提供Oracle数据库的dmp文件        
- 使用Intellij Idea导入该Maven项目,并Install
- 启动Oracle数据库服务
- 启动Oracle监听
- 启动RabbitMQ
- 启动Redis
- 为了防止maven下载不来json-lib-2.4.jar包导致net.sf.json.JSONArray的jsonobject.fromobject或jsonarray.fromobject不让使用,附件上提供了该jar包，请按层级自行放到本地仓库
- 依次启动运行 `XiyeEurekaApplication.java` 、`XiyeAdminApplication.java` 、`XiyeConfigApplication.java` 、`XiyeZuulApplication.java`、`XiyeSystemApplication.java`（开发期间如果不想监控，可以不启动XiyeAdminApplication，服务监控那一套也可以不启）
   
- 配置文件可使用Jasypt加密，可xiye-common项目中 `com.xiye.common.util` 包中找到 JasyptUtil 工具类生成加解密结果
```yaml
# 配置文件加密key
jasypt:
  encryptor:
    password: xiye

spring:
  # 数据源
  datasource:
    # Jasypt加密 可到xiye-common项目中com.xiye.common.util目录中找到JasyptUtil加解密工具类生成加密结果 格式为ENC(加密结果)
    password: ENC(9SkWYSSithVzv5U6iEgMvQ==)
```

### 最后聊几句

- 最近生活中事比较杂时间上很零碎，所以更新上不会太快，尤其业务逻辑功能的更新上会更慢，会优先更新基础功能。
- 如果没有意外情况，会按照项目的进度图顺序进行开发。
- 一些基础问题，请先百度，因为我的回复可能并不会比百度的攻略更详细，你需要做的只是从中挑一个你能看懂的方式进行修改
- 关于遇到的问题，加群或者直接留言。一般情况礼拜1-5白天上班期间会不定期回复。
- 引用的第三方项目或技术基本上不会对其进行源码更改。遇到一系列问题直接在第三方作者的项目下进行留言修复后我会更新~
- 关于Mac版的部署文档，请先自行尝试。这个文档的时间会排的很靠后。
- 关于Docker的部署，同上。并且Docker用的不是很纯熟，等时间充裕的情况下再弄。
- 暂时功能计划上就这么多，如果有想添加的模块，请留言。如果技术上我可以满足，那么会加上。
- Oauth2.0认证方式这一版不会出，下一版再说！
- 前端基于vue的iview模板，刚入坑vue，各种雷需要一步一步趟，碰到的就改。
- 前端的坑会比后端多，毕竟刚入坑vue，希望有精通vue的小伙伴帮忙搞一搞前端！
- 手里资源没有满足配置的服务器，只部署最基本的功能（卍解所有功能和监控在一台机器内存消耗大约12、3个G）！
- 监控服务看情况能部署几个算几个。主要是监控服务占用比较高。希望有小伙伴可以提供空闲服务器进行演示一段时间！
- xiye-eureka、xiye-config、xiye-zuul、xiye-system、oracle服务和监听、rabbitmq、redis为必启项！
- 我曾经是护卫艾泽拉斯的战士，如果我没有回归艾泽拉斯那更新速度还可以接受。但我要是回归了艾泽拉斯，那。。呵呵！

### 技术疑问交流
- 给作者项目Star或捐赠后可加入交流群 `826283463`



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)