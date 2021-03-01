# [Spring Cloud敏捷开发框架](https://gitee.com/likun_557/p-parent "查看代码")

## 1、概述

- 用来快速开发Spring Cloud项目
- 前期会考虑：数据读写分离、数据库各种基本操作、集成自己开发的消息服务、分布式业务调度服务、自动生成代码、后台管理系统页面框架

### 开发工具及相关技术：
- Maven3.3.9
- Jdk1.8
- IntelliJ IDEA
- Springboot2.0.4
- Springcloud Finchley.SR1
- Mybatis
- Freemarker
- ElasticJob
- Sesjs

## 2、项目介绍
- p-base:
    - p-base-comm:框架基础库
    - p-base-jdbc:数据库操作组建，数据库操作基类、主从分离、数据库操作的各种工具方法等
    - p-base-jdbc-starter:p-base-jdbc的starter pom，若需要对数据库进行操作，需在maven中引入该模块
    - p-base-page:分页组件
    - p-base-web:web项目的全局配置、工具等
    - p-base-web-starter: p-base-web的starter pom
- p-code:
    - p-code-generate:代码生成器
- y-cloud:
    - p-cloud-discovery:服务注册中心
    - p-cloud-gateway:服务网关
- y-core: 表示一个业务模块
    - p-core-comm:业务模块公共类
    - p-core-service:业务模块restful服务接口
    - p-core-api:p-core-service对外的feign接口类
    - p-core-api-starter:p-core-api的springstarter,其他模块如果需要调用p-core-service中的服务，需在maven中引入该模块
    - p-core-test:测试模块，通过feign来调用p-core-service
    - p-core-admin: [后台管理系统](http://admin.itsoku.cn/)

## 3、端口
- p-cloud-discovery:7001
- p-cloud-gateway:8001
- p-core-service:9001
- p-core-test:9002
- p-core-admin:9003

## 4、启动顺序
- p-cloud-discovery
- p-cloud-gateway
- p-core-service
- p-core-test

## 5、运行示例
### 数据库配置
- 1、以mysql为例，在本地创建2个库：**ms_master**、**ms_slave**  
- 2、分别ms_master、ms_slave中执行脚本：[数据库初始化脚本](https://gitee.com/likun_557/p-parent/blob/master/p-core/other/%E6%95%B0%E6%8D%AE%E6%A8%A1%E5%9E%8B/create.sql)

### redis配置
> p-core-admin：后台管理系统通过redis来解决session问题  
>**redis配置信息见p-core-admin项目中的application.yml配置文件**
```text
spring:
  redis:
      host: 192.168.11.19
      port: 6379
      password: 123
      database: 0
    session:
      store-type: redis #使用redis存储session信息
      timeout: 3600 #session过期时间
      redis:
        namespace: spring:session #redis中用于存储session信息的命名空间
        flush-mode: immediate #session信息刷新模式，immediate:立即刷新，on_save:http response提交之后刷新
        cleanup-cron: 0 * * * * * #清理redis中过期session数据的job执行频率，默认每分钟执行一次
```

### hosts文件配置
```text
127.0.0.1 admin.ms.org static.ms.org
```
> **admin.ms.org**：访问p-core-admin  
**static.ms.org**：访问静态资源，指向p-parent/static目录

### nginx配置
``` text
server {
    listen 80;
    server_name static.ms.org;
    root C:/Users/pc/IdeaProjects1/p-parent/static;
}

server {
    listen 80;
    server_name admin.ms.org;
	location / {
        proxy_pass http://127.0.0.1:9003/;
    }
}
```
### 启动应用
- p-cloud-discovery
- p-cloud-gateway
- p-core-service
- p-core-test
- p-core-admin

### 访问测试例子
- [访问p-core-test例子](http://localhost:9001/demo/list/1/5)
- [访问p-core-admin](http://admin.ms.org)

## 6、web集群session配置

> **目前项目中使用redis来解决集群session问题,如下：**

- 1、引入maven依赖
```xml
 
     
         org.springframework.boot 
         spring-boot-starter-data-redis 
     
     
         org.springframework.session 
         spring-session-data-redis 
     
 
```

- 2、配置application.properties
```text
spring:
  redis:
      host: 192.168.11.19
      port: 6379
      password: 123
      database: 0
    session:
      store-type: redis #使用redis存储session信息
      timeout: 3600 #session过期时间
      redis:
        namespace: spring:session #redis中用于存储session信息的命名空间
        flush-mode: immediate #session信息刷新模式，immediate:立即刷新，on_save:http response提交之后刷新
        cleanup-cron: 0 * * * * * #清理redis中过期session数据的job执行频率，默认每分钟执行一次
```

- 3、代码中使用session
```text
request.getSession().setAttribute("key",value);
```
**注意:key必须是字符串格式，value必须实现java.io.Serializable接口，支持序列化**


** 相关截图

![](https://oscimg.oschina.net/oscnet/5147a665c5633b6add4a1d04da64ffbb15d.jpg)
![](https://oscimg.oschina.net/oscnet/d3d18ab5a31aa7a42554bc71a61961be92e.jpg)
![后台](https://oscimg.oschina.net/oscnet/212c3b56d867c475bf14df12df26fda0f9d.jpg)
![](https://oscimg.oschina.net/oscnet/7d460280c58e18c584a2333372c33cca55a.jpg)
![](https://oscimg.oschina.net/oscnet/7cd693d3efe02187dd24b63d6f828e8bb33.jpg)
![](https://oscimg.oschina.net/oscnet/b9fd20e5df8976b82c9df31eadb7c265147.jpg)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)