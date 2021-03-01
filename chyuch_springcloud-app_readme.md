# springcloud-app

## 系统介绍

- springcloud-app 是J2EE集群分布式基础开发平台，架构设计包括（分布式，分布式事务，高可用集群，缓存集群，会话集群，动静分离），技术栈包括（springCloud、MyBatis、Shiro、redis、easyui），业务模块包括：用户管理，角色管理、权限管理，字典管理。

## 核心流程概要

- 用户->nginx->HTML->ZUUL(路由中心)->eureka(注册中心)->具体服务（必须引入SHIRO权限）->eureka(注册中心)->核心服务（SHIRO权限认证授权）->REDIS/MYSQL
- 外部通信,方式HTTP,协议HTTP,权限SHIRO,注意ZUUL过滤器屏蔽内部接口（防止内部接口对外暴露）
- 内部通信,方式Feign,协议HTTP,权限eureka账号密码,注意SHIRO要开放内部接口

## 业务功能

- 1.用户管理：用户是系统操作者，该功能主要完成系统用户配置。
- 2.角色管理：角色菜单权限分配。
- 3.菜单管理：配置系统菜单，操作权限，按钮权限标识等。
- 4.字典管理：对系统中经常使用的一些较为固定的数据进行维护，如：是否、男女、类别、级别等。

## 技术栈

- 分布式中间件 springCloud
- 注册中心 springCloud-eureka
- 路由中心 springCloud-zuul
- 配置中心 springCloud-config
- 核心 springBoot 
- MVC springmvc 
- ORM mybatis 
- 会话 shiro 
- 验证 hibernate-validation
- 缓存 redis 
- mybatis二级缓存集群 mybatis-redis
- shiro会话集群，缓存集群 shiro-redis
- 连接池 druid
- 页面UI easyui
- 构建 maven
- 容器 tomcat
- 数据库 mysql

## 部署

- 1.导入数据库脚本springcloud.sql
- 2.安装nginx配置参考nginx.txt
- 3.启动redis
- 4.启动注册中心springcloud-app-eureka位置com.wangsong.springcloudAppEurekaApplication
- 5.启动配置中心springcloud-app-config位置com.wangsong.springcloudAppConfigApplication
- 6.启动路由中心springcloud-app-zuul位置com.wangsong.springcloudAppZuulApplication
- 7.启动服务中心springcloud-app-service位置com.wangsong.springcloudAppServiceApplication
- 8.访问nginx端口/springcloud-app-html

## 预览

![](http://git.oschina.net/uploads/images/2016/1116/164543_5571d631_420150.png "登录")
![](http://git.oschina.net/uploads/images/2016/1116/164618_99cd6105_420150.png "角色权限树")
![](http://git.oschina.net/uploads/images/2016/1116/164633_6dd5c2e9_420150.png "权限右键操作树")

## qq交流群

- 74745979

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)