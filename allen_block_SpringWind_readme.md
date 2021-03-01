
![spring-wind](http://git.oschina.net/uploads/images/2016/0410/215321_0c4657f5_12260.png "SSM架构核心库")

SSM 架构后台管理系统

> 技术讨论 QQ 群 235079513

[项目核心库 spring-wind 点击查看](http://git.oschina.net/juapk/spring-wind)

------------------------------------------------
《春风》

春风如贵客，一到便繁华。

来扫千山雪，归留万国花。

------------------------------------------------



# SpringWind 说明


> 简单介绍

```
该项目为 SSM 核心库 spring-wind 演示项目

http://git.oschina.net/juapk/spring-wind

已集成组件：

1、mybatis-plus （mybatis 自动 crud 功能）
2、kisso （单点授权、权限管理、验证码、api 服务、oauth2认证）
3、mail（收发邮件）
4、veloctiy （继承模板支持、环境控制）
5、slf4j-api（日志 logback 管理）
7、fastjson （json 处理）
8、quartz (定时任务)
9、cos （优化、支持头文件字节检查、图片剪切、视频处理、文档处理）
10、Sigar （系统信息收集）
11、pingyin4j（中文转拼音库 ）
12、表单重复提交aop 辅助工具类 等..

```


> 运行项目配置说明

```
1、根据 /SpringWind/src/main/resources/properties/jdbc.properties 配置数据库

2、导入数据库 /SpringWind/src/test/resources/springwind.sql

3、导入Quartz 相关表 /SpringWind/src/test/resources/quartz_mysql_innodb.sql

4、操作系统 host 添加一行设置 127.0.0.1 demo.baomidou.com

5、访问：http://demo.baomidou.com:8080 登录账户默认：  admin 管理员，密码 123 ，普通会员 test 密码  123


```


> 测试权限

```
1、test 账户登录系统

2、访问地址：http://demo.baomidou.com:8080/role/list.html
```


> 404 异常

```
1、操作系统 host 需要与 /SpringWind/src/main/resources/properties/sso.properties 配置一致（配置好 host 重启浏览器）

2、注意：访问项目名称问题 ，未配置无项目名称访问携带项目名称访问。
```

更多补充中。。。。。


演示界面
=======

![登录效果](http://git.oschina.net/uploads/images/2016/0415/233200_ee76b11a_12260.png "登录效果")

![后台发送邮件测试](http://git.oschina.net/uploads/images/2016/0417/195044_19dcb437_12260.png "后台发送邮件测试")

![后台界面效果](http://git.oschina.net/uploads/images/2016/0415/233226_7713bf12_12260.png "后台界面效果")

![锁定效果](http://git.oschina.net/uploads/images/2016/0415/233245_dc44f2f9_12260.png "锁定效果")


Features
=======

1、欢迎提出更好的意见，帮助完善 Spring-Wind

Copyright
====================
Apache License, Version 2.0

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)