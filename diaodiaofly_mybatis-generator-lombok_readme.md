# mybatis-generator-lombok
A plugin for MyBatis Generator to use Lombok annotations instead of getters and setters

## Maven依赖

```xml
 
     com.seejoke 
     mybatis-generator-lombok 
     1.0 
 
```


# MyBatis Generator Lombok plugin and Comment

# 实现的功能

主要整合了lombok插件实现getter/setter等通用方法的自动生成，同时自定义实现了一个注释生成器，
通过抓取数据库表里面的注释作为实体类的注释内容。

# 插件的用法
如果你想在你的maven中使用,将下面的plugin xml脚本复制到你的pom.xml中即可，下面详细提供了配置的用法

```xml
 
     org.mybatis.generator 
     mybatis-generator-maven-plugin 
     1.3.6 
     
         
             mysql 
             mysql-connector-java 
             ${mysql-connector-java.version} 
             runtime 
         
         
             tk.mybatis 
             mapper 
             4.0.2 
         
         
             com.seejoke 
             mybatis-generator-lombok 
             1.0 
         
     
     
         
             Generate MyBatis Artifacts 
             package 
             
                 generate 
             
         
     
     
         true 
         true 
         src/main/resources/mybatis-generator.xml 
     
 

```

同时添加配置文件`generatorConfig.xml`,使用的时候请根据项目需要自行修改对应配置

```xml


 
 
 
     
     

     

         
         

         
         
         
         

         
         

         
             
             
             
         

       
         
       

         
         

         
         
             
             
             
         

         
         
         

         
             
         

         
       
             -->
             
             

             
             
             
         
         

         
         
             
         

         
       
             
         

         
       
         
       
        
     
 


```
Ider操作界面如图

![image](https://www.seejoke.com/static/20190731.png)


## Author
- 初学者 https://seejoke.com

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)