# MybitesGenerator定制化开发

本源码已经配置好，可直接下载用maven打出jar包后替换你maven下载的mybatis-generator-core-1.3.2.jar文件 注意版本建议1.3.2

如果需要更多定制化开发可以读源码增加自己的定制化开发。本项目添加了对swagger-ui的支持

添加了mybites3Simple方式的生成的Selective方法.并可通过修改配置开关注释，swagger等功能。

使用的 generator.xml 文件如下

```
 
 

 


   

       
           
           
           //自定义的参数，可
        //  通过配置开关注释和swagger注解  使用方式用“，”号隔开 
        //  noget 取消get方法注释
       	//  noset 取消set方法注释
       	//  nofile 取消swagger注解及字段注释
       	//  nomethod 取消mapper方法注释
       	  
      
       

     

 
       
     
	-->


     
     

     
     

     
     
	
       
     	 
       


   
 
```

使用MyBatis3Simple 可以不生成那些用不到的****Example文件，且本项目会生成常用的Selective方法

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)