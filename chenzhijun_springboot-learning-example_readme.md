# springboot-learning-example
spring boot 实践学习案例，是 spring boot 初学者及核心技术巩固的最佳实践。

## 作者与学习乐园
源码地址：我的[GitHub地址](https://github.com/JeffLi1993 "GitHub")、[OSCGit地址](https://git.oschina.net/jeff1993/springboot-learning-example "OSCGit") 
作者：[泥瓦匠BYSocket](http://www.bysocket.com/ "泥瓦匠BYSocket") 
QQ 群 
编程之美① 365234583   
编程之美② 290714704    
关注微信公众号【泥瓦匠BYSokcet】，及时得到技术文章推送 
![公众号](http://www.bysocket.com/wp-content/uploads/2017/01/qrcode_for_gh_cd421e7eb7d6_430.jpg)


## 一、项目结构
「Spring Boot 那些事」：[传送门](http://www.bysocket.com/?page_id=1639 "Spring Boot 那些事") 

#### a. 『 基础 - 入门篇 』
- springboot-helloworld 
 [《Spring Boot 之 HelloWorld 详解》](http://www.bysocket.com/?p=1124 "Spring Boot 之 HelloWorld详解") 
- springboot-properties  
 [《Spring Boot 之配置文件详解》](http://www.bysocket.com/?p=1786 "Spring Boot 之配置文件详解") 

#### b. 『 基础 - Web 业务开发篇 』
- springboot-restful  
 [《Springboot 实现 Restful 服务，基于 HTTP / JSON 传输》](http://www.bysocket.com/?p=1627 "Springboot 实现 Restful 服务，基于 HTTP / JSON 传输") 
 [《Spring Boot 之 RESRful API 权限控制》](http://www.bysocket.com/?p=1080 "Spring Boot 之 RESRful API 权限控制") 
- springboot-freemarker  
[《Spring Boot 集成 FreeMarker 详解案例》](http://www.bysocket.com/?p=1666 "Spring Boot 集成 FreeMarker 详解案例") 

#### c. 『 基础 – 数据存储篇 』
- springboot-mybatis  
 [《Springboot 整合 Mybatis 的完整 Web 案例》](http://www.bysocket.com/?p=1610 "Springboot 整合 Mybatis 的完整 Web 案例") 
- springboot-mybatis-mutil-datasource  
 [《Spring Boot 整合 Mybatis 实现 Druid 多数据源详解》](http://www.bysocket.com/?p=1712 "Spring Boot 整合 Mybatis 实现 Druid 多数据源详解") 


#### d. 『 基础 – 数据缓存篇 』
- springboot-mybatis-redis  
 [《Spring Boot 整合 Redis 实现缓存操作》](http://www.bysocket.com/?p=1712 "Spring Boot 整合 Mybatis 实现 Druid 多数据源详解") 

#### e. 『 其他篇 』
- springboot-dubbo-server  
- springboot-dubbo-client  
Dubbo 服务提供者工程和 Dubbo 服务消费者工程  
 [《Springboot 整合 Dubbo/ZooKeeper 详解 SOA 案例》](http://www.bysocket.com/?p=1681 "Springboot 整合 Dubbo/ZooKeeper 详解 SOA 案例") 
 [《Spring Boot 中如何使用 Dubbo Activate 扩展点》](http://www.bysocket.com/?p=1782 "Spring Boot 中如何使用 Dubbo Activate 扩展点") 
- springboot-validation-over-json  
 [《Spring Boot HTTP over JSON 的错误码异常处理》](http://www.bysocket.com/?p=1692 "Spring Boot HTTP over JSON 的错误码异常处理") 


## 二、项目 Quick Start 快速开发指南
#### a. 基本环境配置
在 MySQL 中，创建数据库 springbootdb：
````
CREATE DATABASE springbootdb;
````
创建表 city 城市 (因为我喜欢徒步)
````
DROP TABLE IF EXISTS  `city`;
CREATE TABLE `city` (
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT COMMENT '城市编号',
  `province_id` int(10) unsigned  NOT NULL COMMENT '省份编号',
  `city_name` varchar(25) DEFAULT NULL COMMENT '城市名称',
  `description` varchar(25) DEFAULT NULL COMMENT '描述',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8;
````
插入基础数据
````
INSERT city VALUES (1 ,1,'温岭市','BYSocket 的家在温岭。');
````
  
### 《 springboot-mybatis 工程 Quick Start 》
首先 check 基本环境配置完成，创建好数据库和表。

#### 1. 修改数据库配置
配置文件地址：springboot-mybatis/src/main/resources/application.properties
修改相应的数据源配置，比如账号、密码等

#### 2. 编译工程
在项目根目录 `springboot-learning-example`，运行 maven 指令：
````
mvn clean install
````
#### 3. 运行工程
右键运行工程包中 `org.spring.springboot.Application` Spring Boot 应用启动类的 main 函数，然后在浏览器访问：
`````
http://localhost:8080/api/city?cityName=温岭市
`````
可以看到返回的 JSON 结果：
````
{
    "id": 1,
    "provinceId": 1,
    "cityName": "温岭市",
    "description": "我的家在温岭。"
}
````


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)