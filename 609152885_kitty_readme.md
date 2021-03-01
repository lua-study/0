# kitty

### 在线演示
演示地址：http://139.196.87.48:9002/kitty

用户名：admin 密码：admin

温馨提示：
有在演示环境删除数据的童鞋们，如果可以的话，麻烦动动小指，右键头像菜单，
选择 -> 备份还原 帮忙恢复到系统默认备份数据，方便后来的童鞋查看，谢谢啦。

### 博客教程
本人技术博客提供同步系列文章教程

[Spring Boot + Spring Cloud 实现权限管理系统 后端篇](https://www.cnblogs.com/xifengxiaoma/p/9474953.html)

[Vue.js + Element UI 实现权限管理系统 前端篇](https://www.cnblogs.com/xifengxiaoma/p/9533018.html)

### 项目介绍

- Kitty是基于Spring Boot、Spring Cloud、Vue、Element实现的Java快速开发平台。
- 目标是搭建出一套简洁易用的快速解决方案，可以帮助用户有效降低项目开发难度和成本。
- 个人博客提供本项目开发过程同步系列教程文章，手把手的教你如何开发同类系统。

### 功能计划
- 登录注册：登录注册，第三方登录（QQ、微信、微博）
- 用户管理：新建用户，修改用户，删除用户，查询用户
- 机构管理：新建机构，修改机构，删除机构，查询机构
- 角色管理：新建角色，修改角色，删除角色，查询角色
- 菜单管理：新建菜单，修改菜单，删除菜单，查询菜单
- 字典管理：新建字典，修改字典，删除字典，查询字典
- 日志管理：记录用户操作日志，查看系统执行日志
- 数据权限：结合用户机构关系，实现数据权限功能
- 数据监控：定制Druid信息，提供有效的SQL监控
- 单点登录：利用 OAuth2, 提供统一的单点登录功能
- 聚合文档：定制在线文档，提供简洁美观的API文档
- 微服务化：结合Spring Cloud，实现系统微服务化
- 服务监控：结合微服务治理，实现服务的全方位监控
- 服务限流：结合微服务治理，实现有效的服务限流
- ...

### 软件架构

#### 后端架构

##### 开发环境

- IDE : eclipse 4.x
- JDK : JDK1.8.x
- Maven : Maven 3.5.x
- MySQL: MySQL 5.7.x

##### 技术选型

- 核心框架：Spring Boot 2.x
- 安全框架：Apache Shiro 1.4.x
- 视图框架：Spring MVC 5.x
- 持久层框架：MyBatis 3.x
- 定时器：Quartz 2.x
- 数据库连接池：Druid 1.x
- 日志管理：SLF4J、Log4j

##### 项目结构

- kitty-common： 公共代码模块，主要放置工具类
- kitty-core： 核心代码模块，主要封装公共业务模块
- kitty-admin： 后台管理模块，包含用户、角色、菜单管理等
- kitty-backup： 系统数据备份备份模块，可选择独立部署
- kitty-monitor： 系统监控服务端，监控Spring Boot服务模块

#### 前端架构

##### 开发环境

- IDE : VS Code 1.27
- NODE: Node 8.9.x
- NPM : NPM 6.4.x

##### 技术选型

- 前端框架：Vue 2.x
- 页面组件：Element 2.x
- 状态管理：Vuex 2.x
- 后台交互：axios 0.18.x
- 图标使用：Font Awesome 4.x

##### 项目结构

kitty-ui
- assets： 图标、字体、国际化信息等静态信息
- components： 组件库，对常用组件进行封装
- http： 后台交互模块，统一后台接口请求API
- i18n： 国际化模块，使用Vue i18n进行国际化
- mock： Mock模块，模拟接口调用并返回定制数据
- permission： 权限控制模块，处理权限认证逻辑
- router： 路由管理模块，负责页面各种路由配置
- store： 状态管理模块，提供组件间状态共享
- utils： 工具模块，提供一些通用的工具方法
- views： 页面模块，主要放置各种页面视图组件


### 安装教程

#### 后端安装

1. 下载源码

    git clone https://gitee.com/liuge1988/kitty.git

2. 导入工程

    使用 Eclipse导入 Maven 项目，在此之前请确认已安装 JDK 和 Maven 工具。

3. 编译代码

    找到 kitty-monitor 工程的 pom.xml，执行 maven clean install 命令编译打包。
    
    找到 kitty-admin 工程的 pom.xml，执行 maven clean install 命令编译打包。

    找到 kitty-backup 工程的 pom.xml，执行 maven clean install 命令编译打包。

4. 导入数据库

    新建 kitty 数据库，导入 kitty-admin 工程 doc 下的 SQL 脚本，导入初始化数据库。
    修改 kitty-admin 下 application.yml 中的数据库连接和账号密码为自己的数据库配置。

5. 启动系统

    找到 kitty-monitor 工程下的 KittyMonitorApplication, 执行 Java 程序，启动项目。

    找到 kitty-admin 工程下的 KittyAdminApplication, 执行 Java 程序，启动项目。

    找到 kitty-backup 工程下的 KittyBackupApplication.java, 执行 Java 程序，启动项目。
    
    注意：监控服务器 monitor 要先启动，其他无所谓。

#### 前端安装

1. 下载源码

    git clone https://gitee.com/liuge1988/kitty-ui.git

2. 编译代码

    进入项目根目录，执行 npm install, 下载安装项目依赖包。

3. 启动系统

    执行 npm run dev 命令，启动项目，通过 http://localhost:8090 访问。

4. 项目打包

    执行 npm run build 命令，启动打包，完成之后会生成 dist 目录。

5. Mock 开关

    通过修改src/mock/index.js中的openMock变量，可以一键开启或关闭Mock功能。

6.修改配置

    如果想自定义端口（默认是8090），可以修改 config/index.js 下的 port 属性。

    后台服务器和备份服务器地址配置在 src/utils/global.js 文件中个，按需修改。

#### 系统展示

##### 登录界面

![输入图片说明](https://images.gitee.com/uploads/images/2018/1011/172530_fd14977c_645970.png "屏幕截图.png")

##### 用户管理

![输入图片说明](https://images.gitee.com/uploads/images/2018/1011/172505_51c77c5a_645970.png "屏幕截图.png")

##### 机构管理

![输入图片说明](https://images.gitee.com/uploads/images/2018/1011/172625_e0e99bc7_645970.png "屏幕截图.png")

##### 角色管理

![输入图片说明](https://images.gitee.com/uploads/images/2018/1011/172658_1b438eb2_645970.png "屏幕截图.png")

##### 菜单管理

![输入图片说明](https://images.gitee.com/uploads/images/2018/1011/172716_7a5a26a9_645970.png "屏幕截图.png")

##### 字典管理

![输入图片说明](https://images.gitee.com/uploads/images/2018/1011/172729_4fd54dbe_645970.png "屏幕截图.png")

##### 系统日志

![输入图片说明](https://images.gitee.com/uploads/images/2018/1011/172747_719d67a0_645970.png "屏幕截图.png")

##### 系统监控

用户名：admin, 密码:admin，即服务端配置的密码

![输入图片说明](https://images.gitee.com/uploads/images/2018/1011/172830_5e3e1daa_645970.png "屏幕截图.png")

##### 接口文档

![输入图片说明](https://images.gitee.com/uploads/images/2018/1011/172928_f63c7f63_645970.png "屏幕截图.png")

##### 主题切换

![输入图片说明](https://images.gitee.com/uploads/images/2018/1011/173415_ef0dc20b_645970.png "屏幕截图.png")

### 使用说明

1. xxxx
2. xxxx
3. xxxx

### 参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


### 码云特技

1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [http://git.mydoc.io/](http://git.mydoc.io/)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)