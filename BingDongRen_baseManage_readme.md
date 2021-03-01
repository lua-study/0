基于JFinal3.3的后台业务框架通用模块，包括系统权限模块、APP版本管理、日志管理、数据字典等
### 使用的技术要点
- 后端使用JFinal3.3
- 权限、会话管理采用 shiro 1.2.4 完成
- 前端页面是基于acev1.3模板改造的，更方便后台人员操作
- 页面是html,使用jfinal的模板引擎
- 扩展jfinal engine支持 shiro 标签
- 前端使用到的框架都是基于jquery
- 部分框架有：树框架zTree,表格框架jqGrid,校验框架jquery.validate.js,弹出层框架layer.js


### 使用步骤
- 在你本地创建baseManage数据库，再导入db/baseManage.sql，在 profile.dev.properties/profile.sit.properties 配置文件对应更改你的数据库连接相关参数
- 用eclipse选择以maven的方式导入项目
- 运行项目，执行com.basemanage.conf.MainConfig.java 即可，本地访问地址 http://127.0.0.1:8090 开始登陆
- 默认系统用户名为admin,密码123456
- 演示地址：http://dev.yumj.xyz 用户名为admin,密码123456
![输入图片说明](https://gitee.com/uploads/images/2018/0125/135941_c76c414f_1338450.png "20180125135832.png")


   
### 代码生成使用步骤（通过代码生成快速完成模块基础增删改查功能，示例：测试管理）
- 运行_TppTest.java的main方法，刷新项目
- com.basemanage.controller.test 该目录下的Test.java 文件 移动覆盖掉  com.basemanage.model下的Test.java 文件
- src/main/webapp/WEB-INF/generate 目录下的test文件夹 移动到view目录下
- com.basemanage.conf目录下的AdminRoutes.java 中 配置路由      add("/test", TestController.class, "/test");
- 运行项目，执行com.basemanage.conf.MainConfig.java 即可，本地访问地址 http://127.0.0.1:8090 开始登陆
- 系统管理资源管理配置资源访问路径 			 
- ![输入图片说明](https://gitee.com/uploads/images/2018/0125/115905_7d19229b_1338450.png "20180125115846.png")
- 刷新页面，左侧菜单已有 测试管理菜单，测试列表 功能 。注：搜索是模糊搜索字段“普通输入字段”

![输入图片说明](https://gitee.com/uploads/images/2018/0125/135453_1f01cf79_1338450.png "20180125135443.png")
	 





 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)