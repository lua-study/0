# wetech-edas-app

SSM整合阿里云EDAS服务示例工程，使用前请先访问[https://help.aliyun.com/document_detail/44158.html ](https://help.aliyun.com/document_detail/44158.html ) 熟悉EDAS开发指南！

## 组织结构

```
wetech-edas-app
├── wetech-edas-app-api -- 提供接口定义
├── wetech-edas-app-common -- SSM框架公共模块
├── wetech-edas-app-service -- 服务提供者应用
└── wetech-edas-app-web -- 消费者应用
```

## 模块介绍

1. wetech-edas-app-parent

> 是所有子模块的父工程，同时也是项目聚合器，以及版本申明管理，无实质代码

2. wetech-edas-app-common

> 公共模块，可以放一些通用工具类

3. wetech-edas-app-api

> 提供接口定义

4. wetech-edas-app-service

> 服务提供者应用

5. wetech-edas-app-web

> 消费者应用

## 技术选型

### 后端技术

技术 | 名称 | 版本 | 官网
----|------|----|----
Spring Framework | IOC容器 | 4.3.5.RELEASE | [http://projects.spring.io/spring-framework/](http://projects.spring.io/spring-framework/)
SpringMVC | MVC框架 | 4.3.5.RELEASE |  [http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#mvc](http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#mvc)
MyBatis | ORM框架 | 3.2.1 |  [http://www.mybatis.org/mybatis-3/zh/index.html](http://www.mybatis.org/mybatis-3/zh/index.html)
Maven | 项目构建管理 | 4.0.0 |  [http://maven.apache.org](http://maven.apache.org/)
Logback | 日志组件 | 1.1.3 |  [https://logback.qos.ch](https://logback.qos.ch/)
Druid | 数据库连接池 | 0.2.23 |  [https://github.com/alibaba/druid](https://github.com/alibaba/druid)
EDAS | 阿里云EDAS | 1.5.4 |  [https://www.aliyun.com/product/edas/](https://www.aliyun.com/product/edas/)

## 软件需求

- JDK1.8+
- MySQL5.6+
- Tomcat7.0+/jetty9.0+
- Maven3.0+

## 本地部署

- 通过git下载源码
- 创建数据库wetech_edas_app，数据库编码为UTF-8
- 执行docs/sql/init.sql文件，初始化数据
- 修改wetech-edas-app-service模块下config.properties文件，更改MySQL账号和密码
- 在项目根模块执行【mvn clean package】
- 将wetech-edas-app-service模块（服务提供者）和wetech-edas-app-web模块（服务调用者）放入ali-tomcat启动！
- 访问轻量配置中心查看服务可用性
- 访问http://localhost:8888/wetech-edas-app-web 测试服务调用

## 预览图

> 启动工程

![](docs/preview/1.gif)

> 轻量配置中心

![](docs/preview/2.gif)

> 测试服务调用

![](docs/preview/3.gif)

## 许可证

Wetech-edas-app 使用 MIT 许可证发布，用户可以自由使用、复制、修改、合并、出版发行、散布、再授权及贩售wetech-edas-app 及其副本。

[查看许可证](LICENSE "LICENSE")

## 获取源码

 [https://github.com/cjbi/wetech-edas-app](https://github.com/cjbi/wetech-admin "github")

 [https://gitee.com/cjbi/wetech-edas-app](https://gitee.com/cjbi/wetech-admin "gitee")



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)