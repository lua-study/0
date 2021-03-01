# Daffodil（达佛）基础管理平台`免费开源`
一个简单、快速、易读的maven项目

本人出生地水仙花之都【[漳州](http://www.zhangzhou.gov.cn/)】

Daffodil英文翻译意思是水仙花，本人也比较佛系且Daffodil音含 [ 达佛 ] 于是就叫“达佛基础管理平台”

#### 介绍
本系统是基于SpringBoot的后台管理系统 易读易懂、界面简洁美观。 采用技术SpringBoot、Hibernate、Shiro、Flowable、thymeleaf等。

系统基础包括：用户管理、角色管理、部门管理、岗位管理、权限管理、菜单管理、字典管理、约束管理、参数配置、通知公告、日志管理、工作流管理、任务管理、流程演示、系统监控等模块...

#### 软件架构
软件架构说明
- 核心框架：Spring Boot
- 安全框架：Apache Shiro
- 持久层框架：Hibernate
- 工作流引擎：flowable
- 模板引擎：Thymeleaf
- 前端技术：bootstrap、layui、fontawesome等

#### 安装教程

以myeclipse开发工具为例：
1.  将项目检出并导入到你的工作空间。
2.  修改daffodil-starter启动项目的数据库资源配置文件application-datasource.properties的数据源配置。
3.  运行DaffodilApplication，如果不出意外正常启动成功。
4.  访问系统[http://127.0.0.1:8080/] 超级管理员账号：admin 密码：123456，点击登录愉快的玩耍吧！

--备注：
1.  第一次启动成功后，请注释掉daffodil-starter启动项目DaffodilApplication类的main()方法中的init()初始化方法。
2.  可以修改daffodil-flowable项目的application-flowable.properties的数据库更新策略database-schema-update=true（仅第一次运行的时候），后续为了提高性能可设置为false。
3.  目前系统只准备了Mysql的初始化数据。如果你想用SqlServer或者Oracle，那么你可以自行手动将Mysql的数据库基础数据导入到SqlServer或者Oracle数据库中，接下来请修改配置文件的数据库驱动driver-class和数据库方言database-platform。

#### 使用说明

1.  目前系统还处于持续开发中，如果存在一些bug请见谅，麻烦你在Issuses上反馈bug问题，后续我会跟进修复。

#### 系统效果
![输入图片说明](https://images.gitee.com/uploads/images/2020/0210/132019_10988e30_332368.jpeg "TIM截图20200210131544.jpg")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0210/132037_716e9d85_332368.jpeg "TIM截图20200210131456.jpg")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0210/132048_998e75bc_332368.jpeg "TIM截图20200210131456.jpg")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0210/132102_b9c4fe4b_332368.jpeg "TIM截图20200210131605.jpg")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0210/132111_0ecb7171_332368.jpeg "TIM截图20200210131633.jpg")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0210/132139_7d345354_332368.jpeg "TIM截图20200210131705.jpg")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0210/132150_880273be_332368.jpeg "TIM截图20200210131901.jpg")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0210/132203_e0a8a623_332368.jpeg "TIM截图20200210131914.jpg")
![输入图片说明](https://images.gitee.com/uploads/images/2020/0210/132214_64b22b91_332368.jpeg "TIM截图20200210131948.jpg")

#### 参与贡献

1.  Fork 本仓库
2.  新建 Feat_xxx 分支
3.  提交代码
4.  新建 Pull Request


#### 码云特技

1.  使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2.  码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3.  你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4.  [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5.  码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6.  码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)