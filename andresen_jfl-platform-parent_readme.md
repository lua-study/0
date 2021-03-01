 
     
     
    	Jfl-platform, a distruted service depends on Dubbo and provides a system for management.
    	 
    	 
      		 
   		 
   		 
      		 
   		         	  
    	 
       		 
     	 
     	 
       		 
     	 
         
 


#### 项目介绍
 此项目主要用于核心系统迁移，使用最新的`微服务`技术，使用的后台技术主要有`Druid`数据源，`Mybatis-Plus`，`Dubbo`，`Redis`，`SpringMVC`，`SpringBoot`，`Shiro`，`Restful`，页面采用`thymeleaf`模板引擎，以及`Bootstrap`以及`Layui`样式等技术。

#### 软件架构
```
├─jfl-platform-parent
│	│
│	├─jfl-platform-api----------------------接口模块 这个相当于开发给web或者对外接口部分的调用的api，以及定义的实体类
│	│
│	├─jfl-platform-common-------------------公共类 一些基础公共类
│	│
│	├─jfl-platform-service------------------dubbo服务层  主要与数据库交互
│	│
│	├─jfl-platform-web----------------------web端
│	│
│	└─jfl-platform-restful------------------restful接口对外
```


#### 安装教程

1. 登陆`gitee`，并注册相应的账号；
2. git clone或者下载zip包到本地；
3. 导入到`eclipse`中，两种方式都可以；
4. 安装`mysql`数据库；
5. 导入数据库脚本；
6. 安装`redis`服务；
7. 安装`zookeeper`并启动服务；
8. 安装`dubbo-admin`并启动服务;
9. 修改`jfl-platform-service`下的`application.properties`和`jfl-platform-web`下的`application.properties`的数据库以`zookeeper`，以及`redis`地址；
10. 先启动`JflPlatformServiceApplication.java`服务，再启动`JflPlatformWebApplication.java`，一定要按照顺序来，否则服务无法调用；
11. 访问地址介绍：localhost:8881管理地址；dubbo-admin地址：localhost
12. 服务关闭，按照以上顺序反过来停服务即可(主要由于服务端存在定时任务会检查zk上注册的服务需要先启动服务端)，客户端不一定要后关闭，关注相应的dubbo配置的官方文档即可。

### 演示系统
1. http://212.64.10.83:8080
2. 用户名：admin 密码：123456


#### 项目开发进度
1. 2018-11-26之前  初次提交到`码云`，已集成`logback`，`mybatis`功能；
2. 2018-11-26  项目已集成`pagehelper`功能，并能通过`postman`发送到后台请求，后续添加`shiro`来做用 户权限校验与认证；
3. 2018-11-27 添加`jfl-platform-api`接口模块；
4. 2018-11-28 集成`dubbo`功能，并能测试通过；
5. 2018-11-29 `dubbo`功能集成完毕，优化代码结构中；
6. 2018-12-02 代码结构优化完成；
7. 2018-12-03 集成前端模板引擎`thymeleaf`；
8. 2018-12-04 集成`redis`，主要用于存储常用的数据，以及系统缓存；
9. 2018-12-11 大版本提交；
10. 2018-12-12 `Shiro`调用`dubbo`服务成功，目前`redis`存在问题；
11. 2018-12-13 完成系统菜单展示，`thymeleaf`模板以及`bootstrap`等技术完成；
12. 2018-12-21 前端用户模块，岗位模块已基本完成，角色和菜单正在开发中；
13. 2018-12-29 大功能上线，目前缓存模块以及日志模块尚未加入，正在优化后台代码以及页面中；
14. 2019-01-01 添加系统操作日志功能，优化部分代码，数据字典跳转字典数据存在bug，尚待解决；
15. 2019-01-03 用户密码加密问题，日志未记录请求参数问题，后期增加对请求参数是否记录的开关；
16. 2019-01-04 优化代码结构，以及已知BUG；
17. 2019-01-06 `Shiro`登录优化，添加部分会话管理功能；
18. 2019-02-01 集成会话管理；
19. 2019-02-14 `restful`接口优化；
20. 2019-02-15 集成首页换肤功能；
21. 2019-03-17 支持修改头像功能；
22. 2019-04-11 修复日志模块，以及修复日志文件bug；
23. 2019-04-21 优化页面结构、添加演示模式、添加第三方接口开关；
24. 2019-09-30 添加`swagger-ui`接口验证部分，以及数据库读写分离ing
25. ...

### 系统思维导图
![Alt text](doc/img/JFL_1.png)
### 后期开发方向
![Alt text](doc/img/processing.png)
### 系统功能截图
 
	 
	     
	     
	 
	 
	     
	     
	 
	 
	     
	 
	 
	     
	     
	 
	 
	     
	     
	 
	 
	     
	     
	 
	 
	     
	     
	 	
	 
	     
	 
	 
	     
	     
	 	
 

### 技术点介绍
1. `Mybatis`目前代码中使用了`mybatis-plus`（未使用其分页功能），分页使用的是`pageheplper`，自己重写了`BaseMapper`，`BaseService`以及`BaseServiceImpl`，对于`Mybatis-Plus`支持的批量更新未做处理，后期需要优化，以及事务的处理等；目前`Sql`使用了注解，`xml`以及代码动态`Sql`，学习的话可以都使用，后期统一使用一种规则或者重新分装；
2. 实体类中由于使用了`@Data`注解，因此需要eclipse集成`lombok`插件；
3. 由于使用热部署功能导致对象无法转换问题，需要在`pom.xml`注释到热加载的依赖
4. 相应的截图未做出对应的调整请注意。
#### 使用说明

1. jdk1.8+
2. dubbo 2.6+
3. redis 3.2+
4. mariadb10.+
5. tomcat8+
6. eclipse
7. zookeeper 3.4+
8. ...

#### 严重申明
此项目只提供大家学习使用，如需商用请跟本人联系！
邮箱：yanzhao_jn@163.com。 
一经发现商用，将追究其法律责任！

### 技术交流
QQ群：879507993
      


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)