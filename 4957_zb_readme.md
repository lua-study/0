# zb

- 支付技术交流QQ群 ：470414533
- 联系QQ : 842324724
- 联系邮箱 ： 842324724@qq.com

详细技术讨论请加QQ群，营造一个温馨、有质量的技术学习空间。

## 前言

　　`zb`项目创建于2017年5月12日，正在慢慢成长中，目的是随着技术积累而慢慢开发一套分布式架构系统。全部采用目前主流技术与框架，为在技术方面有需要的朋友提供一套完整的研究学习实例。

## 项目介绍

　　基于Spring+SpringMVC+Mybatis分布式敏捷开发系统架构，提供整套公共微服务服务模块：内容管理、支付中心、用户管理（包括第三方）、微信服务系统、文件存储系统、配置中心、日志分析、任务和消息通知等。
 　　以上模块目前只是开发了用户管理系统，由于时间与精力有限，加上技术上本人也并非大牛，项目框架与代码都需要重新设计和整理，后期会慢慢的整理。上面模块是我的目标。

### 组织结构

``` lua
zb
├── zb-common -- 公共配置与工具类模块
|    ├── zb-config -- 配置管理中心
|    ├── zb-util -- 工具类、全局辅助类等
├── zb-ucenter -- 用户系统(包括第三方登录)
|    ├── zb-ucenter-dao -- 数据访问层
|    ├── zb-ucenter-rpc-api -- rpc接口包
|    ├── zb-ucenter-rpc-service -- rpc服务提供者
|    └── zb-ucenter-server -- dubbo服务注册模块
|    └── zb-ucenter-web -- 网站前台
├── zb-wechat -- 微信系统
|    ├── zb-wechat-rpc-api -- rpc接口包
|    ├── zb-wechat-rpc-service -- rpc服务提供者
|    └── zb-wechat-server -- dubbo服务注册模块
├── zb-oa -- OA办公系统
|    ├── zb-oa-rpc-api -- rpc接口包
|    ├── zb-oa-rpc-service -- rpc服务提供者
|    └── zb-oa-server -- dubbo服务注册模块
|    └── zb-oa-web -- 网站前台
├── zb-mq -- MQ消息队列服务系统
|    ├── zb-mq-rpc-api -- rpc接口包
|    ├── zb-mq-rpc-service -- rpc服务提供者
|    └── zb-mq-server -- dubbo服务注册模块
├── zb-oauth -- SSO单点登录模块(CAS源码)
├── zb-entity -- 用户实体模块
└── zb-socket -- socket服务推送模块
```

### 技术选型

#### 后端技术:
技术 | 名称 | 官网
------|-------|-------
Log4J | 日志组件 | [http://logging.apache.org/log4j/1.2/](http://logging.apache.org/log4j/1.2/)
Maven | 项目构建管理 | [http://maven.apache.org/](http://maven.apache.org/)
Spring Framework | 容器 | [http://projects.spring.io/spring-framework/](http://projects.spring.io/spring-framework/)
SpringMVC | MVC框架 | [http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#mvc](http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#mvc)
Apache Shiro | 权限管理框架  | [http://shiro.apache.org/](http://shiro.apache.org/)
MyBatis | ORM框架  | [http://www.mybatis.org/mybatis-3/zh/index.html](http://www.mybatis.org/mybatis-3/zh/index.html)
Mapper | Mybatis封装框架  | [http://git.oschina.net/free/Mapper/](http://git.oschina.net/free/Mapper/)
PageHelper | MyBatis分页插件  | [http://git.oschina.net/free/Mybatis_PageHelper/](http://git.oschina.net/free/Mybatis_PageHelper/)
ZooKeeper | 分布式协调服务  | [http://zookeeper.apache.org/](http://zookeeper.apache.org/)
Dubbo | 分布式服务框架  | [http://dubbo.io/](http://dubbo.io/)
Redis | 分布式缓存数据库  | [https://redis.io/](https://redis.io/)
Quartz | 作业调度框架  | [http://www.quartz-scheduler.org/](http://www.quartz-scheduler.org/)
ActiveMQ | 消息队列  | [http://activemq.apache.org/](http://activemq.apache.org/)
Disconf | 分布式配置管理平台  | [http://disconf.readthedocs.io/zh_CN/latest/](http://disconf.readthedocs.io/zh_CN/latest/)
SockJS | websocket封装框架  | [https://github.com/sockjs/sockjs-client/](https://github.com/sockjs/sockjs-client/)
CAS | 单点登录认证系统  | [https://www.apereo.org/projects/cas/](https://www.apereo.org/projects/cas/)
Netty | 网络应用程序通信框架  | [http://netty.io/](http://netty.io/)
Activiti | 工作流框架  | [https://www.activiti.org/](https://www.activiti.org/)
MessagePack | 对象序列化类库  | [http://msgpack.org/](http://msgpack.org/)
Mycat | 数据库分库分表中间件  | [http://www.mycat.io/](http://www.mycat.io/)


#### 前端技术:
技术 | 名称 | 官网
----|------|----
jQuery | 函式库  | [http://jquery.com/](http://jquery.com/)
Bootstrap | 前端框架  | [http://getbootstrap.com/](http://getbootstrap.com/)
zTree | 树插件  | [http://www.treejs.cn/](http://www.treejs.cn/)
jQuery DataTable | 表格插件  | [http://datatables.club/](http://datatables.club/)
jQuery Validation | 表单验证插件  | [https://jqueryvalidation.org/](https://jqueryvalidation.org/)
msgbox | 漂亮提示信息插件  | [http://www.jq22.com/jquery-info1966](http://www.jq22.com/jquery-info1966)
My97DatePicker | 日期控件  | [http://www.my97.net/dp/demo/index.htm](http://www.my97.net/dp/demo/index.htm)
UEditor | 百度富文本编辑器  | [http://fex.baidu.com/ueditor/](http://fex.baidu.com/ueditor/)
ECharts | Javascript图表库  | [http://echarts.baidu.com/feature.html](http://echarts.baidu.com/feature.html)
Highcharts | Javascript图表库  | [https://www.hcharts.cn/demo/highcharts](https://www.hcharts.cn/demo/highcharts)
H-ui | H-ui 前端框架  | [http://www.h-ui.net/](http://www.h-ui.net/)
H-ui.admin | 网站后台模版  | [http://www.h-ui.net/H-ui.admin.shtml](http://www.h-ui.net/H-ui.admin.shtml)
Layer | web弹层组件  | [http://layer.layui.com/](http://layer.layui.com/)
SockJS | client与server通信框架(类似websocket)  | [http://sockjs.org](http://sockjs.org)


#### 模块介绍

> zb-common

- 公共资源文件、工具类、配置等信息

> zb-entity

- 实体bean模块

> zb-oauth

- CAS单点登录模块，CAS源代码

> zb-socket

- 服务器消息推送模块。后端使用了spring-websocket服务器端通信框架。前端使用了sockjs作为连接服务器端通信的javascript api。
- SockJS是一个浏览器JavaScript库，它提供了一个类似WebSocket的对象。SockJS为您提供了一个连贯，跨浏览器的JavaScript API，可在浏览器和Web服务器之间创建低延迟，全双工，跨域通信通道。
- 在引擎罩下，SockJS首先尝试使用本机WebSockets。如果失败，它可以使用各种特定于浏览器的传输协议，并通过类似WebSocket的抽象来呈现它们。
- SockJS旨在适用于所有现代浏览器和不支持WebSocket协议的环境。

> zb-mq

- MQ消息服务模块，目前采用了activemq作为消息服务的框架。
- 简单实现了订单同步消息的发送处理、微信模板消息的发送处理。
- 优点是消息的异步通知与处理。高并发情况下缓解系统压力，提高系统业务处理能力。

> zb-oa

- OA办公系统，目前暂未开发，后期会开发。集成cas单点登录功能，实现多个项目的统一登录认证。

> zb-ucenter

- 用户管理中心系统，提供用户角色与权限管理
- 目前所有功能开发都在此模块中(功能有限，如果分布到其他模块，有点小题大做，不易于学习，后期功能多了之后再慢慢分工)，后期会将不同功能分布到其他模块管理。

> zb-wechat

- 微信功能模块。对微信多数接口进行了接口封装，方便使用。

## 环境搭建

(后期补充)

#### 开发工具:
- MySql: 数据库(目前数据库连接的是我的服务器mysql)
- Tomcat: 应用服务器
- Git: 版本管理(目前项目源码托管于开源中国，暂不支持其他人员一起开发)
- Nginx: 反向代理服务器(本地开发环境无须安装，线上环境需要安装，实现动静分离)
- eclipse: 开发IDE
- PowerDesigner: 建模工具
- Navicat for MySQL: 数据库客户端（或者使用SQLyog）
- Mycat: 数据库分库分表中间件。(本地开发无须安装，只是在服务器环境上配置数据库主从、mycat服务)
#### 开发环境：
- Jdk7+
- Mysql5.5+
- Redis (可连接我的服务器中的redis服务)
- Zookeeper (可连接我的服务器中的redis服务)
- ActiveMQ (可连接我的服务器中的redis服务)
- Dubbo-admin (可访问我的服务器中的dubbo-admin：http://www.2b2b92b.com:4050/dubbo-admin)

### 工具安装

(后期补充)

### 资源下载

- JDK7 [http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase7-521261.html](http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase7-521261.html "JDK7")
- Maven [http://maven.apache.org/download.cgi](http://maven.apache.org/download.cgi "Maven")
- Redis [https://redis.io/download](https://redis.io/download "Redis")
- ActiveMQ [http://activemq.apache.org/download-archives.html](http://activemq.apache.org/download-archives.html "ActiveMQ")
- ZooKeeper [http://www.apache.org/dyn/closer.cgi/zookeeper/](http://www.apache.org/dyn/closer.cgi/zookeeper/ "ZooKeeper")
- Dubbo [http://dubbo.io/Download-zh.htm](http://dubbo.io/Download-zh.htm "Dubbo")
- Elastic Stack [https://www.elastic.co/downloads](https://www.elastic.co/downloads "Elastic Stack")
- Nginx [http://nginx.org/en/download.html](http://nginx.org/en/download.html "Nginx")
- Jenkins [http://updates.jenkins-ci.org/download/war/](http://updates.jenkins-ci.org/download/war/ "Jenkins")
- dubbo-admin-2.5.3 [http://download.csdn.net/detail/shuzheng5201314/9733652](http://download.csdn.net/detail/shuzheng5201314/9733652 "dubbo-admin-2.5.3")
- dubbo-admin-2.5.4-SNAPSHOT-jdk8 [http://download.csdn.net/detail/shuzheng5201314/9733657](http://download.csdn.net/detail/shuzheng5201314/9733657 "dubbo-admin-2.5.4-SNAPSHOT-jdk8")
- 更多资源请加QQ群

## 开发指南:

- 1、请确保自己本机已经安装Jdk7、maven(建议使用阿里云的maven仓库)
- 2、如果想自己搭建服务，那么请确保自己本机安装好以下服务：Mysql、Redis、Zookeeper、ActiveMQ并**启动相关服务**，使用默认配置默认端口即可，其中，MQ可不安装，不影响项目启动，如果想使用zb-mq模块功能，需要启动activemq服务。
- 3、克隆当前项目的源代码到本地并打开，**我使用的是Eclipse Java EE IDE for Web Developers.**，通过maven方式导入到eclipse中。
- 4、项目中存在activiti工作流框架，对于.bpmn工作流文件的设计与管理，需要安装eclipse的一个插件，才可对文件进行可视化设计。除非你对文件配置非常熟悉，可手动编码。

### 修改本地Host

- 由于项目使用了cas单点登录，如果不想连接我的服务器的CAS服务，就需要你打包好zb-oauth这个模块，配置好自己的域名。
- 域名的话，可以通过修改本机host文件指定。CAS不支持ip访问的，所以需要配置域名

### 编译流程

maven的编译打包，我就不多说了。如果在项目编译或者打包部署期间出现了什么问题，可以联系我询问。

### 启动顺序（后台）

> 环境配置准备工作（如果想自己搭建环境，请确保安装以下服务）：

- mysql数据库，导入zb-ucenter-web模块下的[sql脚本]文件夹下的sql文件。

- 安装redis、zookeeper、activemq、disconf(觉得麻烦的可不修改，使用我的服务器服务即可)、cas单点登录服务(也可不修改，使用我的服务器的cas)

- 修改zb-conf模块下的各种连接等配置信息

- 启动Zookeeper、Redis、ActiveMQ、Disconf(使用本机服务的话需要启动服务)、CAS(使用本机服务的话需要启动服务)

> **zb-ucenter**

- 首先启动 zb-ucenter-server (dubbo服务注册)，再启动zb-ucenter-web (dubbo服务订阅)

- 访问 zb-ucenter-web，默认帐号/密码：admin/123456

- 登录成功后，方可操作(目前还未实现多系统的单点登录集成认证)。

> **zb-mq**

- 目前MQ功能还未集成到项目中，后期会加入进来



### 部署方式

- war包项目：使用tomcat等web容器启动

### 框架编码规范约定

约定优于配置(convention over configuration)，此框架约定了很多编程规范，比如：

```

- service类，需要在叫名`service`的包下，并以`Service`结尾，如`UserServiceImpl`

- controller类，需要在以`controller`结尾的包下，类名以Controller结尾，如`UserController.java`

- spring task类，需要在叫名`task`的包下，并以`Task`结尾，如`TestTask.java`

- mapper.xml，需要放到zb-*-dao模块对应的包下，并以`Mapper.xml`结尾，如`UserMapper.xml`

- mapper接口，需要放到zb-*-dao模块对应的包下，并以`Mapper`结尾，如`UserMapper.java`

- entity实体类，需要放到zb-entity模块下，命名规则为数据表转驼峰规则，如`SysUser.java`

- spring配置文件，命名规则为`spring-*.xml`

- 类名：首字母大写驼峰规则；方法名：首字母小写驼峰规则；常量：全大写；变量：首字母小写驼峰规则，尽量非缩写

- 全局的配置文件放到zb-conf模块下的`src/main/resources`目录下，单独的项目模块的配置文件，放到对应的模块下的`src/main/resources`

- 前端静态资源文件放到`src/main/webapp/resources`目录下

- jsp文件，需要在`/WEB-INF/view`目录下

- 模块命名为`项目`-`子项目`-`业务`，如`zb-ucenter-web`

- 更多规范，参考[阿里巴巴Java开发手册] http://git.oschina.net/zhoubang85/zb/attach_files

```

## 演示地址(目前只发布了[用户管理中心系统：zb-ucenter-web])

演示地址： [http://www.2b2b92b.com](http://www.2b2b92b.com "用户管理中心系统访问地址")

### 预览图
![login](zb-doc/preview/login.jpg)
![userlist](zb-doc/preview/userlist.jpg)
![tomcatlogmonitor](zb-doc/preview/tomcatlogmonitor.jpg)
![nettychat](zb-doc/preview/nettychat.jpg)
![socketpushall](zb-doc/preview/socketpushall.jpg)
![wxmsgtemplate](zb-doc/preview/wxmsgtemplate.jpg)
![activitibpmnlist](zb-doc/preview/activitibpmnlist.jpg)
![addrole](zb-doc/preview/addrole.jpg)
![msgalert](zb-doc/preview/msgalert.jpg)
![myactprocessrecord](zb-doc/preview/myactprocessrecord.jpg)
![permissionadd](zb-doc/preview/permissionadd.jpg)
![socketpushmy](zb-doc/preview/socketpushmy.jpg)
![myactiviti](zb-doc/preview/myactiviti.jpg)
![themegreencloor](zb-doc/preview/themegreencloor.jpg)
![redcolor](zb-doc/preview/redcolor.jpg)
![deptactpproval](zb-doc/preview/deptactpproval.jpg)


### 数据模型

(后期补充)

## 附件

(后期补充)

### 优秀文章和博客

(后期补充)

### 在线小工具

- [在线Cron表达式生成器](http://cron.qqe2.com/ "在线Cron表达式生成器")

- [在线工具 - 程序员的工具箱](http://tool.lu/ "在线工具 - 程序员的工具箱")

### 在线文档

- [JDK7英文文档](http://tool.oschina.net/apidocs/apidoc?api=jdk_7u4 "JDK7英文文档")

- [Spring4.x文档](http://spring.oschina.mopaas.com/ "Spring4.x文档")

- [Mybatis3官网](http://www.mybatis.org/mybatis-3/zh/index.html "Mybatis3官网")

- [Dubbo官网](http://dubbo.io/ "Dubbo官网")

- [Nginx中文文档](http://tool.oschina.net/apidocs/apidoc?api=nginx-zh "Nginx中文文档")

- [Freemarker在线手册](http://freemarker.foofun.cn/ "Freemarker在线中文手册")

- [Bootstrap在线手册](http://www.bootcss.com/ "Bootstrap在线手册")

- [Git官网中文文档](https://git-scm.com/book/zh/v2 "Git官网中文文档")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)