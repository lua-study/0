#概述
1.	本工程是[archer-framework](http://git.oschina.net/ArcherGroup/archer-framework)作为服务端对外提供API的示例，也可以看作是[archer-framework](http://git.oschina.net/ArcherGroup/archer-framework)的一个Boilerplate 。
2.	包含最基本的用户角色权限管理逻辑。
3.  你可以在[archer-application-manager](http://git.oschina.net/ArcherGroup/archer-application-manager)中看到该工程接口对应的后台管理系统界面

# 相关项目
| 名称           | 说明            |
| ------------- |-------------|
| [archer-framework](http://git.oschina.net/ArcherGroup/archer-framework)        | `archer-framework`是一个旨在构建RESful风格WEB服务的轻量级框架        |
| [archer-application-manager](http://git.oschina.net/ArcherGroup/archer-application-manager)        | 使用`archer-framework`做的PC WEB端工程演示，只做界面展现。使用`archer-application-core`提供的API       |


# 如何启动
1.	本工程依赖于`archer-framework`,所以请先install `archer-framework`
2.	`resources/application.development.properties`有关于数据库连接的信息，据此创建数据库`core_dev`
3.	使用`sql/main-create-all.sql`脚本创建表结构
4.	使用`sql/init.sql`脚本导入初始化数据  **（注意：user表数据的password字段采用的是数据库默认的AES加密，目前的加密key是`#archer-application-core`，强烈建议用户修改后再执行init.sql脚本）**
5.	如果你修改了`sql/init.sql`脚本中的AES加密key，那么修改`resources/applicationContext.xml` 中ebean配置`serverConfig`bean的`encryptKeyManager`属性
6.	运行`test/DevelopmentStarter.java`启动整个工程。
7.	enjoy :)

# 接下来
1.	运行`test/`目录下的api测试用例瞅瞅看
2.	也可以代码规范[点击此处查看代码规范](/STYLE.md)
3.	去[archer-application-manager](http://git.oschina.net/ArcherGroup/archer-application-manager)工程看看本工程提供的接口是如何为后台管理系统服务的

#	常见FAQ
> 我跑了接口的测试用例，但是几乎每一个接口返回的`resultMsg`告诉我用户尚未登录，我要如何登录？
> > 运行`StaffApiTest`中的`login`方法即可登录，该方法模拟了后台用户的登录操作，同时会将`token`信息缓存起来，之后再调用其他接口时会自动带上`token`信息就不需要登录了

>我在使用中发现了bug，我要如何报告这个bug？
>> 你可以在git上提交issue，说明问题的现象，错误日志等，我们会在第一时间予以排查和修复。





 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)