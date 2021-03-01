------------------------------------------------

> JFinalShop 4.0

------------------------------------------------
## JFinalShop 4.0 系统简介

JFinalShop商城系统是B2C模式的电子商城，是在JFinal基础上搭建的一个Java项目。JFinal以易学易用著称，让您轻松打造自己的独立商城，同时也方便二次开发，让您快速搭建个性化独立商城，为您节约更多时间，去陪恋人、家人和朋友。

## JFinalShop 4.0 功能简介

 **功能列表**
1.	【商品管理】：商品管理、库存管理、商品分类、商品参数、商品属性、规格管理、品牌管理、到货通知。
2.	【订单管理】：订单管理、收款管理、退款管理、发货管理、发货点管理、快递单模板。
3.  【会员管理】：会员管理、会员等级、会员注册项、积分管理、预存款、评论管理、咨询管理、消息配置。
4.  【内容管理】：导航管理、文章管理、文章分类、标签管理、友情链接、广告位、广告管理、模板管理、主题设置、缓存管理、静态化管理、索引管理。
5.  【营销管理】：促销管理、优惠券管理、SEO设置、Sitemap管理。
5.  【统计报表】：访问统计、统计设置、会员统计、订单统计、会员排名、商品排名。
6.  【系统设置】：系统设置、地区管理、支付方式、配送方式、物流公司、支付插件、存储插件、登录插件、管理员、权限管理、角色管理、发送消息、消息列表、草稿箱、日志管理。


## JFinalShop 4.0 项目结构
 **商城系统采用Maven管理，包括以下6大模块：**
 jfinalshop-api 	：项目的对外接口Android、IOS、小程序等外部接口。
 jfinalshop-common 	：工具类，所有工具类都提取出来写在这个项目中。
 jfinalshop-core 	：核心业务项目。主要是Service处理业务逻辑。
 jfinalshop-model 	：数据模型，与数据库表字段对应的实体类。
 jfinalshop-dao 	：数据持久层，操作低层数据库。
 jfinalshop-web 	：项目的web层，admin,shop,wap页面的显示以及控制层。


## JFinalShop 4.0 技术选型

1、后端

* JDK：1.8
* 核心框架：JFinal 3.0, JFinal-ext2 2.0.5
* 安全框架：Apache Shiro 1.3.2
* 数据库连接池：Alibaba Druid 1.0.27
* 缓存框架：Ehcache 2.10.2
* 日志管理：SLF4J 1.7.7、Log4j 1.2.17
* 工具类：Apache Commons-lang3 3.1、fastjson 1.2.19
* 搜索框架：lucene-core 6.3.0
* 搜索插件：LucenePlus

2、前端

* JS框架：jquery-2.1.4
* 表格插件：Bootstrap Table
* 表单验证插件：jquery.validate
* 日期选择插件：Datepicker for Bootstrap
* 弹层组件：layer
* 数据图表：echarts
 
> 运行项目配置说明

```
1、具备运行环境：JDK 1.8+、Maven 3.0+、MySQL 5.6+、Eclipse Luna 

2、git下载项目后，在Eclipse 左侧空白处右击->import-import-> Existing Maven Projects

3、根据 \src\main\resources\jfinalshop.properties 配置数据库

4、导入数据库 \jfinalshop-4.0\jfinalshop4.sql

```

## JFinalShop 4.0 特别说明

1. 免费下载jfinalshop 2.0入门学习，详细介绍请点[查看](https://git.oschina.net/hycx227/jfinalshop-2.0)；

2. 捐赠下载jfinalshop 3.0进阶学习，详细介绍请点[查看](https://git.oschina.net/hycx227/jfinalshop-2.0)；

3. 捐赠下载jfinalshop 4.0二次开发，详细介绍请先联系QQ:187048359。

## 演示地址

1.前台 demo.jfinalshop.com 请点[查看](http://demo.jfinalshop.com)；
2.后台 demo.jfinalshop.com/admin 请点[查看](http://demo.jfinalshop.com/admin)；
3.用户名/密码：jack/123456

移动端 用户名/密码：hycx5/qqqq
## h5商城演示界面
![输入图片说明](https://static.oschina.net/uploads/space/2017/0214/192610_xnZT_566102.png "h5商城演示界面")



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)