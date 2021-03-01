 
     
     
        Based on SpringBoot2, Crown builds a rapidly developed web application scaffolding.
               
               
         Crown官方交流群：223706133  
               
         
		 
		  
		 
		  
		 
		  
		 
          
		 
          
		 
		  
         
          
         
          
       
 

-----------------------------------------------------------------------------------------------
 
     
        热烈庆祝 mybatis-plus、layui 荣获 2018 年度最受欢迎中国开源软件  Top 5 .
         
         
     
      
 

-----------------------------------------------------------------------------------------------
##### Intro :cat:

> 本人作为**MyBatisPlus核心开发**之一，编写了该项目以推广**MyBatisPlus3.0**的使用

> 参考本项目完全可以让你轻松玩转MyBatisPlus最新版本（**持续更新**），故也称为教学版本

> 除了基本使用，还有一些**进阶玩法**在项目中等待大家来发现

> **体验地址** [http://crown.baomidou.com/login.html](http://crown.baomidou.com/login.html)

-----------------------------------------------------------------------------------------------
#####
 
 1  JDK1.8+  
 2  MySQL5.7+  
 3  Gradle4.10+  
 

-----------------------------------------------------------------------------------------------
##### Start :dog:
 
 1  准备好上述基本环境  
 2  导入crown.sql文件(src/test/resources/sql/crown.sql)  
 3  启动CrownApplication.java  
 4  访问http://localhost:8088  
 

-----------------------------------------------------------------------------------------------
##### Show :palm_tree:

![idea-annotation-compile.png](https://raw.githubusercontent.com/Caratacus/Resource/master/crown/login.jpg)
 
![idea-annotation-compile.png](https://raw.githubusercontent.com/Caratacus/Resource/master/crown/user.png)
 
![idea-annotation-compile.png](https://raw.githubusercontent.com/Caratacus/Resource/master/crown/role.png)
 
![idea-annotation-compile.png](https://raw.githubusercontent.com/Caratacus/Resource/master/crown/menu.png)
 
![idea-annotation-compile.png](https://raw.githubusercontent.com/Caratacus/Resource/master/crown/menu-form.png)
 
![idea-annotation-compile.png](https://raw.githubusercontent.com/Caratacus/Resource/master/crown/resource.png)

-----------------------------------------------------------------------------------------------
##### Feature :rocket:
 
 1  标准的Restful风格，完美的标准化API  
 2  防止XSS攻击、SQL注入，妈妈再也不用担心我的安全问题  
 3  深度定制Mybatisplus，各种玩法意想不到  
 4  深入拓展ModelMapper，各种类型一键转换  
 5  运用Liquibase，增量SQL一键导出  
 6  接口日志详情打印，所有访问信息一览无遗  
 7  各项配置调制最优，再也不需要担心默认值性能问题  
 8  P6spy打印SQL，一切操作尽在掌握  
 9  Shiro RestApi 鉴权，前后端完全隔离  
 10  Mock测试、TravisCI保驾护航，BUG再见，再也不见  
 N  更多特性持续更新  
 

-----------------------------------------------------------------------------------------------
##### Frameworks :microscope:
 
 1  核心框架: SpringBoot  
 2  持久层框架: MyBatisplus  
 3  数据库连接池: HikariCP  
 4  SQL脚本: Liquibase  
 5  数据校验: HibernateValidator  
 6  对象转换: ModelMapper  
 7  JSON转换: Jackson  
 8  接口文档: Swagger  
 9  基础工具类: ApacheCommons、VjTools  
 10  日志: SLF4J、Async Log4j2  
 11  SQL打印: P6spy  
 12  权限认证: Shiro  
 13  页面: layui  
 N  以上依赖基本都会升级为最新版本  
 

-----------------------------------------------------------------------------------------------
##### [Lombok](http://projectlombok.org/) FAQ :mushroom:

* ###### 为什么下载的代码后，使用IDEA打开没有相应的get set方法呢？

 
    答：因为框架使用了Lombok包，它是在编译的时期，自动生成get set方法，并不影响运行
 

* ###### 下载的代码后，使用IDEA想自己修改源码时总是莫名提示报错？

![idea-annotation-compile.png](https://raw.githubusercontent.com/Caratacus/Resource/master/idea-annotation-compile.png)

 
    答：上图所示，IDEA下载Lombok插件并开启注解编译支持
 

* ###### 代码编译各种不通过，是什么问题？![Travis Build标签](https://travis-ci.org/Caratacus/Crown.svg?branch=master)

 
    答：查看问题上travis build标签，passing代表代码测试用例通过，更不存在编译问题；failing表示代码测试不通过，联系作者（作者自己也会收到邮件）
 

* ###### 为什么项目启动后用127.0.0.1无法访问项目，localhost却可以？

 
    答：项目是前后端分离的需要127.0.0.1访问方式，修改config.js中serverUrl路径即可
 

-----------------------------------------------------------------------------------------------
##### License :globe_with_meridians:

   The Crown is released under of the [Mit License](https://mit-license.org).  

-----------------------------------------------------------------------------------------------
##### 有事烧钱 :octocat:

 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)