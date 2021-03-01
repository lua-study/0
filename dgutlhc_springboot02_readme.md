东莞理工学院网络空间安全学院

实验报告模板

课程名称：企业开发框架专题                                                                                                                   学期：2019年秋季

| 实验名称 | 利用Spring boot的自动装配特性实现动态注册组件 | 实验序号 | 二           |          |           |
| -------- | --------------------------------------------- | -------- | ------------ | -------- | --------- |
| 姓  名   | 梁宏铖                                        | 学   号  | 201741412222 | 班   级  | 17软卓2班 |
| 实验地点 | ****                                          | 实验日期 | 4/7          | 指导老师 | 黎志雄    |
| 教师评语 | ***                                           | 实验成绩 |              | 评阅教师 |           |
| 百分制   | 80                                            |          |              |          |           |
| 同组同学 |                                               |          |              |          |           |



一、 实验目标：

1、掌握Spring Boot的自动配置原理；

2、掌握Spring框架动态注册Bean的原理；

3、掌握自动生成元数据文件。

4、掌握spring框架的事件模型。

二、 实验条件：

1、JDK 1.8或更高版本

2、Maven 3.6+3、IntelliJ IDEA

三、 实验内容：

1、通过IntelliJ IDEA的Spring Initializr向导创建Spring Boot项目。

![img](src/main/resources/images/wps18.jpg) 

2、创建一个自定义的CommandLineRunner接口的实现类。

![img](src/main/resources/images/wps19.jpg) 

3、创建一个自定义的自动配置类。

![img](src/main/resources/images/wps20.jpg)  

4、创建spring.factories文件

![img](src/main/resources/images/wps21.jpg) 

运行结果：

![img](src/main/resources/images/wps22.jpg) 

5、给自动配置类添加有效条件。

![img](src/main/resources/images/wps23.jpg) 

![img](src/main/resources/images/wps24.jpg)  

6、自定义的一个Bean，绑定属性值，并生成spring配置类的元数据文件。

1）、创建一个类，并在类上加@ConfigurationProperties注解，设置注解的prefix属性指定绑定的属性的前缀。

![img](src/main/resources/images/wps25.jpg) 

2）、 在某个配置类上添加@EnableConfigurationProperties，并指定装配的属性Bean。

![img](src/main/resources/images/wps26.jpg) 

3）、使用spring boot框架提供的注解处理器生成自定义属性的元数据文件。 

![img](src/main/resources/images/wps27.jpg) 

![img](src/main/resources/images/wps28.jpg) 

7、自定义一个事件发布器，并设置线程池，实现异步发布事件。

![img](src/main/resources/images/wps29.jpg) 

![img](src/main/resources/images/wps30.jpg) 

![img](src/main/resources/images/wps31.jpg) 

8、自定义事件类

![img](src/main/resources/images/wps32.jpg) 

9、自定义事件监听器

![img](src/main/resources/images/wps33.jpg) 

10、编写一个测试用例，检查发布事件时，是否使用了多线程异步处理。
![img](src/main/resources/images/wps34.jpg)     

四、 实验总结：


只有自己动手去实践敲代码，才能发现自己更多的不足。在这实验的过程，不断地解决遇到的问题，提升自己的解决问题的能力。        

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)