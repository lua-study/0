# 叮当科技 2.0系统开发框架说明
优爆名品服装零售业务平台项目代码，基于Sping Clound、Spring Boot、Mybatis、Mysql等应用技术体系以API接口方式提供包括优爆的商品信息、门店管理、库存管理、会员管理、营销活动、系统用户、商城等零售业务应用服务。

ddyx-2.0版本系统基于分布式微服务开发平台，采用springboot构建，采用maven多模块设计，集成springcloud各核心组件。
技术栈已使用包括：springboot，springcloud，config，eureka，gateway，feign，ribbon，
hystrix，turbine，mybatis，mybatis-plus，redis，swagger，actuator等。
陆续整合集成包括：bus，zipkin，oauth2，security，sso，kafka，elasticsearch。

## 后端框架

| 框架                       | 说明                  |            版本            |
| -------------------------- | --------------------- | ------------------------ |
| [SpringBoot]               | 基础开发框架           |         2.1.6.RELEASE     |
| [SpringCloud]              | 分布式框架             |        Greenwich.RELEASE  |
| [MySQL]                    | 数据库服务器           |         5.7               |
| [Druid]                    | 数据库连接池、监控组件  |         1.1.16             |
| [MyBatis]                  | 数据持久层框架         |         3.5.1              |
| [MyBatis-Plus]             | Mybatis 增强组件      |        3.1.2               |
| [Eureka]                   | 服务注册发现           |       2.1.2                |
| [Gateway]                  | 服务网关路由           |       2.1.2                |
| [Feign]                    | 声明式远程调用通信      |         2.1.2              |
| [Config]                   | 统一配置中心           |       2.1.2                | 
| [Hystrix]                  | 断路器服务及监控        |       2.1.2               |
| [Turbine]                  | 断路器聚合监控          |       2.1.2               |
| [Ribbon]                   | 客户端负载均衡通信      |        2.1.2              |
| [Actuator]                 | 微服务应用可视化监控     |        2.1.2              |
| [Redis]                    | 缓存数据库             |       2.9.1               |
| [Orika]                    | Javabean封装组件      |       1.5.4                |
| [Springfox-swagger2]       | API文档、接口调试      |       2.9.2                |
| [Swagger-bootstrap-ui]     | Swagger 增强UI实现    |       1.9.3                |
| [Java-Validation]          | 数据验证组件           |       4.2                 |
| [Hibernate-Validation]     | 后台参数校验注解       |       6.0.17.Final         |
| [PageHelper]               | 分页插件              |        1.2.12              |
| [logback]                  | 日志框架              |        1.2.3               |



## 模块结构：

- ddyx-common  公共组件，包含基础工具包，依赖信息、数据源配置，异常处理等核心框架；
- ddyx-generator 代码生成器，采用mybatis-plus组件；
- ddyx-config  系统统一配置中心（默认使用本地配置信息）；
- ddyx-eureka  服务注册中心；
- ddyx-gateway  系统网关路由，swagger文档聚合；
- ddyx-hystrix  服务断路器监控；
- ddyx-turbine  服务断路器聚合监控；
- ddyx-monitor  服务可视化监控模块；
- ddyx-service-user  用户服务父模块
- ddyx-service-user-api  用户服务子模块，定义远程调用接口、实体类、VO对象；
- ddyx-service-user-app  用户服务子模块，处理核心业务逻辑及数据访问；
- ddyx-service-product  商品服务父模块
- ddyx-service-product-api  商品服务子模块，定义远程调用接口、实体类、VO对象；
- ddyx-service-product-app  商品服务子模块，处理核心业务逻辑及数据访问；


### 模块包体说明

```lua
ddyx
├── ddyx-common -- 系统公共模块 
     └── base -- 基础组件定义
     └── framework -- 核心组件配置
     └── utils -- 基本工具包
├── ddyx-generator -- 代码生成器
├── ddyx-config -- 统一配置中心[8888]
├── ddyx-eureka -- 服务注册与发现[8761]
├── ddyx-gateway -- 服务网关路由[9001]
├── ddyx-hystrix -- 服务断路器监控[8605]
├── ddyx-turbine -- 服务断路器聚合监控[9605]
├── ddyx-monitor -- 服务可视化监控[7008]
└── ddyx-service-user -- 用户服务模块
     └── ddyx-service-user-api -- 子模块，定义远程调用接口、实体类、VO对象
            └── entity -- 数据库映射实体类
            └── feign -- 远程调用接口定义
            └── vo -- 封装数据传递对象
     └── ddyx-service-user-app -- 子模块，处理核心业务逻辑及数据访问
            └── config -- 配置
            └── system -- 业务核心开发模块
                  └── controller -- restful接口
                  └── mapper -- 数据访问接口层
                  └── service -- 业务逻辑接口定义
                         └── impl -- 业务逻辑接口实现
└── ddyx-service-product  -- 商品服务模块（包结构与用户模块一致）
     └── ddyx-service-product-api -- 子模块，定义远程调用接口、实体类、VO对象
     └── ddyx-service-product-app -- 子模块，处理核心业务逻辑及数据访问
	 
```


## 开发说明：

- 业务模块分开api、app两个子模块，主要考虑底层数据互通及远程接口调用都需要互相依赖api；

- 建议service服务层接口定义采用VO对象做数据传输；VO对象需要自行创建编写，代码生成器可以创建实体类；

- 整合多数据源，service层可直接使用注解进行数据源切换，具体看user模块使用；

- 新系统舍弃了web层RequestForm、ResponseForm对象的使用，建议采用restful形式提供接口定义及业务对象数据的输入输出；

- controller层接收json数据建议采用VO对象封装，可以较好的搭配swagger插件进行接口调试，swagger插件注解添加在VO对象；

- 系统集成了JavaBean映射工具orika，可以对VO对象、数据库entity实体类进行数据转换； 

- 集成了验证框架javax.validation、hibernate-validator  两种验证框架并用；验证注解全部添加到vo对象及controller层;

- 系统启动建议使用根路径XxxApplication程序主入口启动方式运行，也可以部署外部tomcat、jetty等容器；

- 业务实现可以参考用户模块user的处理，包括swagger注解、数据验证注解、数据源切换注解等；

- 整合三方工具包时，建议依赖比较新的稳定的版本，在整合过程中发现很多工具包依赖还是比较老旧的版本，需要特殊处理；

## 启动部署

- 1.启动注册中心 ddyx-eureka 端口8761
- 2.启动用户服务 ddyx-service-user-app 端口8080
- 3.启动商品服务 ddyx-service-product-app 端口8081
- 4.启动网关路由 ddyx-gateway 端口9001
- 5.启动断路器监控 ddyx-hystrix 端口8605(不是必须，需要查看监控可启动)
- 6.启动断路器聚合监控 ddyx-turbine 端口9605(不是必须，需要查看监控可启动)
- 7.启动服务可视化监控 ddyx-monitor 端口7008(不是必须，需要查看监控可启动)

## 访问：
swagger接口调试(两种UI风格都可以使用)：
- 接口调试地址（bootstrap-UI）： http://localhost:9001/doc.html
- 接口调试地址（默认UI）：       http://localhost:9001/swagger-ui.html

druid数据库连接池：
- 用户模块监控地址：http://localhost:8080/druid/login.html
- 商品模块监控地址：http://localhost:8081/druid/login.html
- 账号： admin/druidadmin (DruidConfig中定义)

eureka服务注册中心：
- 服务注册中心：    http://localhost:8761/

hystrix断路器监控：
- 断路器监控：  http://localhost:8605/hystrix
- 断路器聚合监控：  http://localhost:9605/turbine

springboot-admin监控：
- 服务可视化监控：http://localhost:7008
- 账号:  username/password  (ddyx-monitor模块配置文件中定义)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)