**项目说明** 
- 采用前后端分离开发模式，此为后端程序，前后端通过restful api方式进行交互数据，通过请求头携带token进行跨请求会话。
- 采用mevan分模块结构，主要是为了把数据处理/业务逻辑代码抽取出来作为通用模块，方便项目后期扩展，同时便于规范编码。
  
 
 

**项目结构** 
```
platform
│
├─doc   文档目录
│  └─db 项目SQL语句
│
├─module-service 数据处理/业务逻辑模块
│  ├─common 通用类（常量、全局高频类）
│  │   ├─aspect 切面类（日志、redis等）
│  │   ├─exception 自定义异常
│  │   ├─validator 后台校验
│  │   └─xss XSS过滤
│  ├─resources/mapper SQL对应的XML文件
│  ├─config springboot 配置类
│  ├─dao 数据处理类（数据获取与存储处理）
│  ├─dto dao与service间数据交互封装类
│  ├─entity 实体类
│  ├─enums 枚举类
│  ├─oauth2 权限处理类
│  ├─redis redis数据处理类
│  ├─service 业务逻辑处理类
│  └─util 工具类                                                 
│ 
│ 
├─module-web 网页端交互模块
│  ├─run
│  │  ├─WebApplication 启动类
│  ├─common 通用类（常量、全局高频类）
│  │   ├─annotation 自定义注解类
│  │   ├─aspect 切面类（日志、redis等）
│  │   ├─hander 请求处理器
│  │   └─xss XSS过滤
│  ├─config springboot 配置类
│  ├─controller 控制类
│  ├─form 请求参数封装类
│  ├─util 工具类
│  ├─vo controller返回数据封装类
│  └─resources/application.properties 主配置文件
│  
├──module-job 定时任务模块
│  ├─run
│  │  ├─TaskAppliction 启动类
│  ├─job 任务处理类
│  └─resources/application.properties 主配置文件
│
├──module-aif 微服务集成模块 
│  ├─aif 通用类
│  ├─config springboot 配置类  
│  ├─service 服务类
│  └─util 工具类
│

```
  


**技术选型：** 
- 核心框架：Spring Boot 2.0
- 视图框架：Spring MVC 5.0
- 持久层框架：MyBatis 3.3
- 定时器：Spring task
- 数据库连接池：Druid 1.0
- 日志管理：SLF4J 1.7、Log4j
  


 **后端部署**
- 通过git下载源码
- 创建数据库xxx，数据库编码为UTF-8
- 执行db/xxx.sql文件，初始化数据
- 修改application-dev.xml，更新MySQL账号和密码
- Eclipse、IDEA运行module-web/WebApplication.java，则可启动web端交互程序
- Eclipse、IDEA运行module-job/JobApplication.java，则可启动定时任务程序
- Swagger路径：http://localhost:8080/swagger/index.html，登录接口：账号admin,密码admin

  


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)