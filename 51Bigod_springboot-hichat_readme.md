# springcloud-hichat（前后端分离）

这是本人的第一个开源项目...请多多指教。

ps：本人比较倾向于后端开发，所以页面做得丑，而且页面做的不多，望见谅。主要想体验下springcloud带来的魅力，所以写的代码不是写的很溜啊，希望大神们能提些建议让我开开眼界，也可以一起交流。

该项目分为：用户移动web端和后台web管理系统

wiki后续再补上



# 技术选型

1、后端
- 核心框架：Spring Boot Spring Cloud（用到的组件有eureka、feign、zuul、hystrix、ribbon)
- 安全框架：Apache Shiro
- 持久层框架：MyBatis
- 数据库连接池：Alibaba Druid
- 缓存框架：Redis
- 日志管理：logback
- 数据库：mysql
- 及时通讯框架：t-io（websocket生态组件。码云GVP项目,大神的开源项目不错呀）
- 代码生成工具：mybatis generator



2、前端
- JS框架：vue、vuex、vue-router
- 页面构建：vue-cli脚手架+webpack
- html框架：framework7+vue（移动web），element-ui(后台管理)
- 异步请求框架：axios
- 对象、集合等工具：lodash
- 图表工具：v-charts(因为本项目没有大量的数据，所以写的是静态数据做显示)
- 通讯：websocket
- 图片懒加载：vue-lazyload
- 图片切图截图：photoclip
- pc图轮播：va-carousel
- pc页面跳转进度条：nprogress
- pc图片浏览：vue-photo-preview

4、平台

开发环境：java1.8以上、intellij idea、webstorm 、maven 、svn、nodejs、mysql、谷歌浏览器
图片目录nginx代理


系统项目说明(后端，管理员账号：admin 密码123456)：
- hichat-common（实体类、dto、工具类）
- hichat-eureka(服务治理与注册中心)
- hichat-mobile(移动端web接口项目，服务消费者)
- hichat-provider(服务提供者)
- hichat-web(后台管理系统，服务消费者)
- hichat-zuul(系统服务网关)

系统项目说明(前端)：
- hichat（移动端）
- hichat-web(pc后台)





# 效果图

移动端

![登录页](https://images.gitee.com/uploads/images/2018/0803/220648_2f3cddf8_621372.png "微信图片_20180803220206.png")

![注册](https://images.gitee.com/uploads/images/2018/0803/220718_72e29fdd_621372.png "微信图片_20180803220245.png")

![上传、截图](https://images.gitee.com/uploads/images/2018/0803/220738_eeeaf6db_621372.png "微信图片_20180803220238.png")

![截图后](https://images.gitee.com/uploads/images/2018/0803/220756_59829bf3_621372.png "微信图片_20180803220241.png")

![首页](https://images.gitee.com/uploads/images/2018/0803/220841_9ba0caed_621372.png "微信图片_20180803220310.png")

![用户列表页](https://images.gitee.com/uploads/images/2018/0803/220854_8faf8f41_621372.png "微信图片_20180803220248.png")

![个人信息列表](https://images.gitee.com/uploads/images/2018/0803/220908_37bdb51a_621372.png "微信图片_20180803220251.png")

![聊天页](https://images.gitee.com/uploads/images/2018/0803/221000_594a8576_621372.png "微信图片_20180803220256.png")

![图片预览](https://images.gitee.com/uploads/images/2018/0803/221016_86ec980d_621372.png "微信图片_20180803220259.png")

![发表图文](https://images.gitee.com/uploads/images/2018/0803/221036_1b8384ac_621372.png "微信图片_20180803220304.png")

pc后台

![输入图片说明](https://images.gitee.com/uploads/images/2018/0803/221250_2a99c7c5_621372.png "微信图片_20180803220344.png")

![输入图片说明](https://images.gitee.com/uploads/images/2018/0803/221301_da0875f3_621372.png "微信图片_20180803220347.png")

![输入图片说明](https://images.gitee.com/uploads/images/2018/0803/221316_176cce78_621372.png "微信图片_20180803220350.png")

![输入图片说明](https://images.gitee.com/uploads/images/2018/0803/221332_b273c26e_621372.png "微信图片_20180803220352.png")

![输入图片说明](https://images.gitee.com/uploads/images/2018/0803/221341_f8b22042_621372.png "微信图片_20180803220355.png")

![输入图片说明](https://images.gitee.com/uploads/images/2018/0803/221351_c16891ca_621372.png "微信图片_20180803220359.png")

![输入图片说明](https://images.gitee.com/uploads/images/2018/0803/221528_c5d96197_621372.png "微信图片_20180803220415.png")

![输入图片说明](https://images.gitee.com/uploads/images/2018/0803/221543_c1db84bd_621372.png "微信图片_20180803220419.png")

![输入图片说明](https://images.gitee.com/uploads/images/2018/0803/221555_cb7a9960_621372.png "微信图片_20180803220422.png")

![输入图片说明](https://images.gitee.com/uploads/images/2018/0803/221607_1c8c281d_621372.png "微信图片_20180803220430.png")

交流反馈
QQ 807758751

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)