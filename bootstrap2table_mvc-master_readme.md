# mvc-master

#### 项目介绍﻿
mvc-master是springMVC项目，整合项目技术点，目前升级到4.3.13版本,欢迎大家提出宝贵意见,您的宝贵意见，是我们进步的动力。
 
#### **项目说明**

- 项目基于maven的多profile环境配置，打包时需要选择(test/pro/dev)打包运行的环境。


#### **项目特点** 
> * 友好的代码结构及注释，便于阅读及二次开发 。 
> * 前端页面采用jsp+freemaker，多视图解析处理，优先jsp,采用bootstrap-table强大灵活的表格插件渲染数据。   
> * 后端配置swagger在线文档，方便编写API接口文档。  
> * 引入druib,fastjson,cors,xss,redis-cluster,redis配置。 
> * 引入API模板，根据token作为登录令牌，极大的方便了APP接口开发。 
> * 配置全局异常处理,mybatis,pagehelper分页。 
> * 配置通用日志打印，采用异步线程池日志写入数据库，方便开发寻找异常。 
> * 配置redisson集群模式,使用分布式锁，保证并发的数据一致性。 
> * 配置jta分布式事务，使用atomikos分布式事务处理方案。 
> * 引入druib,javaMelody监控系统各项指标，分析系统瓶颈。 
> * 配置quartz定时器，开启集群版，cron表达式配置数据库，支持手动重启，停止任务。 
> * 配置fileupload(默认配置最大100MB)，下载文件，生成二维码，二维码打印，mail发邮件等功能。 
> * 配置poi和csv简单导出excel功能点,poi目前是多sheet智能导出。 

####  **项目结构**
```
mvc-master
│
├─doc 项目SQL文件
│  ├─isec  数据库isec文件
│  └─qdone 数据库isec文件
│
├─core 框架配置
│
├─mvc 功能模块
│  ├─controller 控制层
│  ├─mapper sql文件
│  ├─model 数据库实体类
│  ├─mybatis sql文件
│  ├─service 业务层
│  ├─task 注解定时任务
│  └─test 模块测试
│ 
├─util 系统工具
│ 
├─module 功能模块
│  ├─app API接口模块(APP调用)
│  ├─interceptor APP权限拦截器
│  ├─job 定时任务
│  ├─solr solr操作
│  └─util 模块工具
│  
├──resources 
│     ├─spring spring配置xml
│     ├─conf   系统配置properties
│     ├─jta.properties  jta配置
│     ├─freemarker.properties   freemarker配置
│     ├─log4j.properties   log4j日志配置
│     ├─mybatis-config.xml   mybatis配置
│     └─spring-mvc.xml springMvc配置
```


####  **环境配置:**
- 1.项目依赖,redis-cluster集群,activeMq,solr,redis工具。 
- 2.doc目录里面有初始化sql，运行项目前，请先创建mysql。 
- 3.工具地址:https://pan.baidu.com/s/1Bm7udGJc40xEENFgnJjsIw  

####  **启动说明:**
- 1.创建mysql数据库isec和qdone实例，运行doc目录里面的sql文件。 
- 2.启动redis集群,(127.0.0.1:6379~6384，密码:qdone) 
- 3.启动activeMq(默认单机版) 
- 4.启动solr(默认单机版) 
- 5.eclipse工具下，项目运行maven build: 
- &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;goals:&nbsp;&nbsp;clean install 
- &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;profile:&nbsp;&nbsp;test/pro/dev(三选一，必填) 
- &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;勾选&nbsp;&nbsp; update snapshots和skip tests 
- &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;执行run之后,拷贝target目录下mvc.war 
- 6.配置tomcat,加入mvc.war，启动tomcat 
- 7.访问http://ip:port/mvc 
	
####  **用户反馈：**
- GitHub： https://github.com/apple987/mvc_action 
- 码云仓库：https://gitee.com/bootstrap2table/mvc-master 
- 邮箱地址: m15171479289@163.com  
		
		

        

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)