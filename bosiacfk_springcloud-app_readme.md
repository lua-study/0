# springcloud-app

## 系统介绍

- springcloud-app 是J2EE集群分布式基础开发平台，技术栈包括：springcloud，eureka，zuul，ribbon，feign，config，bus、hystrix，turbine，zipkin，MyBatis、Shiro、redis，JWT，swagger，lombok，业务模块包括：用户管理，角色管理、权限管理，字典管理。
## 核心流程概要

- 用户->nginx->HTML->ZUUL(路由中心)->eureka(注册中心)->具体服务（必须引入SHIRO权限）->eureka(注册中心)->核心服务（SHIRO权限认证授权）->REDIS/MYSQL
- 外部通信,方式HTTP,协议HTTP,权限SHIRO,注意ZUUL过滤器屏蔽内部接口（防止内部接口对外暴露）
- 内部通信,方式Feign,协议HTTP,权限eureka账号密码,注意SHIRO要开放内部接口

## 业务功能

- 1.用户管理：用户增删改查与角色关系
- 2.角色管理：角色增删改查与权限关系
- 3.菜单管理：菜单增删改查（树形结构）
- 4.字典管理：字典增删改查

## 技术栈

- springcloud 整合
- eureka 注册中心
- zuul 路由中心
- ribbon 通信
- feign 注解通信
- config 配置中心
- bus 实时配置中心功能
- hystrix 断路器监控
- turbine 断路器监控聚合
- zipkin 链路监控
- springBoot ioc，aop
- mybatis ORM  
- shiro 会话
- redis shiro缓存
- 连接池 druid
- JWT 会话
- swagger api
- lombok 代码优化


## 部署

- 1.导入数据库脚本springcloud.sql
- 2.安装nginx配置参考nginx.txt
- 3.启动redis
- 4.启动rabbitmq
- 5.启动注册中心springcloud-app-eureka 访问端口1001
- 6.启动配置中心springcloud-app-config
- 7.启动路由中心springcloud-app-zuul
- 8.启动服务中心springcloud-app-system
- 9.启动调度中心springcloud-app-schedule
- 10.启动断路器监控汇总springcloud-app-turbine 访问端口8989
- 11.启动断路器监控springcloud-app-hystrix 访问端口1301/hystrix
- 12.启动链路追踪springcloud-app-zipkin 访问端口9411
- 13.下载https://gitee.com/vmaps/app-ui 更改对应include.js
- 14.启动nginx 访问端口80/html

## qq交流群

- 74745979

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)