# mybatisplus-maven-plugin

##### 零、Fork 修改
 * 将实体默认包名由 entity 修改为 domain
 * 使用Lombok @Data注解简化Pojo实体代码

##### 一、简介

  * [mybatis-plus](http://git.oschina.net/baomidou/mybatis-plus) 代码生成工具的 maven 插件版本
 
##### 二、使用方法

  * 在项目的pom文件中配置以下内容
  
```xml
 
     com.baomidou 
     mybatisplus-maven-plugin 
     1.0 
     
         
         e:\cache 
         
         true 
         
         true 
         
         Yanghu 
         
		 false 
         
         
             com.mysql.jdbc.Driver 
             jdbc:mysql://127.0.0.1:3306/demo?useUnicode=true&amp;useSSL=false 
             root 
             123456 
         
         
			 
			 remove_prefix_and_camel 
			 
			 bmd_ 
             
             uuid 
             
             com.baomidou.base.BaseService -->
             
             -->
                 sec_user -->
                 table1 -->
             -->
             
             -->
                 schema_version -->
             -->
         
         
             
             com.baomidou 
             
             service 
             
             service.impl 
             
             entity 
             
             mapper 
             
             mapper.xml 
         
         
        	 
			 /template/controller1.java.vm -->
		 
     
     
         
             mysql 
             mysql-connector-java 
             ${mysql.version} 
         
     
 
```

# 执行
  * 下载源码的同学！可使用mvn clean install将自定义的这个插件安装到本地仓库。
	执行：mvn clean install

	命令：mvn com.baomidou:mybatisplus-maven-plugin:1.0:code

  * 显然这个命令太长了，使用很不方便，可在settings.xml中配置如下：
	```
  	 
		 com.baomidou 
	 
	```
  * 然后使用简单命令：mvn mp:code

  
##### 二、参数说明
  
  
  
  

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)