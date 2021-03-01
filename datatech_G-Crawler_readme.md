
G-Crawler 项目简介  
   
    G-Crawler爬虫技术交流 559745472 欢迎加群讨论，快速启动！！！ 


项目目标
     在力所能及的情况下，最大限度的提高 Web爬虫开发人员的生产力，爬虫框架里的一股清流

主要功能
   基于WebMagic开发的完整的分布式爬虫框架，该框架特点如下：
1、完全分布式：由管理端（Admin）、调度端（Master）和多个Worker组成，各个组件通过Http协议通信。
2、完全配置化：通过Admin端的页面配置规则就可以爬取任何网站的数据，当然不同网站的难度不一样，会有不同的组件分别针对处理登录、验证码、封IP等问题。
3、可扩展的任务队列：任务队列由Redis实现，根据任务的状态有四种不同的任务队列：初始、执行中、成功、失败。您也可以扩展不同的任务调度算法，默认是公平调度。
4、可定义持久化方式：爬取结果中，属性数据默认持久化到MonogoDB，图片会被下载到文件服务器，当然您可以扩展更多的存储类型。
5、稳定和容错：任何一个爬虫任务都会重试和记录，只有任务真正成功了才会被移到成功队列，失败会有失败的原因描述。


技术选型
● 核心框架：Webmagic Spring boot 
● 任务调度：Spring + Quartz
● 持久层框架：Spring Jpa 
● 数据库&连接池：Alibaba Druid MongoDB MySql
● 缓存框架：Redis Ehcache 
● 日志管理：SLF4J、Log4j2
● 前端框架： Bootstrap + Jquary


开发环境配置：

  1.安装JDK8 
  2.安装mysql数据库，用作存储解析规则等数据，需要创建一个“yayCrawler”的数据库实例，并执行quartz相关的数据库脚本：quartz.sql（见发布包或源码）。
  3.安装redis
  4.安装mongoDB用于存放结果数据
  5.安装ftp服务器软件ftpserver（可选，用于存放下载图片）

启动说明：

  导入项目，maven install 安装 Admin,Worker,Master 模块。 然后生成的Jar拷贝到 crawler.worker /  deploy 目录中，记住改配置文件里面的Redis,mysql mogodb 的IP ,点击start.bat启动。

 （Linux & Windwos）
  java -jar worker.war --spring.config.location=worker_local.properties
 
  
关闭命令：
(Windows)
  for /f "tokens=1-5 delims= " %%a in ('"netstat -ano|findstr "^:8086""') do taskkill /f /pid %%e


各组件通信说明：

一、Admin
    Admin层主要负责页面抽取规则配置，页面Site配置，资源管理和任务发布

二、Master
    分布式爬虫的控制中心，接受Admin发布的任务，并分派任务给worker执行。
    2.1、接收发布任务
    2.2、接受Worker的注册
三、Worker
    真正干事情的苦逼青年，接受Master分派的任务并执行，定时向Master汇报心跳

  

Docker镜像：
         制作中。。。。。.。。。。。。。。。。。。。。

开发者交流群号

G-Crawler爬虫技术交流  559745472 


![输入图片说明](http://git.oschina.net/uploads/images/2016/0810/142122_594505a2_302008.png "在这里输入图片标题")
 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)