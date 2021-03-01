## 项目简介

spring-boot-doc是一款针对IT团队开发的简单好用的文档管理系统。

spring-boot-doc的前身是[MinDoc](https://git.oschina.net/longfei6671/godoc)，MinDoc 的前身是 SmartWiki 文档系统。SmartWiki 是基于 PHP 框架 laravel 开发的一款文档管理系统。因 PHP 的部署对普通用户来说太复杂，所以原作者改用 Golang 开发。然而对于一个JAVA开发者来说，对于GO语言，出现问题自身又不能解决，所以使用spring-boot重写了MinDoc，可以方便JAVA用户部署和使用，目前只完善了部分功能，持续更新中。

## 项目结构
 
```
     
├─src
│  ├─main
│  │  ├─java
│  │  │  └─com
│  │  │      └─itstyle
│  │  │          └─doc
│  │  │              │  Application.java --启动类
│  │  │              │  
│  │  │              ├─common  --公用包
│  │  │              │  ├─constans
│  │  │              │  │      
│  │  │              │  ├─interceptor
│  │  │              │  │      
│  │  │              │  └─utils
│  │  │              │          
│  │  │              ├─model  --实体类
│  │  │              │      
│  │  │              ├─repository --数据访问层
│  │  │              │      
│  │  │              └─web  -- 控制访问层
│  │  │                      
│  │  ├─resources  -- 系统配置 
│  │  │  │  application-dev.properties
│  │  │  │  application-prod.properties
│  │  │  │  application-test.properties
│  │  │  │  application.yml
│  │  │  │  kaptcha.xml
│  │  │  │  logback-spring.xml
│  │  │  │  
│  │  │  ├─sql -- 数据库文件
│  │  │  │      
│  │  │  ├─static -- 前端插件
│  │  │  │          
│  │  │  ├─templates -- 页面访问模版
│  │  │  │          
│  │  │  └─uploads -- 上传目录
│  │  │              
│  │  └─webapp
│  │      │  index.jsp
│  │      │  
│  │      └─WEB-INF
│  │              web.xml
│  │                                       

```                             



## 安装与使用

作为一个AJAV开发者，首先你的电脑必备JDK，其次你要有个开发工具(Eclipse或者IDEA)，最后你要熟悉spring-boot这个简单易用的快速开发框架。

下载项目以后，自行配置数据库，导致sql中的doc.sql，会自动创建表，同时初始化一个超级管理员用户：admin 密码：111111，请登录后重新设置密码。

## 使用的技术

- spring-boot 1.52
- spring-data-jpa  1.11.1
- thymeleaf 2.1.5 
- kaptcha 2.3.2
- mysql 5.6
- editor.md
- bootstrap 3.2
- vuejs 2.2.6
- jquery 库
- layer 弹出层框架
- webuploader 文件上传框架
- Nprogress 库
- jstree 树状结构库
- font awesome 字体库
- cropper 图片剪裁库
- layer 弹出层框架
- highlight 代码高亮库
- to-markdown HTML转Markdown库
- wangEditor 富文本编辑器

## 主要功能

- 项目管理，可以对项目进行编辑更改，成员添加等。
- 文档管理，添加和删除文档等。
- 评论管理，可以管理文档评论和自己发布的评论。
- 用户管理，添加和禁用用户，个人资料更改等。
- 用户权限管理 ， 实现用户角色的变更。
- 项目加密，可以设置项目公开状态，私有项目需要通过Token访问。
- 站点配置，可开启匿名访问、验证码等。
- 不定期 push 新功能


## 项目截图
![输入图片说明](https://git.oschina.net/uploads/images/2017/0909/190321_c8688308_87650.png "1.png")

![输入图片说明](https://git.oschina.net/uploads/images/2017/0909/190328_79701eb8_87650.png "2.png")

![输入图片说明](https://git.oschina.net/uploads/images/2017/0909/191029_b34cb360_87650.png "4.png")

![输入图片说明](https://git.oschina.net/uploads/images/2017/0909/191038_962827fa_87650.png "5.png")

![输入图片说明](https://git.oschina.net/uploads/images/2017/0909/191044_a1beced1_87650.png "6.png")

![输入图片说明](https://git.oschina.net/uploads/images/2017/0910/113613_7facf3e2_87650.png "7.png")

![输入图片说明](https://git.oschina.net/uploads/images/2017/0910/113559_f73260e8_87650.png "8.png")

![输入图片说明](https://git.oschina.net/uploads/images/2017/0910/113606_78b477e3_87650.png "9.png")

![输入图片说明](https://git.oschina.net/uploads/images/2017/0911/111538_ab5c7454_87650.png "10.png")

![输入图片说明](https://git.oschina.net/uploads/images/2017/0923/174242_a0ff7bf1_87650.png "1234.png")

## 友情提示



- spring-boot-doc作为一个新手入门级别的项目，前提必须熟知spring-boot、thymeleaf、Jpa、vuejs等相关技术，开发过程中并不能保证所有功能的正常使用。

- 项目中使用到了lombok，没有安装的同学可能会报错，[lombok使用技巧](https://blog.52itstyle.com/archives/1557/) 如果不想使用，自行去掉注释，生成get set方法和构造方法。

- 如果想使用MinDoc，请移步安装教程：[安利一款接口文档在线管理系统-MinDoc](https://blog.52itstyle.com/archives/1557/)




作者： 小柒2012

欢迎关注： https://blog.52itstyle.com


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)