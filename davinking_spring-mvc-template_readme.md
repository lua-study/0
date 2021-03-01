#spring-mvc-template
#项目简介

SpringMVC和Hibernate框架搭建的一个模版项目,项目演示一个简单的CRUD功能

项目由Maven管理,JDBC配置部分分为产品模式和开发模式两种配置,避免开发环境和生产环境需要额外修改文件

该项目开发方便,注解和XML两种方式混合,颠覆一般用户对Spring繁多配置的认识

控制层使用一个AbstractBaseController定义了公共的操作方法,所有业务Controller均继承它,统一各模块主功能API

服务层和持久化层抛弃了繁杂的接口+实现的模式,去除了接口部分,并且都继承各自层次结构的抽象类,实现功能的复用和API统一

包括JS部分也使用该方式,统一了各模块的操作,使得业务模块只需要简单的修改该模块自定义部分即可实现整个功能

#项目运行

首先需要下载该项目,然后导入到你的开发工具里

然后你需要创建一个数据库,字符集UTF-8,创建一个空库即可,项目运行成功后会自动创建表

再然后你需要根据你自己的环境修改以下文件

spring-mvc-template\src\main\resources\develop\jdbc.properties -- 开发环境的JDBC配置

spring-mvc-template\src\main\resources\product\jdbc.properties -- 生产环境的JDBC配置

项目使用MAVEN构建和管理,所以你需要使用MAVEN编译该项目mvn compile

如果你只是想简单的部署到容器里运行一下,那么你可以使用命令

mvn -Pproduct package                 -- 按生产环境打包

mvn -Pdevelop package 或者 mvn package  -- 按开发环境打包

然后将spring-mvc-template\target目录下将spring-mvc-template-0.0.1-SNAPSHOT.war拷贝出来放到容器里.为了访问方便,你可以为该文件重命名

现在你应该已经成功启动了,那么只需要按照该地址规则访问即可:http://ip:port/projectName

按照正常情况,你可以用admin和admin来登录,但是该系统并未做登录限制,你可以根据系统已有的任何action随意跳转


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)