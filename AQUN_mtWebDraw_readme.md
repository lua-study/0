# mtWebDraw

# Web绘流系统 - 系统使用说明
本项目为Web版流程图绘图，兼容IE、FF、Chrome等各主流浏览器，提供了各类基础图形，至于如何应用及用来做什么就随各位了，常规的流程图及逻辑辅助、工作流等皆可胜任。本系统虽为开源项目，然精心调配开发测试，有完善的日志记录信息，逻辑和性能皆可，非Demo类、功能类无日志、难移植、难维护、难二次开发的项目可比，请放心使用，本人会对此项目持续维护较长时间。

附件中有数据库备份文件和网站发布包可直接下载使用。

使用中有任何BUG，欢迎反馈给我，请发往邮箱：mkwuji@yeah.net。大家可引用、移植、闭包。绘图底层使用的mxGraph，已完美破解，然请大家遵守其相关协议，不要公开商用，被追究本人概不负责。 :smile: 

在线体验地址(用户名admin 密码mt)（去掉s亦可）：https://drawexp.freedomchat.top/

备用体验地址：http://47.100.253.206:8001/

先来张宣传图，后跟一分钟使用图解。
![mtWebDraw宣传图](https://gitee.com/uploads/images/2018/0525/073617_39fe8d22_1683949.png "xuanchuantu.png")

# 操作基础
1、表格内数据行皆可双击以执行最常用操作、在数据行上右键以调出右键菜单执行常规操作

2、鼠标移入行标题则每个标题右侧的下拉菜单可正序倒序排列，并显示隐藏指定行，行可拖动以调整前后顺序

3、部分表格内行数据支持直接行上编辑（同下流程图授权说明时见）

4、表格内行展开内容复制（同下流程图日志复制源码时见）

# 一分钟使用图解

1、登陆（默认用户名admin，默认密码mt）
![mtWebDraw登陆](https://gitee.com/uploads/images/2018/0525/073422_1f9d58a2_1683949.png "10.png")

2、部门管理
![mtWebDraw部门管理](https://gitee.com/uploads/images/2018/0525/073433_6fb7f20f_1683949.png "20.png")

3、用户管理
![mtWebDraw用户管理](https://gitee.com/uploads/images/2018/0525/073608_c7874cc2_1683949.png "101.png")
左右表格内数据行皆可双击以执行最常用操作、在数据行上右键以调出右键菜单执行常规操作。

4、流程图管理
![mtWebDraw流程图管理](https://gitee.com/uploads/images/2018/0525/073443_b33a2bec_1683949.png "40.png")
右侧显示所有用户流程图的三个菜单仅在以超级管理员登陆时显示。

5、流程图授权
![mtWebDraw流程图授权](https://gitee.com/uploads/images/2018/0525/073449_a5050d48_1683949.png "50.png")
表格内行数据支持直接行上编辑，点击行数据的授权码列可显示下拉权限列表，直接在各行下拉列表中选择所需的权限全部完成后点击提交即可，更改后未提交左上角有红色小三角标。

6、流程图绘图
![mtWebDraw流程图绘图](https://gitee.com/uploads/images/2018/0525/073532_4d0c613c_1683949.png "60.png")
![mtWebDraw流程图绘图](https://gitee.com/uploads/images/2018/0525/073541_5ae41e30_1683949.png "65.png")
![mtWebDraw流程图绘图](https://gitee.com/uploads/images/2018/0525/073549_8c93272f_1683949.png "67.png")
图形可直接另存为新图形以存留原图形而在新图形中编辑，另存为旁边增加了Download Diagram As Html、Download Diagram Code As Text两个实用按钮。

1）Download Diagram As Html：将当前图形下载为单html形式，方便传播，单html打开即为图形形态。

2）Download Diagram Code As Text：将当前图形图形源码下载为txt，可随时再通过Parse XML于任意图形中还原，适用于高度机密时只使用图形展示而不存留源码和历史版本。

3）左下角的定位框可方便查看超大图时局部内容，当然您也可以通过Zoom菜单缩小后查看全图，注意图形左上角图形名称边上的*号，代表当前图形信息没有保存。

7、流程图日志
![mtWebDraw流程图日志](https://gitee.com/uploads/images/2018/0525/082108_4b46ecff_1683949.png "70.png")
展开行复制图形源码至新建图形以Parse XML显示出来以追踪日志，因另存为功能的使用日志功能从未见人用过，故不做精细实现。

# 备注
其它功能等待大家自行使用中探索，操作权限介绍请查看：菜单“系统信息”下“系统介绍”。

备1：在Web.config中有SysAdminUserName配置节，值为admin，改为你要定义为超级管理员的用户用户名即可，用户名需用admin先行建好。

备2：下载源码的，在/Resources/PDM下有数据库模型和生成好的SQL文件，mtTools.dll来自本人开源的另一个类库项目。

# 布署
1、于附件中将mtWebDraw.mdf.bak下载至要布署的数据库目标服务器，执行还原数据库操作

2、于附件中将mtWebDrawV1.0.0.0.rar下载至要布署的Web目标服务器并解压，后于IIS上创建站点，.net4.5集成模式的应用程序池，站点指向解压的文件夹

3、修改Web.config配置：

	1）appSetting中nhConfigPath指向的hibernate.cfg.xml的数据库连接字符串需改为自己的配置（如不使用sa请注意为库设置帐号权限）

	2）system.web中sessionState可选启用以确定用户登陆超时时长


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)