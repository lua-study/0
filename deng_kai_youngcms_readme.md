
### youngcms

   基于SSM框架的内容管理系统，采用最新最主流的技术，后端采用spring boot,mybatis-plus,freemaker，shiro，redis，mysql，DWZ等技术,主要功能：消息队列，权限控制，自定义工作流，扩展模型，内容管理，通用日志记录等。



### 演示

   前端：http://www.youngcms.com

   后端：http://admin.youngcms.com/admin/index   用户名：admin 密码：123456



### 后端：



- JDK：1.8
- 数据库：Mysql
- 项目构建工具：Maven
- MVC框架：SpringBoot 1.5.3.RELEASE
- ORM框架：MyBatisPlus
- 缓存：Redis 2.8.12
- 消息队列： Redis实现
- JSON工具：Fastjson 1.2.29
- 数据库连接池：Druid 1.0.15
- 模板引擎：Freemarker 2.3.23
- 权限管理：ApacheShiro 1.3.2

* * *

### 前端：
- jQuery插件：ztree，ueditor，Ajax upload
- 页面展现：DWZ框架



### 搭建步骤

1. 创建数据库。如使用MySQL，字符集选择为utf8或者utf8mb4（支持更多特殊字符，推荐）。
1. 执行数据库脚本。数据库脚本在database目录下。
1. 在eclipse中导入maven项目。点击eclipse菜单File - Import，选择Maven - Existing Maven Projects。创建好maven项目后，会开始从maven服务器下载第三方jar包（如spring等），需要一定时间，请耐心等待。
1. 修改数据库连接。打开/src/main/resources/application.properties文件，根据实际情况修改jdbc.url、jdbc.username、jdbc.password的值。
1. 运行程序。运行MainApplicion.java
1. 访问系统。后台地址：http://localhost:8081/admin/index，用户名：admin，密码：123456。



 >>>>>> dev
### 后端截图

![输入图片说明](https://git.oschina.net/uploads/images/2017/0809/181259_8bd141d7_142850.png "2017-08-09_175709.png")

![输入图片说明](https://git.oschina.net/uploads/images/2017/0809/181308_7af9d3e0_142850.png "2017-08-09_175741.png")

![输入图片说明](https://git.oschina.net/uploads/images/2017/0809/181318_e57d4996_142850.png "2017-08-09_175805.png")



### 前端截图

 >>>>>> dev


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)