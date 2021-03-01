# 基于 springboot2 改造的Open-shop 版是一套完全开源的微信小程序商场系统，真正前后台全部开源。希望大家可以支持我，我会不断完善代码和推出新功能来让大家更好的使用



# 对比open-shop项目，初步作了如下修改调整
* 对项目包结构进行了部分调整，目前项目之间的依赖处理的不是很好
* 项目整体使用springboot框架进行替换，一个Main函数启动，去掉外部容器的依赖
* 持久层引入mybatis Plus 目前仅做了兼容之前的接口，后面开会新接口，可以基于mybatis Plus 封装接口进行开发
* 视图层因springboot2以后不支持velocity模板 ,故废弃掉velocity模板改使用Freemarker模板；

。

# 技术框架
* 核心框架：Spring boot2.1.6
* 安全框架：Apache Shiro 1.2
* 持久层框架：MyBatis Plus
* 数据库连接池：Alibaba Druid 1.0
* 日志管理：SLF4J 1.7、Log4j
* JS框架：Vue 2.5.1，iview，layer 3.0.3，jquery 2.2.4，jqgrid 5.1.1 
* CSS框架：Twitter bootstrap3.3.7。
* 富文本：froala_editor1.2.2

# 开发环境
建议开发者使用以下环境，这样避免版本带来的问题
* IDE:IDEA
* DB:Mysql5.8
* JDK:JAVA8
* CACHE:Redis4.0

# 运行环境
* 数据库服务器：Mysql5.8
* 操作系统：Windows、Linux、Unix 等

## 交流群： 1017040237
![qq群.png](doc/群.jpg) 



# 快速体验

  #管理端
* 将Open-Shop项目源码通过maven形式导入IDEA；
* 需要下载Redis并启动
* 导入shop.sql数据文件,注意：数据库使用utf-8编码； 
* 修改platform-admin/application-dev.yml文件中的数据库设置参数；
* 修改j2cache.properties文件Redis连接信息
* 直接启动包根目录下的PlatformAdminApplication
* 访问后台地址：http://ip|域名/项目发布名/
* 管理员账号，用户名：admin 密码：admin


  #小程序端
* 将Open-Shop项目源码通过maven形式导入IDEA；
* 需要下载Redis并启动
* 导入shop.sql数据文件,注意：数据库使用utf-8编码； 
* 修改platform-api/application-dev.yml文件中的数据库设置参数；
* 修改j2cache.properties文件Redis连接信息
* 直接启动包根目录下的ApiApplication


# 小程序部署：
* 前端小程序原项目需要密码解压，暂未提供
* 打开小程序工具；
* 选择你下载的源代码wx-mall小程序项目；
* 输入你的AppID；
* 填写你的项目名称；
* 进入之后修改config文件夹里的api.js文件，把NewApiRootUrl改为你后台接口地址即刻运行。

# 小程序演示效果
![](https://images.gitee.com/uploads/images/2019/0625/104952_f9964aa6_1293644.png "前段演示")

# 主界面
![主界面](https://images.gitee.com/uploads/images/2019/0223/145546_1c4fc356_1293644.jpeg "主界面，插件商城")
# 菜单
![菜单](https://images.gitee.com/uploads/images/2019/0223/145541_2a1e5aba_1293644.png "菜单1")

本项目来自码云上 老花生 / Open-Shop（https://gitee.com/old-peanut/wechat_applet__open_source）项目。
我们修复了所有发现的bug，还有自己的新功能增加。
后面会有不断的更新新功能。

## 打赏作者买瓶防脱发药水吧~~~ o(╥﹏╥)o
![微信收款.png](doc/微信收款.png)![支付宝收款.png](doc/支付宝收款.png)





 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)