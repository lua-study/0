# AiJ 游戏服务器

#### 介绍
AiJ是一套完整的房间类游戏解决方案，支持无限水平扩展来满足更大的人数承载，并且提供了良好的调试接口。

主要模块包括：

* 注册中心
* 大厅服务 
* 游戏服务
* 亲友圈服务
* 运营管理系统
* CocosCreator游戏客户端。

网络协议使用Websocket，以更好的支持多平台需求，计划同时支持Mysql、Oracle、SqlServer、Postgresql、Sqlite等多种数据库。

#### 帮助文档

- [快速开始](./doc/aij_quick_start_dev.md)
- 子游戏开发
- 客户端调试
- 未完待续...


#### 技术架构

* Socket框架tio
* mvc与orm框架jfinal
* 注册中心zookeeper
* 网络协议Websocket
* 数据库版本管理flyway
* 客户端游戏引擎CocosCreator
* 客户端编辑器FairyGUI
* 开发语言:java、typescript、javascript、sql

### 业务架构
* 大厅
    * 房卡充值
    * 游戏回放
    * 游戏战绩
    * 实名制
    * ...
* 子游戏
    * 麻将
    * 斗地主
    * 象棋
    * ...
* 亲友圈
    * ...
* 运营管理
    * 玩家管理
    * 服务器管理
    * 代理管理
    * 报表统计
    * ...

#### 快速了解

* UI编辑器

![输入图片说明](https://gitee.com/uploads/images/2019/0428/175537_3e7b183a_369917.png "2.png")

* 开发调试

![输入图片说明](https://gitee.com/uploads/images/2019/0428/175549_b02a6a74_369917.png "WX20190428-175249.png")

* 子游戏

![输入图片说明](https://gitee.com/uploads/images/2019/0428/213459_1ec2c286_369917.png "QQ20190428-212614.png")

* 结算1

![输入图片说明](https://gitee.com/uploads/images/2019/0428/213413_7b220071_369917.png "QQ20190428-212906.png")

* 结算2

![输入图片说明](https://gitee.com/uploads/images/2019/0428/213439_d873ad71_369917.png "QQ20190428-212937.png")

* 回放

![输入图片说明](https://gitee.com/uploads/images/2019/0428/214352_4e7b7e03_369917.png "QQ20190428-214307.png")

* 运营管理

![输入图片说明](https://gitee.com/uploads/images/2019/0428/175609_acddfeaf_369917.png "4.png")

#### 参与贡献

1. Fork 本仓库
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


#### 其他

1. 个人博客 [www.xiyoufang.com](https://www.xiyoufang.com) 获取更多软件开发信息
2. gitee项目首页 [https://gitee.com/xiyoufang/aij](https://gitee.com/xiyoufang/aij)
3. 欢迎关注我的个人微信订阅号

![输入图片说明](https://images.gitee.com/uploads/images/2018/0712/165633_95e6b777_369917.jpeg "qrcode_for_gh_3870df3b5d1f_344.jpg")

### 您也可以加入游戏开发交流QQ群：112958956 ，一起讨论游戏开发技术。

![输入图片说明](https://images.gitee.com/uploads/images/2018/0708/183503_d1f599f2_369917.png "temp_qrcode_share_112958956.png")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)