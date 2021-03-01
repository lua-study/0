# 简介
目前java+js代码将近6w行，一共拆分为：用户，订单，购物车，计价，支付，配送，商品，搜索等服务，每个服务都有自己的独立数据库，服务与服务之间使用消息和http通信，分布式事务采用基于消息的最终一致性。

前端门户请看这里 :point_right:  https://gitee.com/dafanshudl/bigfans-cloud-front 

后台管理请看这里 :point_right:  https://gitee.com/dafanshudl/bigfans-admin

# 技术栈

- 服务注册： Spring Cloud Eureka Finchley.M2
- 服务网关： Spring Cloud Zuul Finchley.M2
- 负载均衡： Spring Cloud Ribbon Finchley.M2
- 服务配置： Spring Cloud Config Finchley.M2
- 服务追踪： Spring Cloud Sleuth Finchley.M2
- 持久层框架： Mybatis  3.4.4
- 数据库连接池： Druid
- 数据库  ：  MySql 5.6
- 全文检索： ElasticSearch 6.2.2
- 消息队列： Kafka 1.0.0
- 缓存和内存数据库 ： Redis
- 短信服务： 阿里大于
- 图片存储： 七牛云
- 支付： 支付宝当面付沙箱
- API文档： Swagger
- 日志组件： Log4j2 , ELK
- 构建工具： Maven
- 部署环境： Docker
- 插件： Lombok



# 系统架构图
![输入图片说明](https://gitee.com/uploads/images/2018/0410/134844_803dceaa_331009.png "系统架构设计 (2).png")

# 商品属性和SKU相关表设计
![输入图片说明](https://gitee.com/uploads/images/2018/0418/141417_b9977d42_331009.png "核心数据库表 (1).png")

图画的太丑 :joy: 


# 项目模块

| 模块 | 功能 |
| ------ | ------ |
| bigfans-cloud-api-gateway  | 微服务网关,基于SpringCloud-Zuul|
| bigfans-cloud-config-server  | 微服务配置中心服务端,基于SpringCloud-Config|
| bigfans-cloud-discovery-eureka  | 微服务注册中心,基于SpringCloud-Eureka|
| bigfans-cloud-service-cart  | 购物车服务, 提供用户购物车,临时购物车等服务|
| bigfans-cloud-service-catalog  | 目录服务,提供商品,分类,品牌,属性,规格,sku库存等服务|
| bigfans-cloud-service-notification  | 通知服务,发送短信,邮件等通知|
| bigfans-cloud-service-order  | 订单服务,提供下单,结算等服务|
| bigfans-cloud-service-payment  | 支付服务,与第三方集成提供支付功能,例如支付宝|
| bigfans-cloud-service-pricing  | 计价服务,计算订单,购物车,商品优惠的价格,提供优惠信息等|
| bigfans-cloud-service-review  | 评论服务, 提供商品评论,反馈,投诉等服务|
| bigfans-cloud-service-search  | 搜索服务, 提供全文检索,相似商品推荐,搜索提示等|
| bigfans-cloud-service-shipping  | 配送服务, 目前没实现|
| bigfans-cloud-service-system  | 系统服务, 提供系统通用信息|
| bigfans-cloud-service-user  | 用户服务, 提供注册,登录,用户地址,信息等|
| bigfans-cloud-zipkin-server  | zipkin请求日志追踪服务端,基于SpringCloud-Sleuth|
| bigfans-framework  | 基础框架,提供通用封装,不掺杂任何业务代码,可以直接引入到其他项目使用|
| bigfans-cloud-base  | 所有服务的基础模块, 提供通用的模型,事件等|

# 系统截图

 **1. 搜索** 

![输入图片说明](http://121.201.3.109:8080/bigfans/images/%E6%90%9C%E7%B4%A2.gif)

 **2. 商品详细** 

![输入图片说明](http://121.201.3.109:8080/bigfans/images/sku.gif)

 **3. 购物车** 

![输入图片说明](http://121.201.3.109:8080/bigfans/images/%E8%B4%AD%E7%89%A9%E8%BD%A6.gif)

 **4. 订单** 

![输入图片说明](http://121.201.3.109:8080/bigfans/images/%E8%AE%A2%E5%8D%95.gif)

![输入图片说明](https://gitee.com/uploads/images/2018/0418/202340_f39466e3_331009.jpeg "1524054180200.jpg")


 **5. 评论** 

![输入图片说明](http://121.201.3.109:8080/bigfans/images/%E8%AF%84%E8%AE%BA.gif)

# 开发计划
1. 升级后台管理系统
   目前后台bigfans-admin这个项目的react和ant design版本都比较老, 和后端的交互也有很多不兼容,所以下一步会先升级后台管理项目.
2. ...
   未来希望能够引入数据分析相关技术

# 后续

项目目前并不完善，我本人也不是做电商的，业务全靠一点点摸索，本来打算把功能做的差不多再开源，后来发现东西越做越多根本做不完。。。毕竟个人时间和精力有限，不过我会一直写下去也希望大家多提意见共同进步，你们的鼓励就是我的动力，给颗Star吧。[![star](https://gitee.com/dafanshudl/bigfans-cloud/badge/star.svg?theme=dark)](https://gitee.com/dafanshudl/bigfans-cloud/stargazers)

QQ群： 665695119

环境搭建视频和手册请加群获取




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)