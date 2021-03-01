# spring-boot-mail

邮件发送服务，文本，附件，模板，队列，多线程，定时任务实现多种功能！！！


Spring-Boot2.0 + Nacos注册中心版：https://gitee.com/52itstyle/spring-boot-mail/tree/spring-boot-mail-nacos

## 欢迎关注

一个有温度的微信公众号，期待与你共同进步，分享美文，分享各种Java学习资源

![输入图片说明](https://images.gitee.com/uploads/images/2018/0809/181043_76e4d5b8_87650.png "1234.png")

## 友情提示

由于工作原因，项目正在完善中，随时更新日志，有疑问请留言或者加群

- JAVA爱好者:   

## 开发环境

JDK1.8、Maven、Eclipse、SpringBoot 2.1.6、spring-boot-starter-mail、spring-boot-starter-thymeleaf、spring-boot-starter-freemarker、Dubbo、zookeeper-3.5.3、Redis

## 演示图


![输入图片说明](https://gitee.com/uploads/images/2018/0504/085208_6aca748c_87650.png "1.png")


![输入图片说明](https://gitee.com/uploads/images/2018/0504/085238_08e21dda_87650.png "2.png")


![输入图片说明](https://gitee.com/uploads/images/2018/0504/085245_4c151318_87650.png "3.png")

## 启动说明

- 项目中RPC框架使用的是当当维护的DubboX，现在阿里已经处于维护状态中，请自行更新

- 配置Dubbo需要安装注册中心zookeeper: http://www.52itstyle.top/thread-19791-1-1.html

- 如果不想使用Dubbo和安装zookeeper，又想启动看下效果，请注释掉 Application 类中的@ImportResource({"classpath:spring-context-dubbo.xml"})， 同时由于接口扫描注解使用的是Dubbo的 com.alibaba.dubbo.config.annotation.Service; 请自行替换成spring的 org.springframework.stereotype.Service(废弃);

- Sql文件位于src/main/resource/sql下，自行导入即可、里面有一条测试数据

- API: http://localhost:8080/swagger-ui.html、 可以自行测试发送邮件，前提是要修改application-dev.properties中的邮箱配置为自己可用的

- 2018-10-25 原spring-context-dubbo.xml 配置 替换为 dubbo-spring-boot-starter 2.0.0

- 执行 com.itstyle.mail.test.SpringbootMailApplication main 方法



## 流程图

### 平台架构
![输入图片说明](https://git.oschina.net/uploads/images/2017/0801/190708_991f282a_87650.png "2574887637.png")

### 进程内邮件队列
![邮件队列](https://git.oschina.net/uploads/images/2017/0804/135111_3b197795_87650.png "邮件队列.png")

## 项目结构

```
├─src
│  ├─main
│  │  ├─java
│  │  │  └─com
│  │  │      └─itstyle
│  │  │          └─mail
│  │  │              │  Application.java
│  │  │              │  
│  │  │              ├─demo
│  │  │              │      CountDownLatchDemo.java
│  │  │              │      Ticket.java
│  │  │              │      TicketRun.java
│  │  │              │      
│  │  │              ├─model
│  │  │              │      Email.java
│  │  │              │      
│  │  │              ├─queue
│  │  │              │      ConsumeMailQueue.java
│  │  │              │      MailQueue.java
│  │  │              │      
│  │  │              ├─redis
│  │  │              │      Receiver.java
│  │  │              │      RedisConfig.java
│  │  │              │      RedisListener.java
│  │  │              │      
│  │  │              ├─service
│  │  │              │  │  IMailService.java
│  │  │              │  │  
│  │  │              │  └─impl
│  │  │              │          MailServiceImpl.java
│  │  │              │          
│  │  │              ├─task
│  │  │              │      SendMail.java
│  │  │              │      
│  │  │              └─util
│  │  │                      CommonUtil.java
│  │  │                      Constants.java
│  │  │                      MailUtil.java
│  │  │                      
│  │  ├─resources
│  │  │  │  application-dev.properties
│  │  │  │  application-prod.properties
│  │  │  │  application-test.properties
│  │  │  │  application.yml
│  │  │  │  spring-context-dubbo.xml
│  │  │  │  spring-context-task.xml
│  │  │  │  
│  │  │  └─static
│  │  │      ├─file
│  │  │      │      关注科帮网获取更多源码.zip
│  │  │      │      
│  │  │      ├─image
│  │  │      │      springcloud.png
│  │  │      │      
│  │  │      └─template
│  │  │              welcome.flt
│  │  │              welcome.html
│  │  │              
│  │  └─webapp
│  │      │  index.jsp
│  │      │  
│  │      └─WEB-INF
│  │              web.xml
│  │              
│  └─test
│      └─java
│          └─com
│              └─itstyle
│                  └─mail
│                      └─test
│                              SpringbootMailApplication.java
```

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

# 20181024

- 原spring-context-dubbo.xml 配置 替换为 dubbo-spring-boot-starter 2.0.0

# 20190908 
- Dubbo 升级为 Apache 组织
- Dubbo 2.6.2 升级为  Apache Dubbo 2.7.3
- 原 com.alibaba.spring.boot dubbo-spring-boot-starter 2.0.0 升级为  org.apache.dubbo dubbo-spring-boot-starter 2.7.3


## 推荐阅读

[SpringBoot开发案例之整合mail发送服务](https://blog.52itstyle.vip/archives/1264/)

[SpringBoot开发案例之整合mail队列篇](https://blog.52itstyle.vip/archives/1385/)


作者： 小柒2012

欢迎关注： https://blog.52itstyle.vip


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)