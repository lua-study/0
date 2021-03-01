SpringOA简介
========

基于SpringMVC+Shiro+Flowable的简单OA，可以快速入门Flowable学习用。
此版本前台使用的是Bootstrap

框架简介
--------
框架以Spring Framework为核心、Spring MVC作为模型视图控制器、Shiro作为权限框架、Hibernate JPA作为数据库操作层。 
本项目也可以为学习SpringMVC的同学提供帮助。 
本项目以查询待办任务、查待受理任务、查看运行中的流程以及流程控制中的一些问题为基础,入门Flowable。  
实现了流程的签收、委派、转办、跟踪、撤销、跳转（向前和回退）至指定活动节点等功能。 
可以通过后台管理，动态部署流程、动态设定用户任务的处理人（运行中的流程也可以调整处理人） 
Shiro实现登录认证和权限控制，结合Ehcache缓存权限列表，毕竟权限表并不是总在变化。
用户在线列表，可以强制踢出。Shiro的密码的加密解密，并发登陆、会话管理等功能。

框架版本
--------
 
 Flowable 6.3.1 
 Spring-4.3.10.RELEASE 
 Shiro-all-1.2.3 

 Validation-api-1.1.0.GA 
 

数据库
-------
 
 目前只支持MySql,建议MySql 5.5及以上 
 


后续功能
--------
1.加入安全框架Shiro. ---已实现 
2.加入缓存 ehcache.  ---已实现 
3.前端页面 EasyUI.   ---已实现 

系统功能不断完善中,欢迎同学Fork并Pull requests.

系统页面
--------
 
快速启动
--------
test:me.server.QuickStartByTomcat  (需要下载tomcat embed，将jar加入classpath)
   
用户账户
--------
admin/123456

mongodb:
db.createUser(
     {
       user:"root",
       pwd:"123456",
       roles:[{role:"root",db:"admin"}]
     }
  )

Activiti User
--------------
引擎内部用户也可以绕开shiro单独登录，访问user/login


Change logs
-------------
升级到Flowable 6.3.1
流程设计移出项目，使用flowable-modeler.
流程管理使用flowable-admin.


页面说明
-------------
模板文件放在web-inf/views下。

error 存放错误处理页面。 和WebRoot下error的区别是这个错误页面是在spring mvc业务应用内手动生成，而WebRoot/error的由tomcat生成。

default 存放系统功能的模板，采用了easy-ui,bootstrap,通过修改在配置文件设置theme_path为其他值。 

demo 存放工作流演示页面，使用了jquery-ui。 包含以下4个演示应用：

form 存放了工作流的表单系统模板，有两种表单： 
	1. 动态表单：通过工作流定义表单（又分为两种定义模式：表单引擎模式，表单属性模式），在浏览器生成。
	2. 表单文件：表单页面存在服务端，通过ajax调用，获取。

oa 工作流下的demo应用，使用了bootstrap或者jquery-ui。 

management 工作流引擎管理页面，单独使用了bootstrap。 

bpmn 工作流辅佐功能。

login.jsp 是一个特殊的login页面，他使用工作流内部的用户系统，不需要shiro来控制。



superdiamond 项目配置管理页面，由sitemesh管理页面。mesh主页面在default/layout/ 使用了bootstrap


CSS说明
-------
主要包含两大css文件，两个不能同时包含

main.css
主框架和框架内页面的css，和bootstrap结合。 主要用在views/default下面的页面

base.css和style.css
基本页面的css，和bootstrap没有关系，但和jquery-ui结合，主要用在deme页面








 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)