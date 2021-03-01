# spring-boot-apollo-sample
Demo project for Spring Boot Apollo

Spring Boot整合携程Apollo配置中心
###代码说明：
>SpringBoot启动vm参数添加：
-Ddev_meta=http://18.16.200.107:8080 -Denv=DEV
其中-Ddev-meta连接的是配置管理eureka的url地址
-Denv配置的是具体的环境

>也可以在C:\opt\settings\server.properties中添加环境配置：
env=DEV
这个配置文件里面只能配置环境，不能配置url

>第一步配置app.id,在META-INF/app.properties里面添加app.id,类型字符串



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)