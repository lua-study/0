
YayCrawler 项目简介  
   
    YayCrawler爬虫技术交流 559745472 欢迎加群讨论，快速启动！！！ 


项目目标  
     在力所能及的情况下，最大限度的提高 Web爬虫开发人员的生产力，爬虫框架里的一股清流
    
主要功能  
   基于WebMagic开发的完整的分布式爬虫框架，该框架特点如下：  
1. 完全分布式：由管理端（Admin）、调度端（Master）和多个Worker组成，各个组件通过Http协议通信。  
2. 完全配置化：通过Admin端的页面配置规则就可以爬取任何网站的数据，当然不同网站的难度不一样，会有不同的组件分别针对处理登录、验证码、封IP等问题。  
3. 可扩展的任务队列：任务队列由Redis实现，根据任务的状态有四种不同的任务队列：初始、执行中、成功、失败。您也可以扩展不同的任务调度算法，默认是公平调度。  
4. 可定义持久化方式：爬取结果中，属性数据默认持久化到MonogoDB，图片会被下载到文件服务器，当然您可以扩展更多的存储类型。  
5. 稳定和容错：任何一个爬虫任务都会重试和记录，只有任务真正成功了才会被移到成功队列，失败会有失败的原因描述。  

    
技术选型
● 核心框架：Webmagic Spring boot   
● 任务调度：Spring + Quartz  
● 持久层框架：Spring Jpa   
● 数据库&连接池：Alibaba Druid MongoDB MySql  
● 缓存框架：Redis Ehcache   
● 日志管理：SLF4J、Log4j2  
● 前端框架： Bootstrap + Jquery  

    
开发环境配置：
    
  1. 安装JDK8  
  2. 安装mysql数据库，用作存储解析规则等数据，需要创建一个“yayCrawler”的数据库实例，并执行quartz相关的数据库脚本：quartz.sql（见发布包或源码）。  
  3. 安装redis  
    可直接使用本目录下redis-win64.zip  
    常用命令：  
    redis注册到windows服务： redis-server --service-install redis.windows-service.conf --loglevel verbose  
    卸载服务：redis-server --service-uninstall  
    开启服务：redis-server --service-start  
    停止服务：redis-server --service-stop  
  4. 安装mongoDB用于存放结果数据  
    下载 https://fastdl.mongodb.org/win32/mongodb-win32-x86_64-2008plus-ssl-4.0.5-signed.msi  
    安装后修改 MongoDB\Server\4.0\bin\mongod.cfg 文件，将bindIp改为实际ip，以便可远程访问  
  5. 安装ftp服务器软件ftpserver（可选，用于存放下载图片）  

启动说明：
    
  1. 导入项目，maven install 安装 Admin,Worker,Master 模块。 然后生成的Jar拷贝到各自deploy 目录中，记住改配置文件里面的Redis,mysql mogodb 的IP ,点击start.bat启动。      
  2. 启动顺序：worker，master，admin  
 
 （Linux & Windows）  
  java -jar worker.war --spring.config.location=worker_local.properties
 
  
关闭命令：  
(Windows)  
  for /f "tokens=1-5 delims= " %%a in ('"netstat -ano|findstr "^:8086""') do taskkill /f /pid %%e

Linux下部署说明：
  master：
    application.properties:
    server.port=8068
    server.address=127.0.0.1    
    server.context-path=/master
  admin:
    application.properties:
    #Master的服务地址
    master.server.address=http://127.0.0.1:8068/master/
    server.port=8069
    server.address=127.0.0.1    
    server.context-path=/admin  
  worker：
    application.properties:
    master.server.address=http://127.0.0.1:8068/master/
    context.path=http://127.0.0.1:8086/worker/
    server.port=8086
    server.address=127.0.0.1    
    server.context-path=/worker  

各组件通信说明：

一、Admin
    Admin层主要负责页面抽取规则配置，页面Site配置，资源管理和任务发布
    Admin spring boot方式若无法启动成功，8069端口无法telnet到，则使用tomcat部署，只需修改tomcat端口即可
二、Master
    分布式爬虫的控制中心，接受Admin发布的任务，并分派任务给worker执行。  
    2.1、接收发布任务  
    2.2、接受Worker的注册  
三、Worker
    真正干事情的苦逼青年，接受Master分派的任务并执行，定时向Master汇报心跳

    
配置要点：  
1. 分页抓取，  
    url正则配置要包含分页参数：^http://www2.hkej.com/instantnews[?]page=[0-9]$  
    作业提交时，url不用带分页参数：http://www2.hkej.com/instantnews ；请求参数中分页 {"$pagination_page":{'START':'1','END':'5','STEP':'1'}}  
2. url正则，为mysql的正则，比如不支持\w \d这些  
3. 链式抓取，先抓列表界面的详情链接，然后在详情中去抓取标题，时间，内容这些字段。不要在列表界面抓取标题。    

Docker镜像：
         制作中。。。。。.。。 

开发者交流群号

YayCrawler  爬虫技术交流  559745472 

install jar :  https://git.oschina.net/shentong_012

![输入图片说明](http://git.oschina.net/uploads/images/2016/1012/110209_e7df5de8_302008.png "在这里输入图片标题")


![输入图片说明](http://git.oschina.net/uploads/images/2016/0810/142122_594505a2_302008.png "在这里输入图片标题")
 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)