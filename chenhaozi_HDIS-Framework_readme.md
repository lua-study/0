      
 HDIS-Framework 
 HDIS是一个基于SpringBoot、Kubernetes、阿里云服务，编写的一个用于支撑微服务的极速开发框架。 
 其文档详尽，Demo全面，设计合理，开箱即用，节省开发时间，提升开发效率。 
 配套的docker、Kubernetes教程已踩过各种坑，让你的微服务无障碍的顺畅运行起来。 
 HDIS与Kubernetes或SpringCloud配合使用，能达到最佳效果。 
   《使用说明文档》   
   《Demo地址》   
   《配套K8S运维教程》   

## 1.0项目介绍
用于支撑微服务的极速开发框架。 
同时也可以关注[《我的博客》](https://gitee.com/w6513017/HDIS-Demo)获取最新的技术分享。 
## 2.0软件架构
基于SpringBoot:1.5.13.RELEASE版本 
基于JDK1.8版本 
### 2.1框架整合pom
framework-starter-web：WebMvc的快速开发扩展框架 
framework-starter-data-jpa：JPA的快速开发扩展框架 
framework-starter-data-mongo：MongoDB的快速开发扩展框架 
framework-starter-cache：集群缓存、二级缓存、缓存工具的快速开发框架 
framework-starter-security：基于Oauth2.0的安全框架 
framework-starter-push：推送服务的快速开发框架 
framework-starter-sms：短信发送服务的快速开发框架 
framework-starter-test-benchmark：基准测试的快速开发框架 
### 2.2框架模块
framework-cache-redis：集群缓存、二级缓存、缓存工具的快速开发框架 
framework-controller：controller通用处理框架 
framework-data-jpa：JPA的快速开发扩展框架 
framework-data-mongo：MongoDB的快速开发扩展框架 
framework-dictionary：数据字典工具 
framework-exception：统一异常处理器 
framework-log：日志框架，日志输出到本地 
framework-log-aliyun：日志框架，日志输出到阿里云 
framework-page：统一分页工具 
framework-push：推送服务的统一接口定义。 
framework-push-aliyun:推送服务的阿里云实现。 
framework-response：统一返回值工具 
framework-security：基于Oauth2.0的安全框架 
framework-sms：短信服务的统一接口定义 
framework-sms-aliyun：短信服务的阿里云实现 
framework-swagger：swagger快速开发扩展框架 
framework-test：测试工具集 
framework-utils：常用工具集合 
## 3.0安装教程
### 3.1源码安装：使用maven编译安装到本地
```
git clone https://gitee.com/w6513017/HDIS-Framework.git
mvn clean install
```
### 3.2直接引用：使用maven引用
```
 
 
     tech.hdis 
     framework 
     1.2 
 
 
 
     
         tech.hdis 
         framework-starter-web 
     
 
 
 
     
         
         
             org.springframework.boot 
             spring-boot-maven-plugin 
         
         
         
             org.codehaus.mojo 
             native2ascii-maven-plugin 
         
     
 
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)