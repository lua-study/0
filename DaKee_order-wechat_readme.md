

**项目结构** 
```
renren-fast
├─doc  项目SQL语句
│
├─common 公共模块
│  ├─aspect 系统日志
│  ├─exception 异常处理
│  ├─validator 后台校验
│  └─xss XSS过滤
│ 
├─config 配置信息
│ 
├─modules 功能模块
│  ├─api API接口模块(APP调用)
│  ├─job 定时任务模块
│  ├─oss 文件服务模块
│  └─sys 权限模块
│ 
├─RenrenApplication 项目启动类
│  
├──resources 
│  ├─mapper SQL对应的XML文件
│  ├─static 第三方库、插件等静态资源
│  └─views  项目静态页面

```



**技术选型：** 
- 核心框架：Spring Boot 1.5
- 安全框架：Apache Shiro 1.3
- 视图框架：Spring MVC 4.3
- 持久层框架：MyBatis 3.3
- 定时器：Quartz 2.3
- 数据库连接池：Druid 1.0
- 日志管理：SLF4J 1.7、Log4j
- 页面交互：Vue2.x 
  


 **本地部署**
- 通过git下载源码
- 创建数据库renren_fast，数据库编码为UTF-8
- 执行doc/db.sql文件，初始化数据
- 修改application-dev.yml，更新MySQL账号和密码
- Eclipse、IDEA运行RenrenApplication.java，则可启动项目
- 项目访问路径：http://localhost
- 账号密码：admin/admin



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)