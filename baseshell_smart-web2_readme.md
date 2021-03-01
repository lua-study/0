功能介绍
=========
---------
**smart-web2** 是一套相对简单的OA系统；包含了流程设计器，表单设计器，权限管理等功能；
系统后端基于SpringMVC+Spring+Hibernate框架，前端页面采用JQuery+Bootstrap等主流技术；
流程引擎基于Snaker工作流；表单设计器基于雷劈网WEB表单设计器。
系统主要功能有：
 >1.系统管理
 >>系统管理包含有：基础信息管理、系统权限管理、版本管理、子系统管理。
 >
 >2.流程管理
 >>流程管理包含有：流程设计器、流程实例管理、流程页面模版管理等功能。
 >
 >3.表单管理
 >>表单管理包含有：表单设计器、表管理、表单帮助信息管理等。
 >
 >4.我的办公
 >>我的待办、我的已办;

使用说明
=======
-------
---数据库MySQL5.6以上  
---下载后把data目录下的smart_web2.zip解压；然后解压出来的脚本文件（“smart_web2.sql”）导入到mysql数据库中；注：建库时，字符集编码为：utf8（utf8_general_ci） 
---修改配置文件“jdbc.properties”，改成对应数据库的用户名和密码  
---“sysconfig.properties”系统配置文件；需要修改“root.dir”属性，设置为系统上传文件时用来存放的根目录  
----系统管理员用户名为：admin；密码为：123456  
环境要求
------------
1.jdk要求1.7及以上； 
2.tomcat6或tomcat7；  
3.eclipse版本4.4以上； 
4.浏览器要求：IE8及以上（最理想的是IE10及以上），火狐，chrome等。 

系统截图
=========
---------
 1.首页
![首页](https://git.oschina.net/bcworld/smart-web2/raw/master/screenshot/0001.png)
![修改密码](https://git.oschina.net/bcworld/smart-web2/raw/master/screenshot/0008.png)
  
 2.资源管理  
![资源管理列表](https://git.oschina.net/bcworld/smart-web2/raw/master/screenshot/0002.png)
![添加资源](https://git.oschina.net/bcworld/smart-web2/raw/master/screenshot/0009.png)
 
 3.菜单管理  
![菜单管理列表](https://git.oschina.net/bcworld/smart-web2/raw/master/screenshot/0003.png)
![菜单管理列表](https://git.oschina.net/bcworld/smart-web2/raw/master/screenshot/0010.png)
  
 4.权限管理
![权限管理列表](https://git.oschina.net/bcworld/smart-web2/raw/master/screenshot/0004.png)
  
 5.流程管理
![流程设计器](https://git.oschina.net/bcworld/smart-web2/raw/master/screenshot/0005.png)
![流程实例管理](https://git.oschina.net/bcworld/smart-web2/raw/master/screenshot/0006.png)
  
 6.表单管理
![表单设计器](https://git.oschina.net/bcworld/smart-web2/raw/master/screenshot/0007.png)

[演示地址](http://39.108.2.10:8080)
-------
地址：http://39.108.2.10:8080  
用户名：test1；密码：123456

技术交流
========
--------
QQ群：554013695

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)