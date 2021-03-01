# 欢迎查看ms项目说明

## 项目简介
  `micro-fast`使用mybatis,spring系列框架作为基础，致力于打造一套中小企业系统解决方案.项目中对常用技术进行封装便于复用以及提高
开发效率，还提供了一个借助springcloud实现的一个分布式项目．这不仅仅是一个springCloud项目，项目中提供了诸多可复用的基础模块，也
许有你想要，可以方便的引入到自己的项目中快速集成。项目的思想是不写一次性代码，所有基础模块都可以在其他项目中通过简单配置快速集成。
如果你觉得本项目对你有帮助，欢迎star;如果你想更深入的了解本项目欢迎加入`qq`交流群`640791460`，如果你乐于分享，欢迎加入本项目的开
发中来，每一个点点滴滴提交都是对项目发展的巨大贡献。
## 参与进来
### `qq`交流群`640791460` 
### 本地部署文档详见[ms开发文档](./all/ms/deploy.md)
## 项目概览
- `mybatis-generator-extend-maven-plugin`模块是便于快速根据条件生成mybatis-generator-plugin配置文件的maven扩展插件，基本增
删改查、按条件分页查询`dao` `servcie` `controller`层利用了词向量、卷积神经网络、使用人工智能技术进行代码语意分析(好吧，我吹不
下去了)自动生成，自动生成70%代码，降低开发中重复性耗时工作,此插件可在其他项目中单独使用。
- 合理的拆分，拥有众多的可复用模块，开箱即用
- 高可用注册中心
- 高可用配置配置管理中心，通过`rabbitmq`支持配置刷新
- 服务网关
- 监控
- 基于oauth2，jwt的认证中心。ouath2服务提供商
- 用户中心
- 权限管理中心
- 拥有配套的后台管理界面[ms-admin-ui](https://gitee.com/kklt1996/ms-admin-ui)
- 支持docker容器部署
- 使用flume收集系统日志，便于日志分析
- 热点数据使用redis缓存
- 多数据源支持
- 完善的项目使用文档
- 用心的开发者
## 整体技术选型
技术名称 | 版本 | 技术使用 | 地址
------- | ------- |------- |-------
jdk | 1.8.0_144 | java开发环境 | [官网](http://www.oracle.com/technetwork/java/javase/downloads/java-archive-javase8-2177648.html)
mysql | 5.7 | 关系型数据库 | [官网](https://www.mysql.com/downloads/)
redis | 3.0.6 | 缓存数据库 | [官网](https://redis.io/download),[中文站](http://www.redis.cn/)
maven | 3.3.9 | 项目管理工具 | [官网](http://maven.apache.org/)
docker | 1.12.6 | 容器技术 | [官网](https://www.docker.com/)
flume|1.8.0| 系统日志收集|[官网](http://flume.apache.org)
rabbitmq|3.7.2| 消息总线|[官网](http://www.rabbitmq.com/)
elasticsearch|6.1.2|日志分析引擎|[官网](https://www.elastic.co/products/elasticsearch)
fastdfs| 5.11 |分布式文件存储|[官网](https://github.com/happyfish100/fastdfs)
springBoot | 1.5.9.RELEASE | 微服务入门框架 | [官网](https://projects.spring.io/spring-boot/)
springCloud | Edgware.RELEASE | 微服务框架 | [官网](http://projects.spring.io/spring-cloud/),[中文文档](https://springcloud.cc/)
mybatis | 3.4.4 | 数据持久化框架 | [官网](http://www.mybatis.org/mybatis-3/zh/index.html)
mybatis-generator | 1.3.5 | mybatis代码生成 | [github地址](https://github.com/mybatis/generator)
mybatis-pagehelper | 4.1.0 | mybatis分页插件 | [github地址](https://github.com/pagehelper/Mybatis-PageHelper)
nodejs |v8.4.0 | web项目开发,静态资源http服务器 | [官网](https://nodejs.org/en/)
npm | 3.10.7 | nodejs模块管理工具 | [官网](https://www.npmjs.com/)
vuejs | 2.5.2 | 前端视图框架| [官网](https://cn.vuejs.org/v2/guide/installation.html)
vue-router | 3.0.1 | 前端路由 | [官网](https://router.vuejs.org/zh-cn/)
vuex| 3.0.1 | 单向数据流 |  [官网](https://vuex.vuejs.org/zh-cn/)
axios| 0.17.1 | ajax请求框架 | [github地址](https://github.com/axios/axios)
elemnet-ui | 2.0.8 | 前端视图库 | [官网](http://element-cn.eleme.io/#/zh-CN/component/installation)
swagger | 2.6.1 | 文档生成 | [官网](https://swagger.io/)
lombok | 1.16.6.1|代码工具|[官网](https://projectlombok.org/features/all)
ratelimit|1.4.0|网关限流|[github](https://github.com/marcosbarbero/spring-cloud-zuul-ratelimit)
## 开发界面
![](./all/ms/idea.png)
## 模块介绍
``` lua
micro-fast
├── boot-starter -- 借助spring boot自建快速启动项目
|    ├── boot-starter-common -- ms系统的通用模块
|    ├── boot-starter-elasticsearch -- elasticsearch快速启用
|    ├── boot-starter-fastdfs-client -- fastdfs客户端
|    ├── boot-starter-maven-plugin -- maven的一系列插件
|    |    └── mybatis-generator-extend-maven-plugin -- 用于简化mybatis-generator生成代码的流程
|    ├── boot-starter-security-oauth -- 权限认证　
|    ├── boot-starter-ssm  -- ssm公共配置
|    └── boot-starter-util -- 常用工具
├── ms -- 分布式系统
|    ├── config-server -- 配置管理中心
|    ├── gateway  -- 服务网关
|    ├── monitor-turbine-- 请求监控
|    ├── monitor-zipkin-- 服务调用监控
|    ├── oauth -- 认证中心
|    ├── register-center1 -- 高可用注册中心
|    ├── register-center2 -- 高可用注册中心
|    ├── ucenter  -- 用户中心
|    └── upms  -- 权限管理系统
├── ms-web -- 业务系统界面搭建示例
└── all-in-one -- ms系统的集中式实现
```

## ms分布式系统架构图
![](./all/ms/架构图.png)
## 登录
![](./all/ms/login.png)
## 首页
![](./all/ms/index.png)
## 系统管理
![](./all/ms/system.png)
## 组织管理
![](./all/ms/organization.png)
## 用户管理
![](./all/ms/Upmsuser.png)
## 权限管理
![](./all/ms/permission.png)
## 角色管理
![](./all/ms/role.png)
## 服务简单信息查看
![](./all/ms/serviceInfo.png)
## 服务详细信息查看,服务状态管理
![](./all/ms/serviceManage.png)
## swagger系统文档聚合
![](./all/ms/swagger.png)
## 监控中心
![](./all/ms/monitor.png)
## 服务调用追踪
![](./all/ms/zipkin.png)
## 热门服务实时排行
![](./all/ms/serviceRank.png)
## 各模块的详细介绍
- `boot-starter`项目介绍[README.md](boot-starter/README.md)
- `ms`项目介绍[README.md](ms/README.md)
- `ms-web`项目介绍[README.md](ms-web/README.md)
- `all-in-one`项目介绍[README.md](all-in-one/README.md)
 



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)