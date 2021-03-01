# 项目介绍

Slife是一个使用`Spring Boot`搭建的企业级快速开发脚手架。
    

### [阿里云代金券 1888元，点击即可获取](https://promotion.aliyun.com/ntms/yunparter/invite.html?userCode=vf2b5zld) 
 

### 建议注册个新账户购买，享受2折 ，如果购买多个产品，可以先放到购物车再一键购买


## 技术栈

Slife需要`Java 8`环境，推荐使用`IDEA`作为开发工具，以下是Slife所用到的技术：

1. Spring Boot v1.5.4
2. MySQL
3. Freemark
4. SiteMesh
5. Shiro
6. Bootstrap
7. mybatis、mybatisPlus
8. redis
9. Activiti v5.22

## 部署

Slife是使用`Maven`构建的多模块项目，分模块开发，各模块可插拔。`slife-web`项目是Slife的主入口，在`slife-web`的`pom`文件中引入需要的模块之后，通过以下步骤来启动项目：

- 导入数据库

  在项目的`db`文件夹下有数据库脚本，首先导入数据。

- 启动`redis`服务

  需本地安装`redis`或者其他远程`redis`。

- 修改相关配置

  修改`web`下`application-dev.yml`中的配置：

  1. 数据库相关配置
  2. `redis`相关配置

- 启动项目

  启动`web`工程下的`WebApplication`。

## 开发

开发上Slife做了一些限制，或者叫约定：

1. 编码约定

系统分为`controller`、`service`、`dao`层。
`controller`主要负责转发、`service`主要负责业务逻辑、`dao`主要是数据库的操作。

2. 文件名称约定

   在页面文件夹中，按照功能模块分别建立不同的文件夹存放页面，如用户的页面就放在`user`文件夹中，而角色的就放在`role`文件夹中。

   - 页面如果是列表类型的。页面的文件名用`list.ftl`命名。

   - 页面如果是详情类型的。页面的文件名用`detail.ftl`命名。

3. `controller`、`service`、`dao`方法名称约定

   - 如果是增加数据操作用`insert`做前缀。

   - 如果是删除操作用`delete`做前缀

   - 如果是修改操作用`update`做前缀

   - 如果是查询操作用`select`做前缀

若是要新建模块开发，可以按照以下步骤进行：

1. new Module 

2. GroupId --->com.slife 

3. ArtifactId---> slife-模块名称   如  slife-activiti

4. Version --> 版本号   如 1.0SNAPSHOT 

5. Module-Name--> slife-模块名称   如  slife-activiti 

6. 提交新建模块 

7. pom 文件引入

   ```xml
    slife-模块名称 
   
        
            
                com.slife 
                slife-common 
            
   
           .
           .
           .其他的依赖
           .
        
       
        
            
                
                    org.apache.maven.plugins 
                    maven-compiler-plugin 
                    3.6.1 
                    
                        1.8 
                        1.8 
                        UTF-8 
                        
                            -parameters 
                        
                        false 
                    
                
            
        
   ```


新建完成模块之后需要继续功能性开发，可按照以下步骤：

1. 创建数据库

2. 创建`entity`类

3. 创建`service`类

4. 创建`controller`类

5. 创建列表界面

   - 将其他功能的`list.ftl`文件复制一份过来。

   - 修改`var url = "${base}/sys/user/"`为刚刚创建的`Controller`所以对应的`@RequestMapping`的值。

   - 修改搜索条件。

   - ```java
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
      
     /**
      * 全模糊
      */
     public static final String SEARCH_LIKE="search_like_";
     
     
     ```

     在模版文件中

     >   

     只要在`input`中的`name`加入`search_eq_` 前缀 再加数据库中的字段名称即可。

   - 修改对应字段名称。

emmm，其实我觉得这部分好像没必要写的。

## 项目截图

- 用户管理

  ![](https://github.com/javanan/slife/blob/master/dec/1.jpg?raw=true)

  ![](https://github.com/javanan/slife/blob/master/dec/1-1.jpg?raw=true)

- 菜单管理

  ![](https://github.com/javanan/slife/blob/master/dec/2.jpg?raw=true)

  ![](https://github.com/javanan/slife/blob/master/dec/2-2.jpg?raw=true)

- 角色管理

  ![](https://github.com/javanan/slife/blob/master/dec/3.jpg?raw=true)

- 日志监控

  ![](https://github.com/javanan/slife/blob/master/dec/4.jpg?raw=true)

- Spring Boot Admin监控

  ![](https://github.com/javanan/slife/blob/master/dec/11.png?raw=true)

  ![](https://github.com/javanan/slife/blob/master/dec/11-1.png?raw=true)

- Activiti工作流

  ![](https://github.com/javanan/slife/blob/master/dec/10.jpg?raw=true)

- API文档

  ![](https://github.com/javanan/slife/blob/master/dec/5.jpg?raw=true)

- 数据库监控

  ![](https://github.com/javanan/slife/blob/master/dec/6.jpg?raw=true)

# 贡献代码

## 贡献代码

- 搭建开发环境

  您需要在系统中安装好`JDK 1.8`或以上的版本，并安装好 `Maven`。您可能还需要一个`IDE`来进行开发。

- 贡献

  我们随时都欢迎任何贡献，无论是简单的错别字修正，`BUG`修复还是增加新功能。请踊跃提出问题或发起 `PR`。

Slife申请了`JetBrains`的全家桶授权，因为之前活跃人数只有两个，所以只申请到了2个全家桶的`Licenses`，如果有贡献者需要，可以联系我们。

# 其他

## 联系我们

- qq群

  搜索421351927加群，或者点击   ，验证问题请回答名称，不要回答数字哦！

## 鸣谢

|                组织&个人                |                             方式                             |
| :-------------------------------------: | :----------------------------------------------------------: |
|       [码云](https://gitee.com/)        |                            GVIP等                            |
| [JetBrains](https://www.jetbrains.com/) | 正版[IDE](https://www.jetbrains.com/store/#edition=discounts)授权 |

## 支持我们

## 友情链接

## 阿里云优惠券

[点我获取阿里云优惠券](https://promotion.aliyun.com/ntms/yunparter/invite.html?userCode=vf2b5zld)


[腾讯云](https://cloud.tencent.com/redirect.php?redirect=1005&cps_key=1cdaea7b77fe67188b187bce55796594&from=console)











 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)