# jee-weapp

#### 简介
- jee-weapp基于微信第三方开放平台基础框架，
- 多模块化开发不同的微信营销插件，
- 支持微信第三方平台扫码授权公众号，小程序
- 支持微信第三方平台覆盖全网发布
- 支持小程序模板开发
- 目前开放营销插件有拼团，满减，限时打折等


#### 软件架构
- jfinal 作为web orm基础框架，
- shiro做安全框架，角色授权，
- 微信商城作为业务基础框架，衍生出一系列针对微信商城的营销插件，
- 包括吸粉，引流，客户留存，推广等一系列插件，
- 每个插件通过dubbo封装成微服务，可独立发布，
- 每个微服务都可以通过docker容器快速部署，
- 支持dubbo灰度发布，
- 可针对特定用户独享容器与数据库

#### 功能列表
【店铺】：店铺基本资料，店铺发货地址，我的文件管理

【商品】：商品发布、分类、规格、运费。

【订单】：订单查询、批量打印、批量发货、退款、快递单模板、发货单模板。

【营销】：限时打折，订单返现，满减送，满包邮。

【会员】：微信公众号粉丝管理。

【设置】：公众号，小程序扫码授权，支付配置。

#### 项目结构
商城系统采用Maven管理，包括以下基础模块：

weapp-service-api ：dubbox的接口规范，支持rpc远程调用。

weapp-service-provider ：核心业务项目。主要是Service处理业务逻辑。

weapp-model ：数据模型，与数据库表字段对应的实体类。

weapp-web-admin ：PC后台管理端。

weapp-web-mobile ：公众号微信端。

weapp-web-api ：微信小程序接口。

weapp-template/wxmall小程序客户端代码

#### 技术选型
核心框架：JFinal 4.7

数据库：mysql 5.6 +

JS框架：jquery-2.1.4，Bootstrap 3.6，jquery weui微信移动框架（微信前端开发的瑞士军刀）

#### 环境与工具

1.  jdk8+, maven 3.3
2.  mysql 5.6+ 字符编码utf8mb4
3.  IntelliJ IDEA （推荐）或 eclipse

#### 新手视频教程
[点击查看新手视频教程](https://www.bilibili.com/video/av74935856/)

#### 安装教程

1.  下载源码 https://gitee.com/dianbuapp_admin/jee-weapp
2.  导入数据库（数据库脚本在weapp-web-admin/doc目录下，mysql 5.6+）
3.  数据库配置文件在weapp-service-provider下的jboot.properties文件中，对应的数据库用户名，密码修改成自己的即可
3.  通过IntelliJ IDEA 或 eclipse导入源码
4.  通过maven命令mvn clean package编译源码
5.  main方法运行weapp-service-provider工程下的StartApp类启动dubbo服务提供者
6.  main方法运行weapp-web-admin工程下的_common包下的StartAdmin类，启动应用管理后台，dubbo服务消费者
7.  开发环境下使用dubbo直连模式，无需启动注册中心，线上发布改成zook模式即可使用zookeeper注册中心发布服务
8.  浏览器访问localhost，默认账号13800138000 密码1111111111
9.  通过微信开发者工具，导入weapp_template/wxmall小程序客户端代码
10. 如果提示小程序无权限，可以配置自己的小程序appid，配置前先到http://admin.dbumama.com/授权小程序即可

#### 关注微信公众号
![关注公众号获取最新项目信息](https://images.gitee.com/uploads/images/2019/1108/114913_a764999d_471938.png "weixin.png")

#### 部分截图

![输入图片说明](https://images.gitee.com/uploads/images/2019/1108/112227_29619881_471938.png "微信图片_20191108110518.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/1108/112236_f332a3a0_471938.png "微信图片_20191108110612.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/1108/112244_9ce38335_471938.png "微信图片_20191108110652.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/1108/112253_067d76aa_471938.png "微信图片_20191108111747.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/1108/112300_776ba464_471938.png "微信图片_20191108111751.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/1108/112311_b4d04f91_471938.png "微信图片_20191108111757.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/1108/112322_915351ee_471938.png "微信图片_20191108111802.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/1108/112330_98c11cd5_471938.png "微信图片_20191108111810.png")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)