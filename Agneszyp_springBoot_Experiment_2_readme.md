# 实验二 利用Spring boot的自动装配特性实现动态注册组件


## 一、 实验目的 

1. 掌握Spring Boot的自动配置原理；
2. 掌握Spring框架动态注册Bean的原理；
3. 掌握自动生成元数据文件。
4. 掌握spring框架的事件模型。

## 二、 实验环境

1. JDK 11
2. Maven 3.6.0
3. IntelliJ IDEA

## 三、 实验任务
1. 通过IntelliJ IDEA的Spring Initializr向导创建Spring Boot项目,并添加 `Spring Configuration Processor` 依赖。
 
     
 

2. 创建一个自定义的CommandLineRunner接口的实现类，不加@Component注解。
 
     
 

3. 再创建一个自定义的自动配置类，同样也不加@Configuration注解
 
     
 

再创建spring.factories，放在META-INF目录下,写入以下代码，指明MyAutoConfig是一个配置类

```
org.springframework.boot.autoconfigure.EnableAutoConfiguration=
com.example.experiment_2.config.MyAutoConfig
```

4. 运行程序，从下图可知我们模拟的自动配置已经生效了
 
     
 

5. 在自动配置类中加入`@ConditionalOnProperty`注解，添加属性条件
 
     
 

这句代码的意思：判断配置文件中是否存在某个配置`example.auto.enable`,如果存在，判断是成立的,即把`MyCommandLineRunner`注入到容器中

6. 在`application.properties`属性文件中添加一个自定义的属性

```
example.auto.enable=true
```

运行程序可以发现配置类已经生效

 
     
 

如果把true改为false，即

```
example.auto.enable=false
```

运行程序可以发现配置类未生效

 
     
 

7. 创建一个类，并在类上加`@ConfigurationProperties`注解，设置注解的`prefix`属性指定绑定的属性的前缀。

 
     
 

@ConfigurationProperties：告诉SpringBoot将本类中的所有属性和配置文件中相关的配置进行绑定；

prefix = "example.auto"：与配置文件中属性进行一一映射

只有这个组件是容器中的组件，才能容器提供的`@ConfigurationProperties`功能,所以要启动该类的`ConfigurationProperties`功能

8. 在配置类上添加@EnableConfigurationProperties，并指定装配的属性Bean。
 
     
 

@EnableConfigurationProperties:启动指定类的`ConfigurationProperties`功能；将配置文件中对应的值和指定类绑定起来；并把指定类加入到ioc容器中，这里的指定类是MyProperties类

9. 使用spring boot框架提供的注解处理器生成自定义属性的元数据文件

  1）确保pom.xml文件中引入spring-boot-configuration-processor依赖

 
     
 

  2）编译打包项目。target目录下出现元数据文件`spring-configuration-metadata.json`

 
     
 

  3） 生成元数据文件后我们在`application.properties`编辑属性文件时，只要输入属性的部分关键字，idea会自动提示

 
     
 

10. 自定义一个事件发布器，并设置线程池，实现异步发布事件

   1)自定义事件发布器，这个自定义的事件发布器的Bean的名称必须是`applicationEventMulticaster`

 
     
 
  
   2)自定义事件类,继承父类`ApplicationEvent`编写事件类
 
     
 

   3)自定义事件监听器，实现接口`ApplicationListener`编写事件监听器
 
     
 

   4)测试使用线程池异步发布事件
 
     
 

运行程序可发现发布事件时，使用了多线程异步处理
 
     
 

11. 自定义一个线程池

   1)先定义一个线程池，并添加属性

 
     
 
  
   2)创建线程任务

 
     
 

   3)单元测试一下，记得添加两个注解
 
     
 

运行程序
 
     
 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)