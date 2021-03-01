# SSM
SpringMVC,Mybatis,Spring三大框架的整合总是很麻烦，在此提供一个已经整合好三大框架的包，可以直接下载导入Myeclipse使用，项目基于Maven做依赖管理。项目基于Mysql自带的Sakila数据库实现了MIS系统中常用的多个功能，运行前请安装好Mysql5.6。

其中包含的内容如下：

1.SpringMVC4.3.16,Mybatis3.2.2,Spring4.3.16三大框架的整合；

2.前端框架集成了Bootstrap3.3.5，Jquery1.12.3,集成了Bootstrap插件Bootgrid数据表格实现分页，使用Bootstrap的datetimepicker插件实现日期时间选择，后台的分页使用Mybatis的插件pagehelper实现；

3.数据库使用Mysql中自带的sakila数据库，使用前，请将SSM\src\main\resources\conf中的spring-mybatis.xml中的数据库密码设置为自己的；

4.实现了sakila中的单表的增删改查和跨表查询，跨表查询包括了Mybatis的1-N和N-1双向映射；

5.不再使用作业自动调度框架Quartz实现作业调度，使用spring框架自带的调度器进行作业调度，简化了配置；

6.json插件使用阿里的开源fastjson工具,注意低版本的fastjson与swagger不兼容，这里有坑；

7.包含了一个文件上传的功能，可上传单个或多个文件；

8.包含了数据表导出为Excel下载的功能，包含了解析Excel内容的API，使用POI实现；

9.包含了带验证码的登录功能以及登录权限验证的拦截器, **登录用户名TOM，密码1234** ；

10.要使用Struts2+hibernate+spring的整合，[点击这里进入](https://github.com/shenzhanwang/SSH_maven)  

11.去掉所有JSP，使用HTML代替，有利于前后端分离;

12.整合日志工具log4j2，较log4j1.x有较大性能提升，支持日志文件输出和控制台输出；

13. 整合接口文档swagger2.4，入口http://localhost:8080/SSM/swagger-ui.html

14. 将后台接口REST化，详情参考https://gitee.com/shenzhanwang/Spring-REST

15. 添加mybatis的动态SQL的使用

访问入口：http://localhost:8080/SSM/login

16. 要使用spring boot，切换分支到https://gitee.com/shenzhanwang/SSM/tree/spring-boot/

效果图：

![输入图片说明](https://images.gitee.com/uploads/images/2018/1128/125458_22041b77_1110335.gif "SSM.gif")

 ![输入图片说明](http://git.oschina.net/uploads/images/2016/1216/145410_018a9ca7_1110335.png "在这里输入图片标题")

![输入图片说明](https://gitee.com/uploads/images/2017/1103/174138_49e9143e_1110335.png "QQ截图20171103174132.png")

![输入图片说明](https://gitee.com/uploads/images/2018/0427/191550_c71b959c_1110335.png "QQ截图20180427190522.png")

![输入图片说明](https://gitee.com/uploads/images/2018/0427/191600_16979257_1110335.png "QQ截图20180427191120.png")



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)