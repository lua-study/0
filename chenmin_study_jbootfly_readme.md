## 简介
JbootFly 是一个由 Jboot + Fly（一个html模板，网址：http://www.layui.com/template/fly/ ）开发的社区。


Jboot是一个基于JFinal 和 Undertow开发的微服务框架。提供了AOP、RPC、分布式缓存、限流、降级、熔断、统一配置中心、swagger api自动生成、
Opentracing数据追踪、metric数据监控、分布式session、代码生成器、shiro安全控制等功能。


Jboot网址：https://gitee.com/fuhai/jboot


## 功能清单（已经全部完成并正常运行）

* 登陆、注册、验证码
* 发帖、回帖
* 帖子列表、分页
* 帖子管理：置顶（三个置顶级别）、加精、删除、编辑
* 回帖：普通回帖、图片回帖、回帖被采纳
* 签到
* 积分名称：元宝。
* 积分规则：
    * 注册用户默认100积分、
    * 签到获得5积分、
    * 发帖获得10积分，
    * 发帖必须设置打赏积分，如果回帖被采纳，回帖者获得打赏的积分。
    * 回帖获得2积分
* 个人中心
    * 个人主页
    * 个人设置
        * 修改个人资料
        * 修改头像
        * 修改密码
    * 我的帖子
    * 我的搜藏
    * 我的动态


## 运行
* 请先在数据库上 建表和插入数据，sql在resource下JbootFly.sql.
* 配置 jboot.properties 文件的数据库账号密码
* 运行 App.java 的 main 方法启动

## 其他
* 默认 admin@jboot.io 为管理员，密码是 111111
* 管理员（user表role字段为 admin 的）可以对任意帖子进行置顶、推荐、编辑、删除等
* 管理员 可以激活其他成员，激活页面在用户中心里


## JbootFly 截图

登陆
![](./docs/images/app_login.png)

注册
![](./docs/images/app_reg.png)

首页
![](./docs/images/app_index.png)

发布新帖子
![](./docs/images/app_newpost.png)

帖子详情
![](./docs/images/app_post_detail.png)

个人中心（我的帖子）
![](./docs/images/app_mypost.png)

个人中心（设置）
![](./docs/images/app_setting.png)



## 注意
如果导入 idea 运行，请注意配置如下配置：
![](./docs/images/idea.jpg)

如果导入Eclipse运行，请注意配置如下配置：
![](./docs/images/eclipse.jpg)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)