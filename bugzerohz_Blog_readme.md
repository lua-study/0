# Blog

#### 介绍
个人博客网站

#### 软件架构
网站使用的是.Net Core 2.2、Redis、Autofac、layui开发，由于前端能力有限，所以没有使用前后端分离，博客基本功能已经全部完成（相关操作日志和异常已经记录到数据库，没有做展示页面）
[博客地址](https://www.miboxapp.com) https://www.miboxapp.com
[后台地址](https://[输入链接说明](https://www.miboxapp.com/main)) https://www.miboxapp.com/main
后台登录用户名/密码：root/123456
 :grin: 由于博客已经正式上线，所以只开放了预览权限


#### 使用说明

1. 网站使用的sqlsugar ORM开源框架，相关文档请查看官网[sqlsugar框架](http://www.codeisbug.com/)，数据库使用的是mysql，ORM支持5种数据库（MySql、SqlServer、Sqlite、Oracle、Postgresql），所以可以随意切换，具体请看sqlsugar官网文档
2. 数据库设计以及备份和SQL文件放在AppSoft网站下的db目录下,项目中后台管理员登录用户名/密码:admin/admin1024
3. 写代码都有详细注释，这里就不一一介绍
4. 创建数据库后记得修改appsetting.json文件中的数据库连接字符串，以及Configs文件夹下的nlog.config的数据库连接字符串
5. 在Linux部署注意事项，后台登录验证码使用的是ZKWeb.System.Drawing，所以在Linux上需要安装相关依赖，详细信息请参考作者说明[ZKWeb.System.Drawing](https://github.com/zkweb-framework/zkweb.system.drawing)
6. 博客中使用Redis缓存，如果要使用Redis缓存功能请先安装Redis，在 AppSoft根目录appsettings.json中配置Redis连接字符串
7. 记录文本日志（数据库日志）使用NLOG
8. 接入QQ授权登录留言评论

如果有什么BUG还希望大家提交到Issues，我看到会及时修复。

前台预览
![前台预览](https://images.gitee.com/uploads/images/2019/0122/094841_7b096768_967952.png "37℃空间-个人博客.png")

后台预览![后台预览](https://images.gitee.com/uploads/images/2019/0122/095015_2d0d64ad_967952.png "后台管理系统.png")



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)