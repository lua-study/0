#RunJS

RunJS 是一个在线的 HTML、Javascript、CSS 等 web 前端代码的编辑分享平台，拥有实时预览、高亮显示、代码格式化等功能，我们提供 OSChina、微博、qq、github、google、yahoo、hotmail这七种登录方式，你只需要有七种任意一个帐号就可以点击右上角的登录按钮来立即体验RunJS。

 

如何在本地运行 RunJS

 1.下载项目源码：git clone http://git.oschina.net/oschina/RunJS.git  
 2.创建空数据库，并使用 RunJS/RunJS/docs/runjs.sql 脚本建表，假设数据库名为 runjs  
 3.修改数据库连接配置 RunJS/RunJS/src/jdbc.properties 的 jdbc.jdbcUrl,jdbc.user,jdbc.password 为你数据库的信息  
 4.打开 build.sh (Windows 下是 build.bat) 将 JAVA_HOME 变量指向 JDK 安装的路径  
 5.非 Windows 系统需要给 build.sh 设置可执行权限 chmod +x build.sh  
 6.执行 build.sh(bat) 进行项目编译  
 7.使用你习惯的应用服务器，如 Tomcat 创建新应用指向 RunJS/RunJS/webapp 。如    
 8.打开浏览器访问即可，目前 oauth 登陆配置只能使用开源中国的账号进行登录

更多介绍请看  https://runjs.cn/help 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)