# QuarkDoc

#### 介绍
QuarkDoc是一个极简主义的文档管理系统。适用于团队或个人管理文档，提升团队沟通成本（本人未来的迭代路线也将以文档管理及开发常用辅助功能为主）。

目前（beta）包含模块：团队人员管理，项目管理，目录管理，文档管理，辅助功能。

人员管理：权限为管理员和非管理员两者，非管理员将无法使用团队人员管理模块。

项目管理：非管理人员不可使用此模块。

目录管理：目录结构为3层可任意配置。

辅助功能：

1.Json数据格式验证

2.JSON参数转Url

3.Http模拟请求


#### 部署QuarkDoc

1.下载源码

2.发布Mins.QuarkDoc.Web

3.在SQL Server 2008及以上版本执行数据库创建脚本（Mins.QuarkDoc.Web项目DBScript文件夹下DBScript.sql文件）

4.修改Web.config文件下的数据库连接串

1    
2      
3    
5.程序可以执行，初始登录权限（后续可以在人员管理进行修改）

账号：jonins@admin.com

密码：admin@admin

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)