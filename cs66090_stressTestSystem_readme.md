**项目说明** 
- 本项目基于renren-fast Java开发平台开发，内核基于Jmeter-Api和Jmeter脚本实现在线性能压测。是在zyanycall/stressTestPlatform的开源项目基础上做了大量的改造，后续还会继续追加新功能。
  
 
**具有如下特点** 
- 友好的代码结构及注释，便于阅读及二次开发
- 实现前后端分离，通过token进行数据交互，前端再也不用关注后端技术
- 灵活的权限控制，可控制到页面或按钮，满足绝大部分的权限需求
- 页面交互使用Vue2.x，极大的提高了开发效率
- 完善的代码生成机制，可在线生成entity、xml、dao、service、html、js、sql代码，减少70%以上的开发任务
- 引入quartz定时任务，可动态完成任务的添加、修改、删除、暂停、恢复及日志查看等功能
- 引入API模板，根据token作为登录令牌，极大的方便了APP接口开发
- 引入Hibernate Validator校验框架，轻松实现后端校验
- 引入云存储服务，已支持：七牛云、阿里云、腾讯云等
- 引入swagger文档支持，方便编写API接口文档
- 引入路由机制，刷新页面会停留在当前页
- 引入最新版本Jmeter-Api，支持分布式压测，测试报告生成及在线查看下载。
- 引入Echarts，支持在线观测性能压测结果。
  

**项目结构** 
```
renren-fast
├─doc  项目SQL语句
│
│─lib  项目引用jar包
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
│  ├─sys 权限模块
│  └─test 测试模块
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
- 前端监控：ECharts 3.8
- 压测内核：Apache JMeter 5.1.1
- 远程执行命令：Ganymed build210
- 批量上传组件：bootstrap-fileinput v4.5.2
- JVM内部缓存：Guava 18.0
  

 **本地部署**
- 通过git下载源码
- 创建数据库renren_fast，数据库编码为UTF-8
- 执行doc/db.sql文件，初始化数据
- 修改application-dev.yml，更新MySQL账号和密码
  （或者application.yml配置h2，调用application-h2.yml配置，连接h2数据库）
- 修改MySQL中sys_config表中Jmeter专属配置项，更新为本地地址
- Eclipse、IDEA运行RenrenApplication.java，则可启动项目
- 项目访问路径：http://localhost:8080/
- 账号密码：admin/admin
- Swagger路径：http://localhost:8080/swagger/index.html

**jar部署**
- 修改application.yml，修改profiles，指定执行环境如线下环境pro
- 修改application-pro.yml，更新线下环境的MySQL账号和密码
- 通过maven命令打包jar包：mvn clean package -f pom.xml
- 将target目录下，打包好的jar包通过java -jar renren-fast.jar 调用
- 也可以将打好的jar包通过Dockerfile build到Docker镜像中
- 项目访问路径，如：http://线下环境ip:8080/renren-fast
- 账号密码：admin/admin

 **tomcat部署**
- 修改application.yml，修改profiles，指定执行环境如线下环境pro
- 修改application-pro.yml，更新线下环境的MySQL账号和密码
- 通过maven命令打包war包：mvn clean package -f pom-war.xml
- 将target目录下，打包好的war包保存到tomcat的webapps目录下
- 通过tomcat的bin目录下的startup命令，启动tomcat
- 访问tomcat路径，如：http://线下环境ip:8080
- 账号密码：admin/admin

 **配置参数**
 性能测试配置(全在数据库保存配置参数：系统管理->参数管理)
 - Jmeter主节点路径，默认测试报告生成使用 jmeterHome: D:\software\apache-jmeter-4.0
 - 存放用例的总目录，里面会细分文件存放用例及用例文件，用例保存路径 casePath: D:\E\stressTestCases
 - Jmeter节点机需要在/etc/bashrc中配置JAVA_HOME，同时source /etc/bashrc生效
 - 
   ：如果配置了Jmeter脚本启动，则额外开启Jmeter进程运行测试用例脚本及分布式程序。
   ：分布式程序可以取消ssl校验（jmeter4及以上版本要求）。
   ：同时可以配置支持Jmeter+InfluxDB+Grafana的实时监控。
   ：支持自带的ECharts实时监控。
 - 如果没有配置Jmeter脚本启动，则使用web本身自带的Jmeter功能。  
   ：MASTER_JMETER_USE_SCRIPT_KEY 默认是false，即使用web程序进程来启动Jmeter-master程序。
 - 默认支持以进程方式生成测试报告，也支持以脚本方式生成测试报告
   ：MASTER_JMETER_GENERATE_REPORT_KEY 为true表示由进程生成测试报告，支持并发生成
 - SCRIPT_SCHEDULER_DURATION_KEY 为true 开启脚本限时执行，以免脚本忘记停止在后台一直压测
 - JMETER_THREADGROUP_SET_KEY 默认为false
   ：JMETER_THREADGROUP_SET_KEY为true则开启线程组管理功能，导入脚本时会往线程组配置库中也导入一份
 
 **注意事项：**
部署时请确保平台jmeter引擎版本、主节点版本、分布式节点版本保持一致（避免不同版本配置文件或生成的报告数据差异导致一些异常）
  

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)