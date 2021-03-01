﻿# 微服务脚手架 - 功能简介
参考说明使用教程文档（从列表的最后一篇往前面阅读即可）：https://www.52jingya.com/special/44.html
```
定时任务调度：目前可以根据quartz的时间规则配置调度微服务。提供了统一集中管理调度任务的前端操作的维护。

服务监控：发现系统的服务出现异常时，可以进行邮件通知。
项目发布：通过上传jar包到Monitor，然后通过Monitor直接将jar部署到服务器，同时提供回滚版本的功能。
API管理： 开发人员能查看系统所有的API接口，同时支持模拟调试系统的接口。
	也支持批量测试接口，可以在版本上线前批量测试应用接口。
原型管理：研发人员可以将原型截图上传到Monitor，将原型上所需要调用的接口都标记和列出调度接口的具体地址，方便前端对接和调试接口。
日志管理：将系统的关键日志记录到调用连跟踪，同时Monitor可以查看到具体日志信息和接口的调用链。
断路由：这里是作为案例，具体可参考biz-service-admin项目的TestServiceImpl.java文件。
Zuul网关：对外提供统一的接口服务，提供了签名认证的功能，支持微服务的轮询等调度方式。同时也做到了对系统接口的限流功能。
源码生成：研发人员可以在开发的时候，直接根据表名来生成基本的增删改查的源码从而提升研发效率。
	支持各种源码的模版配置，支持Mysql、Oracle等数据源的配置。
密钥管理：可以设置拥有项目接口所有权限和增加授权接口访问的权限的信息。
系统优化：可以监控到系统的API响应时间，如果超过固定时间，则会提示在优化列表中。
	列表展示信息有系统编码、接口地址、请求参数、请求时间、响应时间、过程花费时间、响应结果、响应数据大小、备注等信息。
```


### 初始程序
```
初始程序，先执行创建Monitor监控的数据库名称monitor、用户名root密码root，表结构和相关数据在程序启动时自动创建。
初始程序，先执行创建Task定时任务的数据库名称task、用户名root密码root，表结构会在程序启动时自动创建，初始测试数据脚本在【doc/定时任务/task-init.sql】。
配置文件修改（第一次启动使用推荐方式1）: 
    方式1：数据库链接在ms-cloud-config中，路径为[ms-core/ms-cloud-config/src/main/resources/config/]下对应的属性文件中修改。
    方式2：访问Monitor地址[http://127.0.0.1:5250]帐号admin、密码123456。进入主界面后，访问【微服务->配置文件管理】然后新增对应的服务的配置文件即可。
启动redis，修改对应服务中的redis配置的信息（修改方式参考修改配置文件的方式）。
```


### 配置域名映射关系 hosts配置
```
hosts文件所在位置：
window：C:\Windows\System32\drivers\etc\hosts
linux：/etc/hosts
配置内容如下：
127.0.0.1	msMonitor
127.0.0.1	msRc
127.0.0.1	msZuul
127.0.0.1	msConfig
127.0.0.1	msTask
127.0.0.1	msLog
```


### 启动服务 按以下顺序一一启动
```
启动eureka（启动文件：MsCloudEurekaApplication.java）
启动config（启动文件：MsCloudConfigApplication.java）
启动monitor（启动文件：MsCloudMonitorApplication.java）
启动log（启动文件：MsCloudLogApplication.java）
启动zuul（启动文件：MsCloudZuulApplication.java）
启动task（启动文件：MsCloudTaskApplication.java）
启动应用程序（biz-service-api/biz-service-admin）
```

### 注册中心使用
参考说明地址：https://www.52jingya.com/aid13386.html
```
注册中心选型
惊讶微服务注册中心采用的为eureka。
因为eureka2.x版本没有进行维护，所以我们采用的具体版本为1.5.2。该版本稳定，相比2.x资料全面等优点。
后续考虑采用consul
如何启动注册中心
下载源码：https://gitee.com/yuejing/micro-service
导入源码到开发工具中。
找到项目：ms-cloud-eureka
执行Main方法：com.ms.eureka.MsCloudEurekaApplication.java
提示启动成功，则说明注册中心启动正常。
```


### 配置中心使用
参考说明地址：https://www.52jingya.com/aid13387.html
```
惊讶配置中心采用的为spring-cloud-config
使用版本为2.0.2。
如何启动配置中心
下载源码：https://gitee.com/yuejing/micro-service
导入源码到开发工具中。
找到项目：ms-cloud-config
执行Main方法：com.ms.config.MsCloudConfigApplication.java
提示启动成功，则说明注册中心启动正常。
配置文件路径：
各个服务配置文件所在路径为：项目的resources/config下。属性文件名称和各个服务的id一一对应。
变更加载配置文件的位置：
打开项目中resources/application.properties文件，找到如下配置修改路径即可
#加载本地环境
spring.profiles.active=native
spring.cloud.config.server.native.searchLocations=classpath:/config
#spring.cloud.config.server.native.searchLocations=file:E:\\config-test
```

### 代理服务使用
参考说明地址：https://www.52jingya.com/aid13388.html
```
惊讶微服务的代理服务Agent，提供如下功能：
执行Shell命令，可以完成Monitor发起的部署命令。
如何启动代理服务
下载源码：https://gitee.com/yuejing/micro-service
导入源码到开发工具中。
找到项目：ms-cloud-agent
执行Main方法：com.ms.client.MsClientApplication.java
提示启动成功，则说明启动正常。
参数说明：
#部署文件下载保存的目录
version.dir=/app/appsoft/ms-cloud-agent-1.0.0/version
#当前agent的编码，与Monitor的Agent管理中添加的编码一致
client.id=C001
#当前agent的token，与Monitor的Agent管理中添加的token一致
client.token=6307a39dfc7ecb783d6682f4413911d7
#Monitor服务的地址
client.server.host=http://msMonitor:7250
```

### Monitor使用
参考说明地址：https://www.52jingya.com/aid13389.html
```
实现了功能有如下：
项目管理：可以自动发布服务到对应的机器上，实现一键部署
Agent管理：维护部署在各个机器上的代理服务
统一配置：可以将各个服务的配置文件在Monitor中维护
API服务：各个服务的接口说明都在Monitor中可以调度测试
生成源码：在Monitor中可以根据自定义的模板生成对应的增删改查的代码
前后端对接：提供了原型接口对应说明，方便前后端对接
与微服务相关的配置维护等都集成在Monitor中在线配置
```
```
登录地址：http://127.0.0.1:5250
账户：admin
密码：123456
```
登录后首页展示信息页面
![登录后首页](https://static.52jingya.com/syy/blog/2019/03/22/f42bdf0e447c4301bd2187b2024d3bad.png "登录后的页面")

发布版本（点击首页项目的【版本】按钮进入）
![发布版本](https://static.52jingya.com/syy/blog/2019/03/22/283999710240485d9c0c171b56046b03.png "发布版本")

然后新增版本，添加对应的信息。点击【去部署】，然后点击右边的【部署】按钮或【全部署】




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)