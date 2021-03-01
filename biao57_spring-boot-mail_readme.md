# spring-boot-mail

邮件发送服务，文本，附件，模板，队列，多线程，定时任务实现多种功能！！！

[SpringBoot开发案例之整合mail发送服务](https://blog.52itstyle.com/archives/1264/)

[SpringBoot开发案例之整合mail队列篇](https://blog.52itstyle.com/archives/1385/)

## 开发环境

JDK1.7、Maven、Eclipse、SpringBoot1.5.2、spring-boot-starter-mail、spring-boot-starter-thymeleaf，spring-boot-starter-freemarker

## 流程图

### 平台架构
![输入图片说明](https://git.oschina.net/uploads/images/2017/0801/190708_991f282a_87650.png "2574887637.png")

### 进程内邮件队列
![邮件队列](https://git.oschina.net/uploads/images/2017/0804/135111_3b197795_87650.png "邮件队列.png")

## 欢迎关注

![输入图片说明](https://git.oschina.net/uploads/images/2017/0802/192404_8b5f9807_87650.jpeg "1801066129 (1).jpg")

## 友情提示
由于工作原因，项目正在完善中，随时更新日志，有疑问请留言或者加群

- JAVA爱好者①:    (满)
- JAVA爱好者②:   
- JAVA爱好者③:   

## 项目结构

![springboot-mail.png](https://blog.52itstyle.com/usr/uploads/2017/07/429638365.png)


- 普通文本发送
- 富文本发送(图片、附件)
- freeMarker模版发送邮件
- thymeleaf模版发送邮件

# 评测生成模版时间对比(1000次循环)


- Thymeleaf用时:2686ms
- Freemarker用时:498ms

对比测试，建议使用Freemarker模版

# 20170721
- 加入DubboX对外提供发送服务
- 加入定时任务统计失败邮件定时重新发送
- 多环境配置文件实现

![输入图片说明](https://blog.52itstyle.com/usr/uploads/58ad45c0b9e21.gif "在这里输入图片标题")

作者： 小柒2012

欢迎关注： https://blog.52itstyle.com

## 测试


- 修改 application-dev.properties 中自己的邮件配置 同时配置dubbo.registry.address地址
- 执行 com.itstyle.mail.test.SpringbootMailApplication main 方法




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)