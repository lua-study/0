#### 介绍文档 | [部署文档](doc/BUILD.md) |  [初始化文档](doc/INIT.md)

![Spring Boot 2.2.5.RELEASE](https://img.shields.io/badge/Spring%20Boot-2.2.5.RELEASE-brightgreen.svg)
![Mysql 5.7](https://img.shields.io/badge/Mysql-5.7-blue.svg)
![JDK 1.8](https://img.shields.io/badge/JDK-1.8-brightgreen.svg)
![Maven](https://img.shields.io/badge/Maven-3.6.2-yellowgreen.svg)
![Redis](https://img.shields.io/badge/Redis-3.2-green.svg)
![Shiro](https://img.shields.io/badge/Shiro-1.5.1-lightgrey.svg)


# Novel简介
  一直想做一款后台管理系统，看了很多优秀的开源项目，从中发现了若依开源框架，从她出现以来就一直关注，但发现其中的功能太过强大，部分功能也不太适合自己，并且自己也一直想要动手学习一下若依的强大之处，便有了自己现在的novel。
 
  它可以用于所有的Web应用程序，如网站管理后台，网站会员中心，CMS，CRM，OA等等，当然，您也可以对她进行深度定制，以做出更强系统。所有前端后台代码封装过后十分精简易上手，出错概率低。同时支持移动客户端访问。系统会陆续更新一些实用功能。
       

# 内置功能


1.  用户管理：用户是系统操作者，该功能主要完成系统用户配置。
2.  部门管理：配置系统组织机构（公司、部门、小组），树结构展现支持数据权限。
3.  岗位管理：配置系统用户所属担任职务。
4.  菜单管理：配置系统菜单，操作权限，按钮权限标识等。
5.  角色管理：角色菜单权限分配、设置角色按机构进行数据范围权限划分。
6.  操作日志：系统正常操作日志记录和查询；系统异常信息日志记录和查询。
7.  登录日志：系统登录日志记录查询包含登录异常。
8.  服务监控：监视当前系统CPU、内存、磁盘、堆栈等相关信息。
9.  在线用户：当前系统中活跃用户状态监控。
10. 连接池监视：监视当前系统数据库连接池状态，可进行分析SQL找出系统性能瓶颈。
11. 定时任务：在线（添加、修改、删除)任务调度包含执行结果日志。

# 在线体验

前端项目地址：[Novel-vue](https://gitee.com/cnovel/Novel-vue)

演示地址：[http://cnovel.club](http://cnovel.club)


# 演示图

| ![用户登录](https://oscimg.oschina.net/oscnet/up-4fc9e90ab9a427415b2a231d647bb6682b4.png "用户登录") | ![系统首页](https://oscimg.oschina.net/oscnet/up-f5f91451165f3d0dcfdcab9482ab867c09f.png "系统首页") |
| ------------ | ------------ |
| ![用户管理](https://oscimg.oschina.net/oscnet/up-3914e348f499598c26aba4b7c92ad5ce8bb.png "用户管理") | ![用户编辑](https://oscimg.oschina.net/oscnet/up-f24997c68d622dc9b2d079ef24da9919d17.png "用户编辑") |
| ![角色管理](https://oscimg.oschina.net/oscnet/up-a0604715ea922b9cc06cc7ebf5e9d874159.png "角色管理") | ![角色编辑](https://oscimg.oschina.net/oscnet/up-8f24ea94aec59ff494d205254ec9f04ad2c.png "角色编辑") |
| ![菜单管理](https://oscimg.oschina.net/oscnet/up-fb682a64f33692c7fe95befcc83b484f02f.png "菜单管理") | ![菜单编辑](https://oscimg.oschina.net/oscnet/up-ce248e9ea710d4b39969400a5c485cf19a2.png "菜单编辑") |
| ![岗位管理](https://oscimg.oschina.net/oscnet/up-d962e260fdcd43929ff5e8664a00b9ebf2e.png "岗位管理") | ![岗位编辑](https://oscimg.oschina.net/oscnet/up-deac57b7fae4d300bf64267fe9d4408f1d1.png "岗位编辑") |
| ![部门管理](https://oscimg.oschina.net/oscnet/up-a87d3c402fc59b075d11749860043af78f4.png "部门管理") | ![部门编辑](https://oscimg.oschina.net/oscnet/up-c9663b06835ac73f523409c14d65f8d1b85.png "部门编辑") |
| ![操作日志](https://oscimg.oschina.net/oscnet/up-51c244b113d1fe11e51c5e8db36c27baf83.png "操作日志") | ![日志详情](https://oscimg.oschina.net/oscnet/up-12952a8957a15b8e7fb0d9cebe219c6e093.png "日志详情") |
| ![登录日志](https://oscimg.oschina.net/oscnet/up-04f46761918f952cf8df0dc56b09672e69e.png "登录日志") | ![服务监控](https://oscimg.oschina.net/oscnet/up-257213ddf2fcbf090f15a2f3573eff2b566.png "服务监控") |
| ![在线用户](https://oscimg.oschina.net/oscnet/up-0b0ab18325a221e68057be0baabea481602.png "在线用户") | ![数据监控](https://oscimg.oschina.net/oscnet/up-762373c8e139d6512c4f0c64269a5d55c19.png "数据监控") |
| ![个人信息](https://oscimg.oschina.net/oscnet/up-172e7b0f0140f82b11f4929e8af9b33aac5.png "个人信息") | ![编辑头像](https://oscimg.oschina.net/oscnet/up-4583a5fb165131316c90e4793089755f896.png "编辑头像") |
| ![定时任务](https://oscimg.oschina.net/oscnet/up-643bc6ea5ff8a9bcd1d8b5b6245ab2ed311.png "定时任务") | ![任务日志](https://oscimg.oschina.net/oscnet/up-553b0665d66ec17b0624361d6216cbbf84e.png "任务日志") |

# 捐赠支持

开源项目不易，若此项目能得到你的青睐，可以捐赠支持作者持续开发与维护。
 ![收款码](https://oscimg.oschina.net/oscnet/up-e2344cd770f7f7386637d0dbbfb5d48472c.JPEG)


**另：**

本人还有一个开源项目，是该项目中菜单管理中使用的图标组件，喜欢的可以去看看，帮忙点个`star`  [e-icon-picker](https://gitee.com/cnovel/e-icon-picker),非常感谢！


**演示图**

![示例图片](https://oscimg.oschina.net/oscnet/up-bf411d272ce969c1d5be9dc1ea12a8969ea.JPEG "示例图片")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)