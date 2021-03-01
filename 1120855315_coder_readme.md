# coder

## 前言

　　`coder`项目不仅仅是一个开发架构，而是努力打造一套从 **前端模板** - **基础框架** - **分布式架构** - **开源项目** - **持续集成** - **自动化部署** - **系统监测** - **无缝升级** 的全方位J2EE企业级开发解决方案。项目将打造一个开源的电商平台。

## 项目介绍

　　基于Spring+SpringMVC+Mybatis分布式敏捷开发系统架构，提供整套公共微服务服务模块：内容管理、支付中心、用户管理（包括第三方）、微信平台、存储系统、配置中心、日志分析、任务和通知等，支持服务治理、监控和追踪，努力为中小型企业打造全方位J2EE企业级开发解决方案。
组织结构

### 组织结构

``` lua
coder
├── coder-common -- SSM框架公共模块
├── coder-admin -- 后台管理模板
├── coder-ui -- 前台thymeleaf模板[端口:1000]
├── coder-config -- 配置中心[端口:1001]
├── coder-upms -- 用户权限管理系统
|    ├── coder-upms-common -- upms系统公共模块
|    ├── coder-upms-dao -- 代码生成模块，无需开发
|    ├── coder-upms-client -- 集成upms依赖包，提供单点认证、授权、统一会话管理
|    ├── coder-upms-rpc-api -- rpc接口包
|    ├── coder-upms-rpc-service -- rpc服务提供者
|    └── coder-upms-server -- 用户权限系统及SSO服务端[端口:1111]
├── coder-cms -- 内容管理系统
|    ├── coder-cms-common -- cms系统公共模块
|    ├── coder-cms-dao -- 代码生成模块，无需开发
|    ├── coder-cms-rpc-api -- rpc接口包
|    ├── coder-cms-rpc-service -- rpc服务提供者
|    ├── coder-cms-search -- 搜索服务[端口:2221]
|    ├── coder-cms-admin -- 后台管理[端口:2222]
|    ├── coder-cms-job -- 消息队列、任务调度等[端口:2223]
|    └── coder-cms-web -- 网站前台[端口:2224]
├── coder-pay -- 支付系统
|    ├── coder-pay-common -- pay系统公共模块
|    ├── coder-pay-dao -- 代码生成模块，无需开发
|    ├── coder-pay-rpc-api -- rpc接口包
|    ├── coder-pay-rpc-service -- rpc服务提供者
|    ├── coder-pay-sdk -- 开发工具包
|    ├── coder-pay-admin -- 后台管理[端口:3331]
|    └── coder-pay-web -- 演示示例[端口:3332]
├── coder-ucenter -- 用户系统(包括第三方登录)
|    ├── coder-ucenter-common -- ucenter系统公共模块
|    ├── coder-ucenter-dao -- 代码生成模块，无需开发
|    ├── coder-ucenter-rpc-api -- rpc接口包
|    ├── coder-ucenter-rpc-service -- rpc服务提供者
|    └── coder-ucenter-web -- 网站前台[端口:4441]
├── coder-wechat -- 微信系统
|    ├── coder-wechat-mp -- 微信公众号管理系统
|    |    ├── coder-wechat-mp-dao -- 代码生成模块，无需开发
|    |    ├── coder-wechat-mp-service -- 业务逻辑
|    |    └── coder-wechat-mp-admin -- 后台管理[端口:5551]
|    └── coder-ucenter-app -- 微信小程序后台
├── coder-api -- API接口总线系统
|    ├── coder-api-common -- api系统公共模块
|    ├── coder-api-rpc-api -- rpc接口包
|    ├── coder-api-rpc-service -- rpc服务提供者
|    └── coder-api-server -- api系统服务端[端口:6666]
├── coder-oss -- 对象存储系统
|    ├── coder-oss-sdk -- 开发工具包
|    ├── coder-oss-web -- 前台接口[端口:7771]
|    └── coder-oss-admin -- 后台管理[端口:7772]
├── coder-shop -- 电子商务系统

```
### 技术选型

#### 后端技术:
技术 | 名称 | 官网
----|------|----
Spring Framework | 容器  | [http://projects.spring.io/spring-framework/](http://projects.spring.io/spring-framework/)
SpringMVC | MVC框架  | [http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#mvc](http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#mvc)
Apache Shiro | 安全框架  | [http://shiro.apache.org/](http://shiro.apache.org/)
Spring session | 分布式Session管理  | [http://projects.spring.io/spring-session/](http://projects.spring.io/spring-session/)
MyBatis | ORM框架  | [http://www.mybatis.org/mybatis-3/zh/index.html](http://www.mybatis.org/mybatis-3/zh/index.html)
MyBatis Generator | 代码生成  | [http://www.mybatis.org/generator/index.html](http://www.mybatis.org/generator/index.html)
PageHelper | MyBatis物理分页插件  | [http://git.oschina.net/free/Mybatis_PageHelper](http://git.oschina.net/free/Mybatis_PageHelper)
Druid | 数据库连接池  | [https://github.com/alibaba/druid](https://github.com/alibaba/druid)
FluentValidator | 校验框架  | [https://github.com/neoremind/fluent-validator](https://github.com/neoremind/fluent-validator)
Thymeleaf | 模板引擎  | [http://www.thymeleaf.org/](http://www.thymeleaf.org/)
Velocity | 模板引擎  | [http://velocity.apache.org/](http://velocity.apache.org/)
ZooKeeper | 分布式协调服务  | [http://zookeeper.apache.org/](http://zookeeper.apache.org/)
Dubbo | 分布式服务框架  | [http://dubbo.io/](http://dubbo.io/)
TBSchedule & elastic-job | 分布式调度框架  | [https://github.com/dangdangdotcom/elastic-job](https://github.com/dangdangdotcom/elastic-job)
Redis | 分布式缓存数据库  | [https://redis.io/](https://redis.io/)
Solr & Elasticsearch | 分布式全文搜索引擎  | [http://lucene.apache.org/solr/](http://lucene.apache.org/solr/) [https://www.elastic.co/](https://www.elastic.co/)
Quartz | 作业调度框架  | [http://www.quartz-scheduler.org/](http://www.quartz-scheduler.org/)
Ehcache | 进程内缓存框架  | [http://www.ehcache.org/](http://www.ehcache.org/)
ActiveMQ | 消息队列  | [http://activemq.apache.org/](http://activemq.apache.org/)
JStorm | 实时流式计算框架  | [http://jstorm.io/](http://jstorm.io/)
FastDFS | 分布式文件系统  | [https://github.com/happyfish100/fastdfs](https://github.com/happyfish100/fastdfs)
Log4J | 日志组件  | [http://logging.apache.org/log4j/1.2/](http://logging.apache.org/log4j/1.2/)
Swagger2 | 接口测试框架  | [http://swagger.io/](http://swagger.io/)
sequence | 分布式高效ID生产  | [http://git.oschina.net/yu120/sequence](http://git.oschina.net/yu120/sequence)
AliOSS & Qiniu & QcloudCOS | 云存储  | [https://www.aliyun.com/product/oss/](https://www.aliyun.com/product/oss/) [http://www.qiniu.com/](http://www.qiniu.com/) [https://www.qcloud.com/product/cos](https://www.qcloud.com/product/cos)
Protobuf & json | 数据序列化  | [https://github.com/google/protobuf](https://github.com/google/protobuf)
Jenkins | 持续集成工具  | [https://jenkins.io/index.html](https://jenkins.io/index.html)
Maven | 项目构建管理  | [http://maven.apache.org/](http://maven.apache.org/)

#### 前端技术:
技术 | 名称 | 官网
----|------|----
jQuery | 函式库  | [http://jquery.com/](http://jquery.com/)
jquery-form | 弹出窗口插件  | [https://github.com/jquery-form/form#cdn](https://github.com/jquery-form/form#cdn)
Bootstrap | 前端框架  | [http://getbootstrap.com/](http://getbootstrap.com/)
Bootstrap-table | Bootstrap数据表格  | [http://bootstrap-table.wenzhixin.net.cn/](http://bootstrap-table.wenzhixin.net.cn/)
Font-awesome | 字体图标  | [http://fontawesome.io/](http://fontawesome.io/)
material-design-iconic-font | 字体图标  | [https://github.com/zavoloklom/material-design-iconic-font](https://github.com/zavoloklom/material-design-iconic-font)
Waves | 点击效果插件  | [https://github.com/fians/Waves](https://github.com/fians/Waves)
zTree | 树插件  | [http://www.treejs.cn/v3/](http://www.treejs.cn/v3/)
Select2 | 选择框插件  | [https://github.com/select2/select2](https://github.com/select2/select2)
jquery-confirm | 弹出窗口插件  | [https://github.com/craftpip/jquery-confirm](https://github.com/craftpip/jquery-confirm)
jQuery EasyUI | 基于jQuery的UI插件集合体  | [http://www.jeasyui.com](http://www.jeasyui.com)
React | 界面构建框架  | [https://github.com/facebook/react](https://github.com/facebook/react)
Editor.md | Markdown编辑器  | [https://github.com/pandao/editor.md](https://github.com/pandao/editor.md)
coderAdmin | 后台管理系统模板  | [https://github.com/shucoder/coderAdmin](https://github.com/shucoder/coderAdmin)
autoMail | 邮箱地址自动补全插件  | [https://github.com/shucoder/autoMail](https://github.com/shucoder/autoMail)
coder.jprogress.js | 加载进度条插件  | [https://github.com/shucoder/coder.jprogress.js](https://github.com/shucoder/coder.jprogress.js)
coder.jtotop.js | 返回顶部插件  | [https://github.com/shucoder/coder.jtotop.js](https://github.com/shucoder/coder.jtotop.js)
#### 架构图

![架构图](project-bootstrap/architect.png)

#### 模块依赖

![模块依赖](project-bootstrap/project.png)

#### 模块介绍

> coder-common

Spring+SpringMVC+Mybatis框架集成公共模块，包括公共配置、MybatisGenerator扩展插件、通用BaseService、工具类等。

> coder-admin

基于bootstrap实现的响应式Material Design风格的通用后台管理系统，`coder`项目所有后台系统都是使用该模块界面作为前端展示。

> coder-ui

各个子系统前台thymeleaf模板，前端资源模块，使用nginx代理，实现动静分离。

> coder-upms

本系统是基于RBAC授权和基于用户授权的细粒度权限控制通用平台，并提供单点登录、会话管理和日志管理。接入的系统可自由定义组织、角色、权限、资源等。用户权限=所拥有角色权限合集+用户加权限-用户减权限，优先级：用户减权限>用户加权限>角色权限

> coder-oss

文件存储系统，提供四种方案：

- **阿里云** OSS
- **腾讯云** COS
- **七牛云**
- 本地分布式存储

![阿里云OSS](project-bootstrap/aliyun-oss-post-callback.png)

> coder-api

服务网关，对外暴露统一规范的接口和包装响应结果，包括各个子系统的交互接口、对外开放接口、开发加密接口、接口文档等服务，可在该模块支持验签、鉴权、路由、限流、监控、容错、日志等功能。示例图：

![API网关](project-bootstrap/gateway_config.png)


> coder-cms

内容管理系统：支持多标签、多类目、强大评论的内容管理，有基本单页展示，菜单管理，系统设置等功能。

> coder-pay

- 一站式支付解决方案，统一下单接口，支持支付宝、微信、网银等多种支付方式。不涉及业务的纯粹的支付平台。

- 统一下单（统一下单接口、统一扫码）、订单管理、数据分析、财务报表、商户管理、渠道管理、对账系统、系统监控。

![统一扫码支付](project-bootstrap/coder-pay.png)

> coder-ucenter

通用用户管理系统， 实现最常用的用户注册、登录、资料管理、个人中心、第三方登录等基本需求，支持扩展二次开发。

> coder-wechat-mp

微信公众号管理平台，除实现官网后台自动回复、菜单管理、素材管理、用户管理、消息群发等基础功能外，还有二维码推广、营销活动、微网站、会员卡、优惠券等。

> coder-wechat-app 

微信小程序后台

## 环境搭建

#### 开发工具:
- MySql: 数据库
- jetty: 开发服务器
- Tomcat: 应用服务器
- SVN|Git: 版本管理
- Nginx: 反向代理服务器
- Varnish: HTTP加速器
- IntelliJ IDEA: 开发IDE
- PowerDesigner: 建模工具
- Navicat for MySQL: 数据库客户端

#### 开发环境：
- Jdk7+
- Mysql5.5+
- Redis
- Zookeeper
- ActiveMQ
- Dubbo-admin
- Dubbo-monitor

### 工具安装

环境搭建和系统部署文档

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
- dubbo-admin-2.5.3 [http://download.csdn.net/detail/shucoder5201314/9733652](http://download.csdn.net/detail/shucoder5201314/9733652 "dubbo-admin-2.5.3")
- dubbo-admin-2.5.4-SNAPSHOT-jdk8 [http://download.csdn.net/detail/shucoder5201314/9733657](http://download.csdn.net/detail/shucoder5201314/9733657 "dubbo-admin-2.5.4-SNAPSHOT-jdk8")

## 开发指南:

- 1、本机安装Jdk7、Mysql、Redis、Zookeeper、ActiveMQ并**启动相关服务**，使用默认配置默认端口即可
- 2、克隆源代码到本地并打开，**推荐使用IntelliJ IDEA**，本地编译并安装到本地maven仓库

### 修改本地Host

- 127.0.0.1	ui.coder.cn
- 127.0.0.1	upms.coder.cn
- 127.0.0.1	cms.coder.cn
- 127.0.0.1	pay.coder.cn
- 127.0.0.1	ucenter.coder.cn
- 127.0.0.1	wechat.coder.cn
- 127.0.0.1	api.coder.cn
- 127.0.0.1	oss.coder.cn
- 127.0.0.1 config.coder.cn

- 127.0.0.1	zkserver
- 127.0.0.1	rdserver
- 127.0.0.1	dbserver
- 127.0.0.1	mqserver

### 编译流程

maven编译安装coder/pom.xml文件即可

### 启动顺序（后台）

> 准备工作

- 新建coder数据库，导入project-datamodel文件夹下的coder.sql

- 修改各dao模块和rpc-service模块的redis.properties、jdbc.properties、generator.properties数据库连接等配置信息，其中master.redis.password、master.jdbc.password、slave.jdbc.password、generator.jdbc.password密码值使用了AES加密，请使用com.coder.common.util.AESUtil工具类修改这些值

- 启动Zookeeper、Redis、ActiveMQ、Nginx（配置文件参考project-tools/nginx下的*.conf文件）

> **coder-upms**

- 首先启动 coder-upms-rpc-service(直接运行src目录下的coderUpmsRpcServiceApplication#main方法启动) => coder-upms-server(jetty)，然后按需启动对应子系统xxx的coder-xxx-rpc-service(main方法) => coder-xxx-webapp(jetty)

![启动演示](project-bootstrap/start.png)

- 访问 [http://upms.coder.cn:1111/](http://upms.coder.cn:1111/ "统一后台地址")，子系统菜单已经配置到coder-upms权限中，不用直接访问子系统，默认帐号密码：admin/123456

- 登录成功后，可在右上角切换已注册系统访问

> **coder-cms**

- coder-cms-admin：启动ActiveMQ-启动 => 启动coder-rpc-service => 启动coder-cms-admin

- coder-cms-web：启动nginx代理coder-ui静态资源，配置文件可参考 [nginx.conf](http://git.oschina.net/shucoder/coder/attach_files)

> **coder-oss**

- 首先启动coder-oss-web服务

- 开发阶段，如果coder-oss-web没有公网域名，推荐使用`ngrok`内网穿透工具，为开发环境提供公网域名，实现上传回调

- 启动nginx代理coder-ui静态资源


### 开发

- 创建数据表（建议使用PowerDesigner）

- 直接运行对应项目dao模块中的generator.main()，可自动生成单表的CRUD功能和对应的model、example、mapper、service代码

    - 生成的model和example均已实现Serializable接口，支持分布式

    - 已包含抽象类BaseServiceImpl，只需要继承抽象类并传入泛型参数，即可默认实现mapper接口所有方法，特殊需求直接扩展即可
    
    - BaseServiceImpl默认已实现四种根据条件分页接口
     
        - selectByExampleWithBLOBsForStartPage()
        
        - selectByExampleForStartPage()
        
        - selectByExampleWithBLOBsForOffsetPage()
        
        - selectByExampleForOffsetPage()

    - BaseServiceImpl方法根据读写操作自动切换主从数据源，继承的扩展接口，可手动通过`DynamicDataSource.setDataSource(DataSourceEnum.XXX.getName())`指定数据源

- 启动流程：优先rpc-service服务提供者，再启动其他webapp

- 扩展流程：可扩展和拆分rpc-api和rpc-service模块，可按微服务拆分或场景拆分

### 框架规范约定

约定优于配置(convention over configuration)，此框架约定了很多编程规范，下面一一列举：

```

- service类，需要在叫名`service`的包下，并以`Service`结尾，如`CmsArticleServiceImpl`

- controller类，需要在以`controller`结尾的包下，类名以Controller结尾，如`CmsArticleController.java`，并继承`BaseController`

- spring task类，需要在叫名`task`的包下，并以`Task`结尾，如`TestTask.java`

- mapper.xml，需要在名叫`mapper`的包下，并以`Mapper.xml`结尾，如`CmsArticleMapper.xml`

- mapper接口，需要在名叫`mapper`的包下，并以`Mapper`结尾，如`CmsArticleMapper.java`

- model实体类，需要在名叫`model`的包下，命名规则为数据表转驼峰规则，如`CmsArticle.java`

- spring配置文件，命名规则为`applicationContext-*.xml`

- 类名：首字母大写驼峰规则；方法名：首字母小写驼峰规则；常量：全大写；变量：首字母小写驼峰规则，尽量非缩写

- springmvc配置加到对应模块的`springMVC-servlet.xml`文件里

- 配置文件放到`src/main/resources`目录下

- 静态资源文件放到`src/main/webapp/resources`目录下

- jsp文件，需要在`/WEB-INF/jsp`目录下

- `RequestMapping`和返回物理试图路径的url尽量写全路径，如：`@RequestMapping("/manage")`、`return "/manage/index"`

- `RequestMapping`指定method

- 模块命名为`项目`-`子项目`-`业务`，如`coder-cms-admin`

- 数据表命名为：`子系统`_`表`，如`cms_article`

```

### 数据模型
![数据库模型](project-datamodel/coder.png)

### 拓扑图
![拓扑图](project-bootstrap/distributedSystem.png)

### 开发模块
![开发模块](project-bootstrap/progress.png)

## 附件


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)