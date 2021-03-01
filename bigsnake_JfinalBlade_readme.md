#JFinalBlade java开发平台
## 平台简介
JFinalBlade是是基于多个优秀的开源项目高度整合封装而成的快速开发平台。内置了 用户管理、 角色管理、 菜单管理、字典管理、部门管理、附件管理、参数管理、连接池监视、日志管理、代码生成等基础模块。是SpringBlade的 JFinal版本！

## 鸣谢
1.[SpringBlade](https://www.oschina.net/p/springblade)
2.[JFinal](https://www.oschina.net/p/jfinal)
3.[beetl](https://www.oschina.net/p/beetl)
4.[beetlsql](https://www.oschina.net/p/beetlsql)
5.[dreamlu](https://www.oschina.net/p/dreamlu)
6.[JFinalShiroPlugin](https://www.oschina.net/p/jfinalshiroplugin)

## 技术选型

1、后端

* 核心框架：JFinal
* 安全框架：Apache Shiro
* 服务端验证：Blade Validator
* 持久层框架：beetlsql
* 模板引擎：beetl
* 数据库连接池：Alibaba Druid
* 缓存框架：Ehcache
* 日志管理：SLF4J
* 工具类：Apache Commons、FastJson、JFinal-ueditor、BladeToolBox

2、前端

* JS框架：jQuery
* CSS框架：Bootstrap
* 客户端验证：JQuery-html5Validate
* 富文本：KindEditor、UEditor
* 数据表格：jqGrid
* 树结构控件：jQuery zTree
* 弹出层：Layer
* 日期控件： LayDate

## 部分后台界面
![后台界面](http://git.oschina.net/uploads/images/2016/1103/162134_4875c1d2_64709.png "后台界面")
![后台界面](http://git.oschina.net/uploads/images/2016/1103/162152_197d4be2_64709.png "后台界面")
![后台界面](http://git.oschina.net/uploads/images/2016/1103/162206_60005d2d_64709.png "后台界面")
![后台界面](http://git.oschina.net/uploads/images/2016/1103/162224_b80d40ad_64709.png "后台界面")

## 权限相关
1、配置文件 shiro.ini 配置默认规则
2、AdminBaseController 仅允许管理员访问
3、UrlPermissController 允许权限表中配置的权限
可根据需求继承上面两个Controller

注：
=======

jetty启动入口： com.ikkong.common.MainConfig.java
登陆名、密码 均为  admin




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)