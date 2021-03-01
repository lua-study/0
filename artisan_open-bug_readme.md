ppm-bug 缺陷管理系统
=======

项目主页： http://www.ppm123.cn

在线演示： http://121.199.44.145:9000/open-bug/  (用户名：ross，密码：1，Chrome浏览器)

免费下载： http://ppm123.cn/pages/bug/detail.php

简介：

PPM缺陷管理系统是在见到当前免费的缺陷管理工具功能和界面都非常粗糙的情况下，旨在打造一个功能全面，界面清新的开源缺陷管理系统！

1. 工作面板 -- 快捷处理我接收的项目、缺陷，展示统计图和系统动态

2. 缺陷管理 -- 行业内领先缺陷管理流程，提高缺陷处理，管理效率

3. 项目状态 -- 按项目管理缺陷，直观统计项目下人员与缺陷的各种状态

4. 用户管理 -- 按职位管理用户，项目经理，研发工程师，测试工程师

5. 缺陷跟踪 -- 记录缺陷操作记录，流程图高亮显示操作路径与当前所处状态

6. 视图机制 -- 用户可在缺陷列表和工作面板中定制想看到的缺陷列表

7. 定制页面 -- 用户可自定义缺陷操作与查看页面的表单字段


版本：

PPM Bug v1.3 是PPM缺陷管理系统于2013年7月14号发布的第四个版本。

PPM Bug v1.3 特性：

1. 缺陷解决经验分享

2. 自定义表单，用户可定制缺陷操作与查看页面的表单字段
 
技术体系
=======

前端：

主 -- JQuery + Bootstrap + JQueryUI(bootstrap theme) + iCheck + uploadify + FancyBox + HignCharts + SVG

附 -- JQuery自定义插件 + 下拉框插件

后端：

主 -- SpringMVC + Sitemesh + Hibernate(注解) + Spring(Ioc) + Spring Security + JSP2 TagDir + POI + log4j

附 -- 反射 + 自定义表单

源码使用
=======

查看PPM Bug的源码并运行起来十分的简单，并且源码提供了非常详细的注释

1. 下载zip包，解压

2. Eclipse引入已存在项目，选择刚才解压的文件夹

3. PPM Bug采用内存数据库derby，所以只需将解压的文件夹下的db-bug文件夹放到tomcat安装目录的bin文件夹下即可，无需安装数据库

4. 打开WebRoot/WEB-INF/applicationContext.xml，将数据源中的jdbc:derby:D:/derby/bin/db-bug;改为jdbc:derby:db-bug;

5. 部署，运行，默认用户名admin，密码1


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)