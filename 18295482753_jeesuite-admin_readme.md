**黄金位置放个小广告→**欢迎加交流群：`230192763` （不限于讨论该框架热爱技术就行）
## jeesuite-admin
jeesuite-admin定位于统一系统运行管理系统。提供统一鉴权接入和监控管理，包括：配置中心后台、kafka监控、定时任务监控管理、微服务监控、APM以及第三方成熟监控产品的接入。同时该项目也作为`Spring-cloud`微服务集成[jeesuite-libs](http://git.oschina.net/vakinge/jeesuite-libs)的一个示范项目。

####  [在线演示](http://47.93.239.14:7777/admin.html) `账号/密码：test/test123`
设置安全ip，安全码：`12345678`
#### 依赖lib
 - spring boot 1.5.2.RELEASE 
 - [jeesuite-mybatis](http://git.oschina.net/vakinge/jeesuite-libs/tree/master/jeesuite-mybatis)
 - [jeesuite-cache](http://git.oschina.net/vakinge/jeesuite-libs/tree/master/jeesuite-cache)
 - [jeesuite-kafka](http://git.oschina.net/vakinge/jeesuite-libs/tree/master/jeesuite-kafka)
 - [jeesuite-scheduler](http://git.oschina.net/vakinge/jeesuite-libs/tree/master/jeesuite-scheduler)
 - mybatis
 - druid
 - mapper
 
#### 依赖说明（如果出现包找不到或者某些class没找到）
- SNAPSHOT结尾的依赖包请自行下载[jeesuite-libs](http://git.oschina.net/vakinge/jeesuite-libs) 项目本地构建。
- release版的依赖请配置最高的版本号，版本号请看：[sonatype](https://oss.sonatype.org/content/repositories/releases/com/jeesuite/) 

#### 已实现功能
 - 配置中心
   1. 支持全局配置、多应用共享配置
   2. 支持配置文件、配置项、json配置支持
   3. 支持配置DES、RSA加密
   4. 支持spring、springboot无缝对接
   5. 支持占位符引用
   6. 支持环境、项目维度权限控制
   7. 支持开启/停用仅内网拉取配置限制
   8. 支持在线查看应用当前运行时配置（配置中心与本地合并后的最终配置）
   9. 支持查看日志变更记录并一键恢复
 - 定时任务监控（需要使用`jeesuite-scheduler`模块）
   1. 支持实时监控定时任务执行情况
   2. 支持手动执行触发定时任务
   3. 支持开关定时任务及设置执行时间策略
 - kafka监控
   1. 支持kafka producer发送成功率监控
   2. 支持consumer logsize、lat、partition监控
 - 其他
   1. 支持开启安全ip功能
 
 
####应用集成配置中心请参考
[jeesuite-confcenter-client](http://git.oschina.net/vakinge/jeesuite-libs/tree/master/jeesuite-confcenter-client)

或者直接下载demo项目[jeesuite-bestpl](http://git.oschina.net/vakinge/jeesuite-bestpl) 已经集成了配置中心


#### 计划实现功能（主要整合一些成熟的监控产品）
 - spring cloud监控
 - zookeeper管理
 - redis监控管理
 
 
#### 如何运行
 1. 执行sql脚本
 2. 修改application.properties文件对应数据配置
 3. 直接运行Application.java,或者打包后通过java -jar 运行
 4. 初始账号密码：admin/admin123

#### 页面截图
页面基于`layui-beginner_admin`构建。

![image](http://ojmezn0eq.bkt.clouddn.com/admin_profile.png)
![image](http://ojmezn0eq.bkt.clouddn.com/admin_config.png)
![image](http://ojmezn0eq.bkt.clouddn.com/admin_config_jm.png)
![image](http://ojmezn0eq.bkt.clouddn.com/admin_ms.png)
![image](http://ojmezn0eq.bkt.clouddn.com/admin_kafka.png)
![image](http://ojmezn0eq.bkt.clouddn.com/admin_sch.png)





 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)