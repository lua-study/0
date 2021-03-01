JeeWeb敏捷开发平台
===============
* 	QQ交流群： 570062301（满）、522959928
* 	官方网站： [https://www.jeeweb.cn](https://www.jeeweb.cn)
* 	文档地址： [https://doc.jeeweb.cn](https://doc.jeeweb.cn)
* 	项目演示： [https://demo.jeeweb.cn](https://demo.jeeweb.cn)
* 	前后端分离版本项目演示： [http://vuedemo.jeeweb.cn](http://vuedemo.jeeweb.cn)
*   分离开发前端项目地址：[https://gitee.com/dataact/jeeweb-vue-admin](https://gitee.com/dataact/jeeweb-vue-admin)

简介
-----------------------------------
JeeWeb是一款基于SpringBoot 2+Spring+Mybatis+Hibernate的敏捷开发系统；它是一款具有代码生成功能的智能快速开发平台；是以Spring Framework为核心容器，Spring MVC为模型视图控制器，Hibernate为数据访问层， Apache Shiro为权限授权层，Ehcahe对常用数据进行缓存，Disruptor作为并发框架，Bootstrap作为前端框架的优秀 **开源** 系统。

JeeWeb是一款 **全开源开发平台** ，特别 **代码生成器模块也采用开源模式** ，各位开发者可以根据自己的需要改造出更加适合自己的代码生成器，不管是做项目、学习、接私活它都将是你的最佳拍档；

JeeWeb主要定位于企业快速开发平台建设，已内置很多优秀的基础功能和高效的 **代码生成** 工具，包括：系统权限组件、数据权限组件、数据字典组件、核心工具组件、视图操作组件、代码生成、 **UI模版标签** 库等。前端界面风格采用了结构简单、性能优良、页面美观大气的Twitter Bootstrap页面展示框架。采用分层设计、提交数据安全编码、密码加密、访问验证、数据权限验证。使用Maven做项目管理，提高项目的易开发性、扩展性。

目前功能模块代码生成器、权限框架、数据字典、数据缓存、并发框架、数据监控、计划任务、多数据源管理、附件管理、类似mybatis动态SQL、UI模板标签、短信发送、邮件发送、统计功能等功能。

JeeWeb的开发方式采用（ **代码生成器快速设计生成代码->手工完善逻辑->丰富模板标签快速前端开发** ），可以快速协助java开发人员解决60%的重复工作，让开发人员更多关注业务逻辑的实现，框架使用前端模板标签，解放JAVA开发人员的开发压力，提高开发效率，为企业节省项目研发成本，减少开发周期。

后台框架演示（支持两种前端样式自由切换）
-----------------------------------

 
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
 

论坛演示
-----------------------------------

 
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
 

前后端分离演示
-----------------------------------

 
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
     
           
           
     
 

JeeWeb 技术特点
-----------------------------------
JeeWeb使用目前流程的WEB开发架构技术，如 **SpringBoot,Mybatis, Hibernate,Apache Shiro, Disruptor , ehcache, Jquery ,BootStrap** 等等，支持多种数据库MySQL, Oracle, sqlserver等。  **分层设计：使用分层设计，分为dao，service，Controller，view层，层次清楚，低耦合，高内聚。**  

安全考虑：严格遵循了web安全的规范，前后台双重验证，参数编码传输，密码md5加密存储，shiro权限验证，从根本上避免了SQL注入，XSS攻击，CSRF攻击等常见的web攻击手段。

JeeWeb 功能特点
-----------------------------------
* 	SpringBoot+Spring+Mybatis+Hibernate+Shiro+ Ehcache+Disruptor+Jquery + Boostrap + Ztree等基础前后端架构架构
* 	采用面向声明的开发模式， 基于泛型编写极少代码即可实现复杂的数据展示、数据编辑、表单处理等功能，在不使用代码生成器的情况下，也只需要很少的代码就能实现基础的CURD操作，再配合在线开发与代码生成器的使用，更加加快了开发的进度，将J2EE的开发效率成本提高，可以将代码减少60%以上。
* 	在线开发(通过在线配置实现一个表模型的增删改查功能，无需一行代码，支持用户自定义表单布局) 
* 	代码生成器，支持多种数据模型,根据表生成对应的Entity,Service,Dao,Controller,JSP等,增删改查功能生成直接使用
* 	UI标签开发库，针对前端UI进行标准封装表，页面统一采用UI标签实现功能：数据datagrid,treegrid,FileInput,Editor,GridSelect等，实现JSP页面零JS，开发维护简洁高效
* 	查询过滤器：只需前端配置，后台动态拼SQL追加查询条件；支持多种匹配方式（全匹配/模糊查询/包含查询/不匹配查询）
* 	移动平台支持，对Bootstrap(兼容Html5)进行标准封装
* 	灵活的权限控制，可控制到页面或按钮，满足绝大部分的权限需求,优化权限注解方便权限配置
* 	完善的XSS防范及脚本过滤，彻底杜绝XSS攻击
* 	支持分布式部署，session存储在redis中
* 	友好的代码结构及注释，便于阅读及二次开发
* 	引入quartz定时任务，可动态完成任务的添加、修改、删除、暂停、恢复及日志查看等功能
* 	引入swagger文档支持，方便编写API接口文档
* 	国际化（支持多语言，国际化的封装为多语言做了便捷支持）
*   多数据源（在线配置数据源，数据源工作类封装）
* 	数据权限：整合Shiro权限
*   计划任务控制（在线配置计划任务、方便计划任务的时间调整规划）
*   邮件发送（配置邮件模版、邮件帐号的在线配置、邮件异步发送、邮件发送日志功能统计）
*   短信发送（配置短信模版、短信帐号的在线配置、短信异步发送、短信发送日志功能统计、支持短信发送平台动态切换）
*   多种首页风格切换,支持自定义首页风格。（Inspinia风格|ACE风格）
*   数据统计报表：丰富的报表统计功能
* 	支持多种浏览器: Google, 火狐, IE,360 等
* 	支持数据库: Mysql,Oracle10g,SqlServer等
* 	基础权限: 用户，角色，菜单权限
* 	Web容器测试通过的有Jetty和Tomcat,Weblogic
* 	要求JDK1.8+

技术选型
===============

1、后端

* 核心框架：Spring boot2.0、Spring Framework
* 安全框架：Apache Shiro
* 服务端验证：Hibernate Validator
* 模板标签：Beetl
* 任务调度：Quartz
* 持久层框架：Hibernate 
* 数据库连接池：Alibaba Druid
* 缓存框架：Redis、Ehcache
* 并发框架：Disruptor
* 日志管理：SLF4J、Log4j
* 工具类：Apache Commons、Jackson、Xstream、
 
2、前端

* JS框架：jQuery。
* CSS框架：Twitter Bootstrap
* 客户端验证：Validform。
* 富文本在线编辑：markdown、simditor、Summernote、CodeMirror自由切换
* 文件上传工具:Bootstrap fileinput
* 数据表格：jqGrid
* 对话框：layer
* 树结构控件：jQuery zTree
* 日期控件： datepicker
* 代码高亮： syntaxhighlighter

简单使用说明
-----------------------------------
* 导入jeeweb目录下的，具体模块sql/mysql.sql文件到mysql数据库
* 导入项目到Idea,(项目目前使用分模块开发，我们建议是用IDEA开发).
* 修改数据库配置文件application.yml中的账号密码.
* 启动项目,管理员账号admin/密码123456

平台目录结构说明
-----------------------------------
```
jeeweb
├─jeeweb-common     公共模块
│    ├─jeeweb-common-base  公用基础模块
│    │ 
│    ├─jeeweb-common-email  邮件基础模块
│    │ 
│    ├─jeeweb-common-hibernatemvc  hibernate公用模块
│    │ 
│    ├─jeeweb-common-mybatismvc  mybatis公用模块
│    │ 
│    ├─jeeweb-common-oss  数据存储公用模块
│    │ 
│    ├─jeeweb-common-quartz  quartz公用模块
│    │ 
│    ├─jeeweb-common-query  查询封装模块
│    │ 
│    ├─jeeweb-common-security  安全公用模块
│    │ 
│    ├─jeeweb-common-sms  短信公用模块
│    │ 
│    └─jeeweb-common-utils 公用工具模块
│ 
├─jeeweb-ui     UI模块
│    ├─jeeweb-beetl-tag  基于beetl的类似spring form的模板标签
│    │ 
│    ├─jeeweb-ui-static  公用静态资源模块
│    │ 
│    └─jeeweb-ui-tag  基于静态资源模块的标签
│       
├─jeeweb-web  业务模块
│    ├─jeeweb-admin  后台案例模块
│    │ 
│    ├─jeeweb-bbs Jeeweb官方论坛代码模块
│    │ 
│    ├─jeeweb-vue 前后端分离后端模块
│    │ 
│    └─jeeweb-generator  代码生成器模块
│
```

代码示例
-----------------------------------
###  [1].GRID列表
```
 
     
     
     
     
     
     
     
     
     

     
 
```
![JSP列表图片](https://git.oschina.net/uploads/images/2017/0630/205011_87420e1e_1394985.png "JSP列表图片")

###  [2].TREEGRID列表
```
 
	 
	 
	 
	 
	 

	 
	 
	 
	 
	 
 
```
![TREEGRID](https://git.oschina.net/uploads/images/2017/0630/205353_af457e21_1394985.png "TREEGRID")
###  [3].表单代码
```
 
 
   
   
     
     
       
         用户名:  
       ${data.username} 
       
         
           * 姓名:  
       
         
          
       
     
     
       
         
           * 邮箱:  
       
         
          
       
       
         
           * 联系电话:  
       
         
          
       
     
     
       
         
           * 用户角色:  
       
          
     
     
       
         组织机构:  
       
          
     
     
   
 
 
```
![表单](https://git.oschina.net/uploads/images/2017/0630/205612_2d09fd89_1394985.png "表单")


升级说明
-----------------------------------
* 更改项目为分模块依赖开发。
* 剥离代码生成器，代码生成器作为单独项目启动、并升级了一些功能。
* 更改前端模板引擎为Beetl。使前段渲染更快、更友好的前端设计体验
* 项目更改为Spring boot2.0，降低开发门槛。
* 引入swagger用于接口管理。
* 引入redis SESSION管理，方便集群部署。
* 升级日志功能、分离为登陆日志以及操作日志。
* 引入quartz定时任务，可动态完成任务的添加、修改、删除、暂停、恢复及日志查看等功能
* 更好的开发体验。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)