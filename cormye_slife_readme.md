## 联系方式
微信0
qq群    
 
## qq群 421351927

## 或者加入我的知识星球
![](https://github.com/javanan/slife/blob/master/dec/333.jpg?raw=true)

# **[小福利 点我获取阿里云优惠券](https://promotion.aliyun.com/ntms/act/ambassador/sharetouser.html?userCode=vf2b5zld&utm_source=vf2b5zld)**


## 感谢码云的支持
![](https://github.com/javanan/slife/blob/master/dec/222.jpg?raw=true)


# slife
    spring boot 搭建的一个企业级快速开发脚手架。
### 技术栈
1. Spring Boot  
2. MySQL 
3. Freemark  
4. SiteMesh  
5. Shiro   
6. Bootstrap  
7. mybatis、mybatisPlus  
8. redis  
9. Activiti  


# 编码约定
系统分为controller、service、dao层。
controller主要负责转发、service主要负责业务逻辑、dao主要是数据库的操作。


### 文件名称约定
在页面文件夹中，按照功能模块分别建立不同的文件夹存放页面，如用户的页面就放在user文件夹中，而角色的就放在role文件夹中。
1. 页面如果是列表类型的。页面的文件名用list.ftl命名。
2. 页面如果是详情类型的。页面的文件名用detail.ftl命名。

### controller、service、dao方法名称约定
1. 如果是增加数据操作用insert做前缀。
2. 如果是删除操作用delete做前缀
3. 如果是修改操作用update做前缀
6. 如果是查询操作用select做前缀


# 数据库读写分离




# 缓存ecache、redis




# 新建模块
1. new Module  
2. GroupId --->com.slife   
3. ArtifactId---> slife-模块名称   如  slife-activiti      
4. Version --> 版本号   如 1.0SNAPSHOT  
5. Module-Name--> slife-模块名称   如  slife-activiti      
6. 提交新建模块   
7. pom 文件引入
```
     slife-模块名称 

     
         
             com.slife 
             slife-common 
         

        .
        .
        .其他的依赖
        .
     
```


# JDK版本 1.8
```

     
         
             
                 org.apache.maven.plugins 
                 maven-compiler-plugin 
                 3.6.1 
                 
                     1.8 
                     1.8 
                     UTF-8 
                     
                         -parameters 
                     
                     false 
                 
             
         
     

```




# 新建一个功能模块
1、创建数据库

2、创建entity类

3、创建service类

4、创建controller类

5、创建list界面
```

5.1 到其他list复制代码过


5.2 修改
  
        var url = "${base}/sys/user/";
  

 中的 url 为你刚刚创建的 controller的类
 @Controller
 @RequestMapping(value = "/sys/user")
 public class SysUserController extends BaseController {

 的  @RequestMapping(value = "/sys/user") 值



5.3 修改搜索条件
目前的搜索条件有
    /**
     * 等于
     */
    public static final String SEARCH_EQ="search_eq_";

    /**
     * 左模糊
     */
    public static final String SEARCH_LLIKE="search_llike_";

    /**
     * 右模糊
     */
    public static final String SEARCH_RLIKE="search_rlike_";

    /***
     * 全模糊
     */
    public static final String SEARCH_LIKE="search_like_";



      

     只要在  input中 的 name 加入 search_eq_ 前缀 再加数据库中的字段名称即可



5.4 修改表格的字段名称

```






# 项目截图介绍

## 系统用户管理
![](https://github.com/javanan/slife/blob/master/dec/1.jpg?raw=true)
![](https://github.com/javanan/slife/blob/master/dec/1-1.jpg?raw=true)


## 系统菜单管理
![](https://github.com/javanan/slife/blob/master/dec/2.jpg?raw=true)
![](https://github.com/javanan/slife/blob/master/dec/2-2.jpg?raw=true)


## 系统角色管理

    RBAC权限管理模型

![](https://github.com/javanan/slife/blob/master/dec/3.jpg?raw=true)


## 日志监控

    系统自定义注解，结合AOP，监控用户操作行为

![](https://github.com/javanan/slife/blob/master/dec/4.jpg?raw=true)

## Spring Boot Admin 监控
![](https://github.com/javanan/slife/blob/master/dec/11.png?raw=true)
![](https://github.com/javanan/slife/blob/master/dec/11-1.png?raw=true)


## Activit工作流


![](https://github.com/javanan/slife/blob/master/dec/10.jpg?raw=true)

## API文档

    swaggerUi接口文档展示

![](https://github.com/javanan/slife/blob/master/dec/5.jpg?raw=true)


## 数据库监控

    使用druid监控数据库健康。本来这里是三个数据源的，使用aop动态的书写切换。没上传到git，需要的同学可以私我

![](https://github.com/javanan/slife/blob/master/dec/6.jpg?raw=true)



## maven构建 多模块开发

    根据不同的业务，不在不同的业务模块中开发，如果基本的用户、组织等的管理在 sys模块
    日志的业务逻辑在 log模块

![](https://github.com/javanan/slife/blob/master/dec/7.jpg?raw=true)

**可插拔式部署**
    把不同的模块打包成jar，对应的freemark文件也打包在对应的模块jar中。实现了功能模块的可插拔式部署。

![](https://github.com/javanan/slife/blob/master/dec/8.jpg?raw=true)

























 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)