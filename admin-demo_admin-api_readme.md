## 项目说明
> admin-api是一个轻量级的，前后端分离的Java快速开发平台，能快速开发项目并交付【接私活利器】

**具有如下特点** 
- 灵活的权限控制，可控制到页面或按钮，满足绝大部分的权限需求
- 页面交互使用 Vue2.x，极大的提高了开发效率
- 完善的代码生成机制，可在线生成 entity、xml、dao、sql 代码，减少70%以上的开发任务
- 引入 quartz 定时任务，可动态完成任务的添加、修改、删除、暂停、恢复及日志查看等功能
- 引入 API 模板，根据 token 作为登录令牌，极大的方便了 APP 接口开发
- 引入 Swagger 文档支持，方便编写 API 接口文档
- 引入路由机制，刷新页面会停留在当前页


## 项目说明

```
admin-api
.
└── io
    └── adminboot
        ├── config              Spring Boot config
        ├── contrant            系统级常量
        ├── domain              领域对象
        │   ├── dto
        │   ├── form
        │   ├── param
        │   └── vo
        ├── entity              实体类（有mybatis生成，与表一一对应）
        ├── exception           Exception 定义
        ├── manager             Manager 层：与第三方交互，与 DAO 层交互，封装公共业务
        ├── repository          DAO 层：由 mabatis 自动生成
        │   └── extend          DAO 扩展：存放自定义 SQL，避免 mybatis 自动生成覆盖 
        ├── service             业务逻辑层
        │   └── impl
        ├── system              系统相关
        │   ├── annotation
        │   ├── aspect
        │   ├── cache
        │   ├── interceptor
        │   ├── job
        │   │   └── task
        │   ├── oauth2
        │   ├── oss
        │   ├── redis
        │   ├── resolver
        │   ├── validator
        │   │   └── group
        │   └── xss
        ├── utils               工具类
        └── web                 接口层

```

## 技术选型
- 核心框架：Spring Boot 2.0
- 安全框架：Apache Shiro 1.3
- 持久层框架：MyBatis 3.3
- 定时器：Quartz 2.3
- 页面交互：Vue2.x + Element UI


 ## 本地开发
- 通过git下载源码
- 创建数据库`admin_boot`，数据库编码为`utf8mb4`
- 执行db/admin_boot.sql文件，初始化数据
- 修改application-dev.properties，更新MySQL账号和密码
- Eclipse、IDEA 运行 Application.java，则可启动项目
- 项目访问路径：http://localhost:8080/
- 账号密码：admin/123456
- Swagger路径：http://localhost:8080/swagger-ui.html

## 部署

1. 打包

```
mvn -Dmaven.test.skip=true clean package -Ptest
```
> -Ptest 指定了配置文件的环境为 test 环境，在 applicetion-{profle}.properties 和 pom.xml 可以看到不同环境的特有配置文件   
> 其他可选环境：   
> -Pdev 开发   
> -Pprod 开发   


2. 运行

```
nohup java -jar target/admin-api.jar > log.out &
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)