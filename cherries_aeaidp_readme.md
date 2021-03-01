**AEAI DP开发平台介绍**
-------------
AEAI DP开发平台专门用于开发MIS类的Java Web应用，也称Miscdp（Misc Develope Platform）综合应用开发平台。 AEAI DP开发平台在数通畅联软件产品家族中也作为扩展开发的支撑工具，比如：为AEAI Portal门户平台扩展开发Portlet组件、Web Service和Http Service；为AEAI BPM流程集成平台扩展开发业务流程表单及功能等。     
 
![enter image description here](http://www.agileai.com/HotServer/reponsitory/images/oschina/dp.png)
  
AEAI DP包括三部分，一部分是一站式的Java Web框架Hotweb；另一部分是基于Eclipse插件的扩展开发设计器Miscdp Studio；第三部分是开发调试服务环境HotServer，基于Tomcat 7.0.X扩展。基于AEAI DP开发出的Web项目符合Java Web相关规范，可以运行于主流Java Servlet容器之上，包括Weblogic AS、Webshpere AS、JBOSS AS、Apusic AS、Tomcat、Jetty等。

开发平台设计器Miscdp Studio可以开发三类Web应用，普通的Java Web 应用、集成Web应用和Web服务应用。普通Web应用及Web服务应用基于HotServer来开发调试的，集成Web应用是基于AEAI Portal开发调试。集成Web应用，除了具备普通Web的所有功能模型以外，还可以开发符合jsr168，jsr286等规范的Portlet，同时复用AEAI Portal的统一身份认证、权限体系，跟AEAI Portal门户平台实现无缝集成。
 
![enter image description here](http://www.agileai.com/HotServer/reponsitory/images/oschina/aeaidp.png)
 
采用AEAI DP可以快速（在5分钟内）开发出满足典型需求的可运行Java Web应用功能框架，包括：登录认证、功能菜单管理、群组角色管理、系统用户管理、系统授权管理，系统日志管理、系统编码管理、密码修改等。

**AEAI DP开发平台主要特性：**
-------------
 1. 自带典型功能样例可以快速上手；
 2. 预置丰富的功能模型和相关类库：包括单表操作功能、主从表操作功能、综合查询功能、树形管理功能、树及内容关联管理功能、树及列表选择功能、文件上载功能等；
 3. 基于Eclipse插件Miscdp Studio以向导式、编辑配置模式，收集上述典型功能模型元数据，然后基于代码生成器创建典型业务功能，生成易读规范、即时运行的代码，一般情况，创建一个业务功能不超过10分钟；
 4. AEAI DP开发平台的设计遵循MVC标准，框架代码编写符合规范，支Oracle、SQLServer、Mysql等主流数据库，可以在生成代码基础上扩展来满足复杂的功能需求；
 5.	Hotweb一站式Java Web框架封装几乎所有常见的调用方式及处理机制，预置众多Java Web开发所必须的Web组件，极端的应用模式下，如：one page one application下可以抛开Miscdp studio设计器，直接使用Hotweb框架来开发应用；
 6.	HotServer内置热加载机制，跟Miscdp Studio以手动模式启停应服务器重启，减少重启服务器次数，配合实现远程调试，提高开发效率。同时，支持传统Java Web应用调试模式；
 7.	内置完备的系统管理相关功能，作为应用系统的支撑模块，大大减少业务系统的开发工作量。

欢迎加入数通畅联产品QQ技术群:[299719834](http://shang.qq.com/wpa/qunwpa?idkey=366d7f20977a19335ecbf578959f3fbd607436af9b18fea7bd3e4f9f0710d040)，一起参与讨论。
官方网站：http://www.agileai.com

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)