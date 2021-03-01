#项目简介
社团集结号(clubassembly)是模仿人人网-社团人的一个java web 项目。旨在做出java实用框架整合的示例性项目。

#[项目WiKi](https://git.oschina.net/hbsdtaoxue/clubassembly/wikis/Home)

#前端技术
jquery, flat-ui, bootstrap, jquery-validation, ajax, matrix 等

#后端技术
spring, spring mvc, hibernate, maven, shiro, sitemesh ,quartz等

#项目展示
项目前台主页：http://ztao.xyz:8080/clubassembly/index
项目后台主页：http://ztao.xyz:8080/clubassembly/manager/login

#示例账号
项目前台:641041018@qq.com,admin
项目后台:641041018@qq.com,admin

#运行方法

1.执行sql脚本，位于src\main\resources\sql\mysql\clubassembly_bak002.sql

2.执行maven构建命令，进行web项目构建

3.maven构建完成之后，将target/clubassembly.war放到tomcat容器下。

4.在tomcat 目录下建立clubassemblyResourdces 文件夹

5.在tomcat/conf/server.xml 文件中的  的上方加入``` ```   可参照config/apache-tomcat-7.0.53  的配置。 5，6两步主要用于将项目运行时上传的图片保存到项目之外，这样在下次部署项目时，图片依然能找到



6.运行tomcat即可。



#Android
在product目录下，有两个apk包，一个是android用户端，一个是android管理端。在两个apk包里，嵌入了前台URL和后面URL， 因为项目前台flat-ui和项目后台matrix 都是基于bootstrap的，所以在android设备上，显示效果也非常好。

#test






 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)