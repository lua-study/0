scala-springmvc-thymeleaf-bootstrap-template
============================================

A starter web application project combining Scala, Spring, Spring MVC, Thymeleaf 2.0, Spring Security and twitter bootstrap.

What is this?
=============
Spring MVC is a powerful web development framework, however it needs to integrated with bunch of other libraries to make it really powerful! However 
putting together everything needed to get things off the ground is still pretty time consuming and challenging and one of the reasons why
we are seeing one-stop frameworks like Play! become popular. 

In this sample project, I also demonstrate using Scala with Spring MVC instead of Java. Additionally, I integrate with
Spring Security and templating with Thymeleaf.

Stack
=====
* Scala 2.9.2
* Spring 3.2.0 RELEASE
* Spring MVC 3.2.0
* Spring Security 3.2.0 M1
* [Spring Security Scala Extensions](http://blog.springsource.org/2012/12/10/introducing-spring-scala/) - Scala extensions for spring
* [Jacks Jackson module](https://github.com/wg/jacks) - Handle's serialization of objects to JSON. The default Jackson based mapper does not handle scala case classes.
* [Thymeleaf 2.0](http://www.thymeleaf.org) + [Layout Plugin](https://github.com/ultraq/thymeleaf-layout-dialect) - Excellent templating engine. I use 
the layout dialect  to use it for decorating as well.
* Bootstrap - Twitter's Bootstrap CSS
* Logback - for logging. Example showcases how to get Spring to use logback instead of Apache commons logging.
* Maven - For build and jetty integration


How to run
==========
Checkout project, and simply do a  mvn jetty:run and point your browser to http://localhost:8080/

Credits
=======
Based on [thymeleaf-spring-maven-archetype](https://github.com/maggandalf/thymeleaf-spring-maven-archetype)

Contact
=======
Twitter: [@zoheb](http://www.twitter.com/zoheb)

Web: [zoheb.com](http://www.zoheb.com)

[![endorse](http://api.coderwall.com/zohebsait/endorsecount.png)](http://coderwall.com/zohebsait)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)