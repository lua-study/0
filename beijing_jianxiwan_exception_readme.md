1.描述：
在J2EE项目的开发中，不管是对底层的数据库操作过程，还是业务层的处理过程，还是控制层的处理过程，都不可避免会遇到各种可预知的、不可预知的异常需要处理。每个过程都单独处理异常，系统的代码耦合度高，工作量大且不好统一，维护的工作量也很大。 
那么，能不能将所有类型的异常处理从各处理过程解耦出来，这样既保证了相关处理过程的功能较单一，也实现了异常信息的统一处理和维护？答案是肯定的。下面将介绍使用Spring MVC统一处理异常的解决和实现过程。
2.分析 ：
Spring MVC处理异常有3种方式： 
（1）使用Spring MVC提供的简单异常处理器SimpleMappingExceptionResolver； 
（2）实现Spring的异常处理接口HandlerExceptionResolver 自定义自己的异常处理器； 
（3）使用@ExceptionHandler注解实现异常处理；
3.实战 
3.1 引言 
为了验证Spring MVC的3种异常处理方式的实际效果，我们需要开发一个测试项目，从Dao层、Service层、Controller层分别抛出不同的异常，然后分别集成3种方式进行异常处理，从而比较3种方式的优缺点。 
演示项目：perfect-ssm.rar

所需工具：
Eclipse：Version: Mars.2 Release (4.5.2)
Jdk：1.7
Tomcat：tomcat7
资源包：perfect-ssm.rar
数据库：mysql。

操作步骤如下：
1.解压项目到本地,导入到eclipse：
第一步：鼠标选中perfect-ssm.rar，右键单击，选择解压到当前目录。
第二步：打开eclipse，右键点击：import，导入已经存在的maven项目：




导入项目后，首先更新maven依赖包，右键点击项目，maven-update project
第三步：将项目加入到tomcat，启动后，即可开始springmvc统一异常的测试。
注意：数据库的连接配置，需要自己完成，在此不再说明，sql文件：
Db/ssm-perfect-demo.sql
整个项目结构如下：



第四步：
第一种异常方式的测试：使用Spring MVC提供的简单异常处理器SimpleMappingExceptionResolver。
准备工作：
1.打开spring-context-mvc.xml的配置文件，SimpleMappingExceptionResolver-方式一 的注释打开，即放开12-23行，
2.将spring-context-mvc.xml的配置文件中，第26行的异常方式二，注释掉。

3.启动tomcat，打开浏览器，访问：http://localhost:8080/perfect-ssm/exception/simple1
4.显示结果如下：


出现异常的运算条件异常。
控制层代码如下：

同理：
访问：http://localhost:8080/perfect-ssm/exception/simple2

显示：数组下标异常。

第二种异常方式的测试：实现Spring的异常处理接口HandlerExceptionResolver 自定义自己的异常处理器.
1.打开spring-context-mvc.xml的配置文件，SimpleMappingExceptionResolver-方式一 注释，即12-23行加上注释。
2.将spring-context-mvc.xml的配置文件中，第26行的异常方式二，注释放开。

3.继承类如下：

4.启动tomcat，打开浏览器测试，地址：http://localhost:8080/perfect-ssm/exception/simple1
5.显示结果如下：

7.启动tomcat，打开浏览器测试，地址：http://localhost:8080/perfect-ssm/exception/simple2
8.显示结果如下：

第三种异常方式的测试：使用@ExceptionHandler注解实现异常处理。
操作步骤如下：
1.注释掉上述两种方式的配置，在spring-context-mvc.xml.
2.新增baseController.java

3.修改测试层controller,如下：


6.启动tomcat，打开浏览器测试，地址：http://localhost:8080/perfect-ssm/exception/simple1

9.启动tomcat，打开浏览器测试，地址：http://localhost:8080/perfect-ssm/exception/simple2
10.显示结果如下：

4.总结 
综合上述可知，Spring MVC集成异常处理3种方式都可以达到统一异常处理的目标。
从3种方式的优缺点比较，若只需要简单的集成异常处理，
1.推荐使用SimpleMappingExceptionResolver即可；

2.若需要集成的异常处理能够更具个性化，提供给用户更详细的异常信息，推荐自定义实现HandlerExceptionResolver接口的方式；

3.若不喜欢Spring配置文件或要实现“零配置”，且能接受对原有代码的适当入侵，则建议使用@ExceptionHandler注解方式。 


5.参考资料：
1.使用Spring MVC统一异常处理实战
https://blog.csdn.net/ufo2910628/article/details/40399539

2. liushang / SSM统一异常处理测试（博客）
https://gitee.com/beijing_jianxiwan/exception

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)