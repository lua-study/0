#简介

本项目是SpringBoot 集成Spring Security的Demo，包含了完整的权限验证系统，可根据权限控制页面按钮的显示隐藏。

>技术讨论QQ群：499033245

#技术选型

 - 核心：SpringBoot
 
 - 权限框架：SpringSecurity

 - 持久层：MyBatis + [MyBatis-Plus](http://git.oschina.net/baomidou/mybatis-plus)

 - 模板引擎：Velocity

 - 前台UI：[HUI](http://www.h-ui.net/)
 
 - 验证码：Kaptcha
 
#实现细节
 
 - 扩展JQuery实现了$.post支持状态错误码(如405)的处理
 
 - 扩展JQuery实现了网页右键菜单的封装（如需要可自行提取）
 
    >/static/js/jquery/jquery-contextmenu.js
    
    >使用方法请参考页面：/templates/resource/list.vm
    
 - 登录验证码使用的Kaptcha谷歌开源的验证码模块
 
 - 实现@Async异步方法并让异步方法使用自定义线程池（记录登录日志）。
 
 - 完成MyBatis-Plus的代码生成器（快速生成Mapper.xml, Mapper.java, IDao.java, DaoImpl.java, IService.java, ServiceImpl.java, Controller.java）已适用本项目。
 
 - ...还有好多细节，就不描述了，请入群讨论或者参见代码
 
#Spring Security
Spring Security是一个能够为基于Spring的企业应用系统提供声明式的安全访问控制解决方案的安全框架。它提供了一组可以在Spring应用上下文中配置的Bean，充分利用了Spring IoC，DI（控制反转Inversion of Control ,DI:Dependency Injection 依赖注入）和AOP（面向切面编程）功能，为应用系统提供声明式的安全访问控制功能，减少了为企业系统安全控制编写大量重复代码的工作。
 
#为什么选择Security而不是Shiro
 
我之所以选择Security是因为网上还没有完整的教程，配置起来确实会遇到很多坑，而关于Security集成SpringBoot的例子更是凤毛麟角，所以我才选择Security集成SpringBoot的完整例子奉献给大家作为参考。

#让Demo跑起来

1.在本地执行 /src/test/resources/tb_security.sql 文件，数据库名字是tb_security

2.默认账户是Admin 123456

#写在最后

本源码的注释略显粗糙，还请见谅(*^_^*)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)