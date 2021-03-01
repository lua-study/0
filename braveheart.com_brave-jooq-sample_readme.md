# springboot、dbcp、jooq、mysql
结合Springboot，用dbcp进行连接池管理，有事务控制

# mysql本地安装参见docker官网镜像。

# pom文件注意，需要将生成的目录加入到classpath

We will configure the build-helper-maven-plugin plugin such that maven will add the JOOQ generated code resides in gensrc/main/java directory as source folder.

```
 
     org.codehaus.mojo 
     build-helper-maven-plugin 
     
         
             generate-sources 
             
                 add-source 
             
             
                 
                     gensrc/main/java 
                 
             
         
     
 
```

# jooq介绍，可以参见[oschina](https://www.oschina.net/p/jooq)或者[官网](http://www.jooq.org/doc/3.6/manual-single-page/#jooq-in-7-steps)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)