#概述
1.	本工程是[archer-framework](http://git.oschina.net/ArcherGroup/archer-framework)，以[archer-application-core](http://git.oschina.net/ArcherGroup/archer-application-core)提供的API为数据来源的一套后台管理系统。
2.	本工程只负责界面展现。

#界面截图
![菜单管理](/snapshot/menu.png "菜单管理")

![角色列表](/snapshot/role.png "角色列表")

![角色详情](/snapshot/roleDetail.png "角色详情")

# 相关项目
| 名称           | 说明            |
| ------------- |-------------|
| [archer-framework](http://git.oschina.net/ArcherGroup/archer-framework)        | `archer-framework`是一个旨在构建RESful风格WEB服务的轻量级框架        |
| [archer-application-core](http://git.oschina.net/ArcherGroup/archer-application-core)        | 使用`archer-framework`做的服务工程演示，一个简单的用户角色权限管理系统，对外只提供API        |

#  主要技术
-	css：`bootstrap` `AdminLTE`
-	js: `vue` `jquery`


# 如何启动
1.	本工程依赖于`archer-framework`,所以请先install `archer-framework`
2.	本工程依赖于`archer-application-core`提供的接口，所以请先启动`archer-application-core`工程
3.	运行`test/DevelopmentStarter.java`启动整个工程。
4.	使用admin/123456用户登录
5.	enjoy :)

# 常见FAQ

> IE兼容性如何？
>> 因为这是后端管理系统，采用的是`vue`，而`vue`支持IE9+，所以该工程也支持IE9+。

> 为什么选用`vue`而不是`angular`？
>> `vue`简单易用，且`angular2`尚未正式发布。

>我在使用中发现了bug，我要如何报告这个bug？
>> 你可以在git上提交issue，说明问题的现象，错误日志等，我们会在第一时间予以排查和修复。


#	特别鸣谢
- [AdminLTE](https://github.com/almasaeed2010/AdminLTE)   极好的bootstrap的后台管理界面皮肤

- [vue.js](https://github.com/vuejs/vue) 国人参与的MVVM js库，确实比angular.js简单

- [bootstrap-table](https://github.com/wenzhixin/bootstrap-table) 国人写的table组件，最近还有vue版本出现，个人觉得比datatables简单易用

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)