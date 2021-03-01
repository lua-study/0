# Config 服务配置中心

Config Server，用于集中管理端服务配置

## 部署

需要连接外网，来从git拉取服务配置

需要配置git用户和密码

### 使用说明

1、配置本地HOST，指向 Eureka Server

2、启动服务

### 客户端说明

1、添加POM依赖

	 
		 org.springframework.cloud 
		 spring-cloud-starter-config 
	 

2、配置 bootstrap.properties

	# Git分支
	spring.cloud.config.label=master
	# Config Server
	spring.cloud.config.fail-fast=true
	spring.cloud.config.discovery.enabled=true 
	spring.cloud.config.discovery.service-id=demoncat-config-server

3、在GIT的配置管理项目上，创建应用的目录，配置application.properties和application-{profile}.properties

4、配置刷新

	1.使用 @RefreshScope 注解读取配置的Bean
	
	2.更新GIT配置
	
	3.刷新配置：curl -XPOST http://localhost:8000/actuator/refresh



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)