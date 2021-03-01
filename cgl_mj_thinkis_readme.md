# thinkis

### 使用过程中有问题的进群讨论：104777913

#### 我的网站 [www.ithinkis.cn](http://www.ithinkis.cn)基于thinkis实现

#### 项目介绍
thinkis是一套由jeesite 1.2.7改造而来的项目框架，将原来的jeeiste拆分成多模块项目，舍弃掉原jeesite前端框架。改为了beetl和layui组合。
模块拆分为：

1、thinkis-act:工作流模块

2、thinkis-api:api模块，集成jwt和swagger2,该模块用来做api的开发，可以给app提供接口开发。

3、thinkis-cms：内容管理模块

4、thinkis-core:系统核心模块，包含系统基础功能

5、thinkis-gen:代码生成模块

6、thinkis-miniapp:小程序集成开发模块

7、thinkis-web：前端页面模块

8、thinkis-weixin:微信公众号集成开发模块

以上模块可以灵活依赖，最小只需要thinkis-core和thinkis-web两个模块即可。包含系统基础功能（用户管理、机构管理、区域管理、菜单管理、角色管理、字典管理、操作日志、连接池监视）

#### 内置功能

用户管理：用户是系统操作者，该功能主要完成系统用户配置。

机构管理：配置系统组织机构（公司、部门、小组），树结构展现，可随意调整上下级。

区域管理：系统城市区域模型，如：国家、省市、地市、区县的维护。

菜单管理：配置系统菜单，操作权限，按钮权限标识等。

角色管理：角色菜单权限分配、设置角色按机构进行数据范围权限划分。

字典管理：对系统中经常使用的一些较为固定的数据进行维护，如：是否、男女、类别、级别等。

操作日志：系统正常操作日志记录和查询；系统异常信息日志记录和查询。

连接池监视：监视当期系统数据库连接池状态，可进行分析SQL找出系统性能瓶颈。

工作流引擎：实现业务工单流转、在线流程设计器

#### 技术选型
1、后端

核心框架：Spring Framework 4.3.6

安全框架：Apache Shiro 1.2

视图框架：Spring MVC 4.3.6

服务端验证：Hibernate Validator 5.2

工作流引擎：Activiti 5.21

任务调度：Spring Task 4.1

持久层框架：MyBatis 3.4.2

数据库连接池：Alibaba Druid 1.0

缓存框架：Ehcache 2.6、Redis

日志管理：SLF4J 1.7、Log4j

工具类：Apache Commons、Jackson 2.2、Xstream 1.4、Dozer 5.3、POI 3.9


2、前端

前端框架：layui2.4。

富文本在线编辑：uEditor

模板解析：beetl 2.8.2


3、平台

服务器中间件：在Java EE 5规范（Servlet 3、JSP 2.1）下开发，支持应用服务器中间件 有Tomcat 6+、Jboss 7+、WebLogic 10+、WebSphere 8+。

数据库支持：目前仅提供MySql和Oracle数据库的支持，但不限于数据库，平台留有其它数据库支持接口， 你可以很方便的更改为其它数据库，如：SqlServer 2008、MySql 5.5、H2等

开发环境：Java、Eclipse Java EE 4.3、Maven 3.1、Git

#### 系统界面
![登录界面](https://images.gitee.com/uploads/images/2018/1103/164742_5d37af58_874185.png "登录界面.png")
![桌面](https://images.gitee.com/uploads/images/2018/1103/165404_8b8a64f1_874185.png "桌面.png")
![个人信息](https://images.gitee.com/uploads/images/2018/1103/165428_1ebc0a3e_874185.png "个人信息.png")
![素材管理](https://images.gitee.com/uploads/images/2018/1103/165451_9fcf7ad2_874185.png "素材管理1.png")
![内容管理](https://images.gitee.com/uploads/images/2018/1103/165510_1dc2d5f4_874185.png "内容管理.png")
![系统管理](https://images.gitee.com/uploads/images/2018/1103/165528_7872aab9_874185.png "系统管理.png")
![代码生成](https://images.gitee.com/uploads/images/2018/1103/165540_2ddae357_874185.png "代码生成.png")
![网站](https://images.gitee.com/uploads/images/2018/1103/165622_4ddfdedd_874185.png "企业网站.png")

#### 感谢以下项目作者
1、jeesite1.x

2、layui

3、kit-admin


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)