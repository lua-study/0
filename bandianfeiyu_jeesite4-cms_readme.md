# jeesite4-cms

#### 项目介绍

JeeSite4 CMS 内容管理模块

该模块目前仅完成了后台 站点管理、栏目管理、在线模板管理、内容发布的基础添加删除管理。 封装了mysql 的初始化脚本（暂不支持其他数据库）。
具体设计，请参考db-cms.erm


 **项目目前完成度70%, 前端+cms自定义标签** 

#### 软件架构
软件架构说明


#### 安装教程

1. IDE导入Maven工程jeesite4-cms
2. 执行com.jeesite.test.InitCoreData中initCoreData()方法
3. 执行jeesite-module-cms模块db目录下init-cms.sql，init-cms-data.sql


数据库初始化说明：
1. 导入CMS数据库结构初始化语句：init-cms.sql
2. 导入CMS模块 字典表初始化语句：init-cms-data.sql
3.  模块安装请参考 B站视频教程 ：JeeSite4.0 如何创建新模块？
	https://space.bilibili.com/383413957/channel/index



# JeeSite 4.0 企业信息化快速开发平台

## 配套视频教程

https://ke.qq.com/course/376588?tuin=c55da0ad

视频教程QQ群1：866607936

## JeeSite-module-cms UI

https://adminlte.io/
https://www.pikeadmin.com/demo/charts.html

## JeeSite-module-cms Bug
01. sql bug。
mssql：
Reserved word is used as the column name. Table name : js_cms_site 。
Reserved word is used as the column name. Table name : js_cms_article。
postgresql：
Reserved word is used as the column name. Table name : js_cms_guestbook。


## SiteMesh 3.0.1
http://wiki.sitemesh.org/wiki/display/sitemesh3/Getting+Started+with+SiteMesh+3
## Bootstrap UI  
MIT license

Themes for Bootstrap https://bootswatch.com
https://bootswatch.com/



## JeeSite-module-cms UI 皮肤框架参考

1. https://adminlte.io/
2. https://www.pikeadmin.com/demo/charts.html

## JeeSite-module-cms Bug
1. mssql bug：
Reserved word is used as the column name. Table name : js_cms_site 。  
Reserved word is used as the column name. Table name : js_cms_article。
2. postgresql bug： 
Reserved word is used as the column name. Table name : js_cms_guestbook。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)