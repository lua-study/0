#officialWebsite
## 技术选型

* 核心框架：Spring Framework 4.3.5
* 安全框架：Apache Shiro 1.2
* 视图框架：Spring MVC 4.3.5
* 视图驱动：Thymeleaf 3.0.2.RELEASE
* 任务调度：Spring Task 4.3.5
* 持久层框架：MyBatis 3.2
* 数据库连接池：commons-dbcp 1.4
* 缓存框架：Ehcache 2.6、Redis
* 日志管理：log4j2 slf4j

## 文件目录说明
**源码主目录: scau.zzf**

**base:主要存放基础类目录，不需要经常更改的类文件,这里对部分文件做主要说明**
> common:常用的通用继承类

>> BaseController ：每个Controller 继承的抽象类

>> IBaseMapper ：每个Dao接口 继承的接口

>> IBaseService ：每个Service接口继承的接口

>> Unique ：每个实体类继承的父类

> shiro：存放改写后的shiro过滤器

> dictionary :数据字典

> service :存放Service接口，每个接口需继承 IBaseService

>>Imp: 存放Service实现类，这里主要是用于一些较复杂的比如表关联操作，mybatis通用Mapper无法实现的SQL，需要自己手写的方法，便在此实现

> task : 存放实现任务调度的类，相对应需要修改spring-task.xml配置

> web : Controller层

**资源主目录: resources**

>config :存放配置文件

>>spring

## 如何上手

* 推荐使用IntellJ IDEA

* 修改config/properties的数据库文件，安装redis，然后修改redis.conf中的密码选项，redis.conf默认没有密码选项，若不进行修改，则需注释spring-redis.xml和spring-shiro.xml的中redis配置的密码选项

* 建立对应的实体类（继承Unique） Dao（继承IBaseMapper） Service (继承IBaseService(T)) Impl （继承AbstractBaseService和实现对应的Service接口）

* 已IUserSerive为例子，通过自动注入，IUserService就可以使用定义和实现在AbstractBaseService中的各个方法

## 使用Mybatis通用Mapper以及分页插件

*  IBaseService  定义了通用Service方法，AbstractBaseService 通过使用通用Mapper插件实现了通用Servicve方法
*  分页插件使用，如
    PageHelper.startPage(1, 10);
    List  userList = iUserService.findAll();
    分页插件会为后面执行的*第一条*自动分页

## Controller注意事项
*   每个Controller都需要继承Base Controller类
*   返回数据统一使用Result，使用sendCode方法写入状态码和状态信息
*   状态码和状态信息存放在dictionary包下的Code枚举类,每个枚举类实现BaseCode
*   增加接口使用@Validated(ValidObject.class)进行校验，修改接口使用@Validated({ValidObject.class，ValidId.class})，在Entity上确定校验规则,同时方法要以**va开头**，**申明BindResult result 参数**
## entity注意事项
*  每个实体类继承Unique 类，默认使用id作为主键，生成方式为UUID
*  添加不属于数据库的字段，要用上@Transient注解



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)