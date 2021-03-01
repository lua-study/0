   

 
   
     
   
   
     
   
   
     
   
   
     
   
   
     
   
 



# Soraka

- 前后端完全分离，基于最新稳定版本`Spring Boot 2.0.6.RELEASE`
- 基于网关的统一权限管理，更高效更方便
- 基于`Spring Security OAuth`实现按钮级细粒度权限控制
- `Apache LICENSE 2.0`，完全开源

**交流QQ群：808305454**

# 项目介绍

Soraka一个基于Spring Cloud的基础微服务开发框架，有高效率，低封装的特点，非常适合学习和中小企业直接作为开发框架使用。

项目使用Maven进行管理，结构如下：

``` lua
soraka
├── soraka-admin -- 管理模块（端口：8003）
├── soraka-auth -- 权限模块（端口：8005）
├── soraka-common -- 共用模块
├── soraka-discovery -- 服务中心（端口：8001）
├── soraka-gateway -- ZUUL网关（端口：80）
├── soraka-weixin -- 微信模块（待实现 端口：8004）
```

前端项目链接：https://gitee.com/beiyoufx/soraka-view

- 用户管理：完整的用户管理授权体系
- 部门管理：配置系统组织机构，树结构展现，可随意调整上下级
- 菜单管理：配置系统菜单，操作权限，按钮权限标识，图标等
- 角色管理：角色菜单权限分配，最新的基于资源的权限控制（new RBAC）

## 软件架构

#### 后端技术选型

| 名称                  | 版本           | 说明         | 官网                                                         |
| --------------------- | -------------- | ------------ | ------------------------------------------------------------ |
| JDK                   | 1.8.0_161      | 运行环境     | https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html |
| Maven                 | 3.5.2          | 项目构建管理 | http://maven.apache.org                                      |
| Spring-boot           | 2.0.6.RELEASE1 | 微服务框架   | https://spring.io/projects/spring-boot                       |
| Spring-cloud          | Finchley.SR2   | 微服务框架   | https://spring.io/projects/spring-cloud                      |
| Eureka                |                | 服务发现     | https://github.com/spring-cloud/spring-cloud-netflix         |
| Zuul                  |                | 网关         | https://github.com/spring-cloud/spring-cloud-netflix         |
| MySQL                 | 5.7.16         | 数据库       | https://www.mysql.com/downloads/                             |
| MyBatis               |                | ORM框架      | http://blog.mybatis.org/                                     |
| Swagger2              | 2.7.0          | 文档         | http://swagger.io                                            |
| Spring Security OAuth |                | 安全框架     | https://spring.io/projects/spring-security-oauth             |
| Hystrix               |                | 熔断器       | https://github.com/spring-cloud/spring-cloud-netflix         |
| Ribbon                |                | 负载均衡     | https://github.com/spring-cloud/spring-cloud-netflix         |

#### 前端技术选型

| 名称               | 版本   | 说明         | 官网                                            |
| ------------------ | ------ | ------------ | ----------------------------------------------- |
| vue                | 2.5.17 | 前端框架     | https://github.com/vuejs/vue                    |
| element-ui         | 2.4.6  | UI组件       | https://element.eleme.io/#/                     |
| axios              | 0.18.0 | 网络组件     | https://github.com/axios/axios                  |
| nprogress          | 0.2.0  | 进度条       | https://github.com/rstacruz/nprogress           |
| vuex               | 3.0.1  | 前端状态管理 | https://github.com/vuejs/vuex                   |
| vue-router         | 3.0.1  | 前端路由     | https://github.com/vuejs/vue-router             |
| vue-admin-template |        | 后台模板     | https://github.com/PanJiaChen/vue-element-admin |

# 文档

1. [快速开始](soraka-wiki/快速开始.md)
2. [常见问题](soraka-wiki/常见问题.md)

# 截图

![Soraka演示](https://gitee.com/beiyoufx/soraka-view/raw/master/demo.gif)

# 关注我们

作者深知一个人的精力是有限的，如果觉得项目对您有帮助，欢迎fork和star，加入QQ群一起维护Soraka吧！
**交流QQ群：808305454**

公众号 **Java实践笔记**

分享Java开发中常用的技术，分享软件开发的新技术，分享业内相关的解决方案和互联网资讯，让自己做一个紧跟时代潮流的程序猿~

![img](https://gitee.com/beiyoufx/soraka-view/raw/master/javanoteqr.jpg)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)