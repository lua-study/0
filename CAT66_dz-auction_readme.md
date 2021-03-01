# dz-auction 对庄拍卖系统

readme编写日期：2019-10-07
本项目看情况保持更新

#### 介绍

1.拍卖自动开拍
2.拍卖自动结拍2
3.拍卖保证金功能
4.拍卖中标自动创建订单
5.拍卖未中标退款
6.拍卖加价延长时间

#### 软件架构

截止到2019-10-07，该项目整合了spring全家桶最新的框架版本，框架使用maven parent项目管理版本，保持子项目版本统一

主要框架：
spring-boot 2.1.8.RELEASE
spring-boot-starter-data-jpa 2.1.8.RELEASE
spring-cloud Greenwich.SR3
spring-cloud-starter-openfeign
eureka-server

数据库：postgresql
swagger2.8


#### 安装教程

导入项目到idea

![主要结构](https://images.gitee.com/uploads/images/2019/1007/230004_92ebf231_4846092.png "EE308843-3B03-41bb-9FAC-719BEE9589D6.png")

dz-auction-parent为父项目，它的pom.xml管理所有子项目的框架
auction-provider为生产者服务，主要功能是拍卖自动开拍、拍卖自动结拍、拍卖中标自动创建订单、拍卖未中标退款。目前其他功能也写在这个服务
auction-web是api、页面等
eureka-server是Netflix开发的服务发现框架，本身是一个基于REST的服务，同等zk。这个项目配合openfeign框架，微服务之间使用rpc调用、通讯

1. 导入数据库
2. 分别启动springboot启动器
3. auction-web使用maven里面的springboot-run启动不然不支持jsp

![输入图片说明](https://images.gitee.com/uploads/images/2019/1007/231822_423a61eb_4846092.jpeg "首页.jpg")

#### 使用说明

1. 首页：http://localhost:8763/main
2. auction-provider服务 http://localhost:8762/
3. eureka-server：http://localhost:8761/
4. swagger：http://localhost:8763/swagger-ui.html

#### 参与贡献

1. Fork 本仓库
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


#### 后续计划

1. 整个业务层加入redis 
2. 加入mq限流、削峰，如排队、答题、分层过滤，限制无效请求，减少服务器负担
3. Spring整合DWR comet 实现无刷新显示拍卖时间和竞投人数据

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)