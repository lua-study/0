# zscat-platform

# qq: 951449465
#### 项目介绍

> 基于SpringBoot+MyBatis的电商系统，包括前台商城系统及后台管理系统。

> 如果该项目对您有帮助，您可以点右上角 "Star" 支持一下 谢谢！

> 或者您可以 "follow" 一下，该项目将持续更新，不断完善功能。

> 项目交流qq群 419078373 473023475 203747031

> 如有问题或者好的建议可以在 Issues 中提。

> 单机版mall商城 https://gitee.com/catshen/mall-applet 

> dubbo版本mall商城github  https://github.com/shenzhuan/mall-dubbo

> dubbo版本mall商城码云地址  https://gitee.com/catshen/mall-dubbo

zscat-platform是高效率，低封装，面向学习型，面向微服的开源Java EE开发框架。

zscat-platform是在SpringBoot基础上搭建的一个Java基础开发平台，MyBatis为数据访问层，ApacheShiro为权限授权层，Ehcahe对常用数据进行缓存,dubbo为数据远程调用。

zscat-platform主要定位于后台管理系统学习交流，已内置后台管理系统的基础功能和高效的代码生成工具， 包括：系统权限组件、数据权限组件、数据字典组件、核心工具组件、视图操作组件、工作流组件、代码生成等。 前端界面风格采用了结构简单、性能优良、页面美观大气的Twitter Bootstrap页面展示框架。 采用分层设计、双重验证、提交数据安全编码、密码加密、访问验证、数据权限验证。 使用Maven做项目管理，提高项目的易开发性、扩展性。

zscat-platform目前包括以下四大模块，系统管理（SYS）模块、 内容管理（CMS）模块、在线办公（OA）模块、代码生成（GEN）模块。 系统管理模块 ，包括企业组织架构（用户管理、机构管理、区域管理）、 菜单管理、角色权限管理、字典管理等功能； 内容管理模块 ，包括内容管理（文章、链接），栏目管理、站点管理、 公共留言、文件管理、前端网站展示等功能； 在线办公模块 ，提供简单的请假流程实例；代码生成模块 ，完成重复的工作。

zscat-platform 提供了常用工具进行封装，包括日志工具、缓存工具、服务器端验证、数据字典、当前组织机构数据 （用户、机构、区域）以及其它常用小工具等。另外还提供一个强大的在线 代码生成 工具。

`mall-dubbo`项目是一套电商系统，包括前台商城系统及后台管理系统，小程序，h5，基于SpringBoot+MyBatis实现。
前台商城系统包含首页门户、商品推荐、商品搜索、商品展示、购物车、订单流程、会员中心、客户服务、帮助中心等模块。
后台管理系统包含商品管理、订单管理、会员管理、促销管理、运营管理、内容管理、统计报表、财务管理、权限管理、代码生成设置等模块。
### 技术选型

####部署和演示wiki https://github.com/shenzhuan/mall-dubbo/wiki

后台功能列表
 
小程序功能列表
 

#### 后端技术

技术 | 说明 | 官网
----|----|----
dubbo
Spring Boot | 容器+MVC框架 | [https://spring.io/projects/spring-boot](https://spring.io/projects/spring-boot)
Spring Security | 认证和授权框架 | [https://spring.io/projects/spring-security](https://spring.io/projects/spring-security)
MyBatis | ORM框架  | [http://www.mybatis.org/mybatis-3/zh/index.html](http://www.mybatis.org/mybatis-3/zh/index.html)
MyBatisGenerator | 数据层代码生成 | [http://www.mybatis.org/generator/index.html](http://www.mybatis.org/generator/index.html)
PageHelper | MyBatis物理分页插件 | [http://git.oschina.net/free/Mybatis_PageHelper](http://git.oschina.net/free/Mybatis_PageHelper)
Swagger-UI | 文档生产工具 | [https://github.com/swagger-api/swagger-ui](https://github.com/swagger-api/swagger-ui)
Hibernator-Validator | 验证框架 | [http://hibernate.org/validator/](http://hibernate.org/validator/)
Elasticsearch | 搜索引擎 | [https://github.com/elastic/elasticsearch](https://github.com/elastic/elasticsearch)
RabbitMq | 消息队列 | [https://www.rabbitmq.com/](https://www.rabbitmq.com/)
Redis | 分布式缓存 | [https://redis.io/](https://redis.io/)
MongoDb | NoSql数据库 | [https://www.mongodb.com/](https://www.mongodb.com/)
Docker | 应用容器引擎 | [https://www.docker.com/](https://www.docker.com/)
Druid | 数据库连接池 | [https://github.com/alibaba/druid](https://github.com/alibaba/druid)
OSS | 对象存储 | [https://github.com/aliyun/aliyun-oss-java-sdk](https://github.com/aliyun/aliyun-oss-java-sdk)
JWT | JWT登录支持 | [https://github.com/jwtk/jjwt](https://github.com/jwtk/jjwt)
LogStash | 日志收集 | [https://github.com/logstash/logstash-logback-encoder](https://github.com/logstash/logstash-logback-encoder)
Lombok | 简化对象封装工具 | [https://github.com/rzwitserloot/lombok](https://github.com/rzwitserloot/lombok)

#### 前端技术

技术 | 说明 | 官网
----|----|----
Vue | 前端框架 | [https://vuejs.org/](https://vuejs.org/)
Vue-router | 路由框架 | [https://router.vuejs.org/](https://router.vuejs.org/)
Vuex | 全局状态管理框架 | [https://vuex.vuejs.org/](https://vuex.vuejs.org/)
Element | 前端UI框架 | [https://element.eleme.io/](https://element.eleme.io/)
Axios | 前端HTTP框架 | [https://github.com/axios/axios](https://github.com/axios/axios)
v-charts | 基于Echarts的图表框架 | [https://v-charts.js.org/](https://v-charts.js.org/)
Js-cookie | cookie管理工具 | [https://github.com/js-cookie/js-cookie](https://github.com/js-cookie/js-cookie)
nprogress | 进度条控件 | [https://github.com/rstacruz/nprogress](https://github.com/rstacruz/nprogress)
4、平台

服务器中间件：SpringBoot内置
数据库支持：目前仅提供MySql数据库的支持，但不限于数据库
开发环境：Java、Eclipse Java EE 、Maven 、Git
安全考虑
开发语言：系统采用Java 语言开发，具有卓越的通用性、高效性、平台移植性和安全性。
分层设计：（数据库层，数据访问层，业务逻辑层，展示层）层次清楚，低耦合，各层必须通过接口才能接入并进行参数校验（如：在展示层不可直接操作数据库），保证数据操作的安全。
双重验证：用户表单提交双验证：包括服务器端验证及客户端验证，防止用户通过浏览器恶意修改（如不可写文本域、隐藏变量篡改、上传非法文件等），跳过客户端验证操作数据库。
安全编码：用户表单提交所有数据，在服务器端都进行安全编码，防止用户提交非法脚本及SQL注入获取敏感数据等，确保数据安全。
密码加密：登录用户密码进行SHA1散列加密，此加密方法是不可逆的。保证密文泄露后的安全问题。
强制访问：系统对所有管理端链接都进行用户身份权限验证，防止用户直接填写url进行访问。

#### 软件架构
软件架构说明

- ├── mall-common -- 工具类，通用类几乎不依赖任务jar包
- ├── mall-core -- 工具类，核心类
- |-- cms-api     内容服务中心接口
- |-- cms-service 内容服务中心服务 【20881】，可以单独数据库
- |-- ums-api     用户服务中心接口
- |-- ums-service 用户服务中心服务 【20882】，可以单独数据库
- |-- pms-api     商品服务中心接口
- |-- pms-service 商品服务中心服务 【20883】，可以单独数据库
- |-- oms-api     订单服务中心接口
- |-- oms-service 订单服务中心服务 【20884】，可以单独数据库
- ├── mall-portal-- 【8085】 前台接口的聚合
- ├── mall-admin--  【8081】 后台接口的聚合




#### 安装教程


### 注意

模型类无get,set方法，采用lombok注解方式实现。 需要安装插件

- 1. 创建数据库mall,
- 2.下载群里的zscat-tools,一键启动zookeep,redis,nginx rabbitmq,
需要安装mongodb，配置相关地址
- 3.启动cms-service，运行springboot的主类
- 4.启动ums-service，运动springboot的主类
- 5.启动pms-service，运动springboot的主类
- 6.启动oms-service，运动springboot的主类
- 7.启动mall-portal，运动springboot的主类，http://localhost:8085/swagger-ui.html  
- 8.启动mall-admin，运动springboot的主类， http://localhost:8080/swagger-ui.html  
- 9.启动mall-search，运动springboot的主类，http://localhost:8081/swagger-ui.html  
- 10 克隆`mall-admin-web`项目，并导入到IDEA中完成编译
- 在IDEA命令行中运行命令：npm install,下载相关依赖;
- 在IDEA命令行中运行命令：npm run dev,访问地址：[http://localhost:8090](http://localhost:8090) 即可打开后台管理系统页面;


 **_uniapp_** 

uni-app 是一个使用 Vue.js 开发跨平台应用的前端框架，开发者编写一套代码，可编译到iOS、Android、H5、小程序等多个平台。

 



## 目前h5项目已实现功能
1. 首页数据的展示
2. 分类页数据的展示
3. 购物车
4. 我的
5. 注册
6. 登录
7. 商品详情页
8. 商品搜索
##h5项目效果图


![](https://images.gitee.com/uploads/images/2019/0217/112713_5f032a4c_134431.png)

![](https://images.gitee.com/uploads/images/2019/0217/112713_f4cb24ab_134431.png)

![](https://images.gitee.com/uploads/images/2019/0217/112713_a17c828d_134431.png)

![](https://images.gitee.com/uploads/images/2019/0217/112713_a7afcc52_134431.png)

![](https://images.gitee.com/uploads/images/2019/0217/112713_2d82d3c8_134431.png)

![](https://images.gitee.com/uploads/images/2019/0217/112714_62baf63a_134431.png)

![](https://images.gitee.com/uploads/images/2019/0217/112715_c571472d_134431.png)


## 目前小程序项目已实现功能
1. 首页数据的展示
2. 分类页数据的展示
3. 购物车
4. 我的
5. 注册
6. 登录
7. 商品详情页
8. 商品搜索
9.下单
10.用户详情


## 目前pc项目已实现功能
1. 首页数据的展示
2. 分类页数据的展示
3. 购物车
4. 我的
5. 注册
6. 登录
7. 商品详情页
8. 商品搜索
9.下单
10.用户详情

#### 参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request

### 微信交流群
![输入图片说明](https://images.gitee.com/uploads/images/2018/1202/213120_80b3755c_134431.jpeg "platform.jpg")
### 群主微信
![输入图片说明](https://images.gitee.com/uploads/images/2018/1202/213146_d8dcc5b2_134431.jpeg "zscat.jpg")

###  请作者喝杯咖啡

![输入图片说明](https://git.oschina.net/uploads/images/2017/0829/203712_6694b4c1_134431.jpeg "weixin.jpg")
![输入图片说明](https://git.oschina.net/uploads/images/2017/0829/203723_5567bd56_134431.jpeg "alipay.jpg")
###  **- - 关注公众号 ，有更多的资料** 
![输入图片说明](https://images.gitee.com/uploads/images/2018/0923/103015_3df65a8a_134431.jpeg "qrcode_for_gh_ad5fa85786aa_344.jpg")
 **_

### 
待做功能
_** 

![输入图片说明](https://images.gitee.com/uploads/images/2019/0120/093834_eef64601_134431.png "屏幕截图.png")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)