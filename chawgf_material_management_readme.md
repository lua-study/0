# 物资管理系统
项目负责人：常州-_陈默，在QQ群797192690里。

项目预览地址：[wuzi.m3w.cn](https://wuzi.m3w.cn) 

安卓APP地址： [https://pan.baidu.com/s/1G21VzFDPCKXb8NslxsyejQ](https://pan.baidu.com/s/1G21VzFDPCKXb8NslxsyejQ) 提取码: wvja 

体验账户用户名：13800138000；密码：123456。此地址为测试体验地址，具体某单位上线时，需要单独部署。

![输入图片说明](https://images.gitee.com/uploads/images/2020/0215/101737_9fb331ec_5529724.png "物资管理系统.png")

本项目是基于木兰宽松许可证的开源项目，代码全部开源，开发者可自由使用其中的代码，自己部署相关的系统。

#### 介绍
新型冠状病毒疫情期间抗疫相关物料的管理系统，领用、派发记录，库存查询统计。

#### 功能
物资入库：包括捐赠物资、上级下拨物资、自行采购物资

物资发放：物资直接发放、物资发放型号、数量、领取时间、领取人信息

物资库存：查看物资剩余库存

#### 界面及其详细功能细节

[初步详细设计界面](https://free.modao.cc/app/587de5304407459d3e4b163cd97ae854d56bb7ab)

##  项目运行说明

1. 下载HBuilderX

本项目需要HBuilderX 2.5.11以上版本才能运行。**切记看清版本号，要最新alpha版**

[下载地址]((https://www.dcloud.io/hbuilderx.html))

![输入图片说明](https://images.gitee.com/uploads/images/2020/0213/022916_c822f4df_1628277.png "hx下载.png")

下载时选alpha版。然后根据自己的操作系统下载，下载标准版即可，运行项目时会自动安装依赖的插件。

HBuilderX是绿色的，Windows版解压后直接运行里的HBuilderX.exe即可。

2. 拉取项目源码

从本项目中复制git地址：[https://gitee.com/dcloud/material_management.git](https://gitee.com/dcloud/material_management.git)

在HBuilderX中点菜单文件-导入，选择从git导入，粘贴刚才复制的git地址。

![输入图片说明](https://images.gitee.com/uploads/images/2020/0215/102236_8088b458_5529724.png "导入.png")

3. 登陆
如果以前注册过HBuilderX，请保持登陆状态。如没有，在HBuilderX左下角点登陆。

4. 申请appid
源码项目不含appid，需要自己在manifest.json中申请。

具体操作方式为打开项目下的manifest.json文件，在右边点击申请appid。 

![输入图片说明](https://images.gitee.com/uploads/images/2020/0215/153918_b1f62e5a_5529724.png "获取APPID.png")


5. 申请和绑定服务空间
本项目构建在uniCloud云开发模式下，使用的是阿里云severless引擎，通过js云函数方式完成后台开发。开发者需要创建一个阿里云的serverless空间，并把服务端代码（也就是云函数）部署到自己的服务空间里。

DCloud和阿里云合作，疫情期间免费提供服务器，没有容量和并发限制。即便瞬间进入几百万用户也毫无影响。基于这套serverless架构，开发者无需关心双机热备、并发扩充、DDoS攻击等问题。详见uniCloud的官网：https://uniapp.dcloud.io/uniCloud/README

对项目下的cloudfunctions目录点右键，选择你的服务空间。如果没有服务空间，需要创建，创建时会引导登录和注册uniCloud。（如果看不到服务空间选择菜单，说明你使用的HBuilderX版本过低）

项目需要注册和开通uniCloud，因阿里云审核要求，需要实名认证。疫情期间，工作时间一般半小时内完成审核。

创建好服务空间后，继续对项目下的cloudfunctions目录点右键，选择你之前创建的服务空间，完成绑定。

![输入图片说明](https://images.gitee.com/uploads/images/2020/0215/102952_66fe1189_5529724.png "选择云空间.png")

6. 初始化服务空间
服务空间包括云数据库和云函数。刚建的服务空间，在uniCloud的web控制台看，里面数据库和云函数都是空的，需要建表和上传云函数。

（云数据库是mogodb，基于nosql）

数据库的结构说明在项目文件根目录下的db.md文件中。调整配置云数据库连接地址如下图：

![输入图片说明](https://images.gitee.com/uploads/images/2020/0215/103422_eb41dc21_5529724.png "屏幕截图.png")

下一步是上传云函数到你的服务空间。对cloudfunctions目录点右键，上传所有云函数到你的服务空间中。

![输入图片说明](https://images.gitee.com/uploads/images/2020/0215/103558_0d920c7b_5529724.png "屏幕截图.png")

你可以在uniCloud的web控制台，查看云端的数据库和云函数情况。打开web控制台的方式是对cloudfunctions目录点右键，打开uniCloud web控制台。

7. 运行项目
项目初始化完毕，可以运行了。

uni-app框架开发的项目，都可以运行在所有平台，不管是浏览器还是小程序，或者iOS、Android的App。点击工具栏的运行，或者Ctrl+r快捷键，可看到运行菜单。

点击运行到内置浏览器，或者不通过运行菜单，直接点HBuilderX右上角的预览，可以在直接运行H5版。

![输入图片说明](https://images.gitee.com/uploads/images/2020/0215/103832_ede0da9d_5529724.png "屏幕截图.png")

若之前下载的HBuilderX是标准版，此时会开始安装uni-app插件，插件安装完毕后重新运行一下。

若编译控制台提示node_module条件编译报错，可忽略。

如果要运行在外部浏览器，需要在uniCloud的web控制台的H5安全域名界面绑定安全域名，否则会有跨域问题。

如果要运行在手机App上，请通过数据线连接手机和电脑，然后点运行菜单，会刷出识别到的手机设备，进一步运行。

8. 创建管理员账户并登陆
运行起来的系统，需要登陆。因账户密码是通过算法加密存储的，所以之前的数据库初始化无法直接把超级账户预置进去。目前系统可以进行可视化界面创建用户，点击【我的】->【立即登录】->输入用户名和密码，点击【注册超级管理员】

![输入图片说明](https://images.gitee.com/uploads/images/2020/0215/104117_ff5ab5fa_5529724.png "屏幕截图.png")

默认界面显示的用户名：13800138000；密码：123456

然后就可以在前端界面里，用上述账户密码登陆了。
阿里云serverless的云函数第一次调用时，有冷启动过程，访问较慢，大约5秒左右才能联网返回数据。第二次调用是正常速度。目前阿里云在一定时间后会回收一直没再运行的云函数资源，回收后再执行仍然需要冷启动过程。这个问题阿里云正在优化。

最后，可以运行了。运行到内置浏览器或小程序、app都可以。

更多技术问题或需求请扫码进群，或发邮件565036413@qq.com。

![输入图片说明](https://images.gitee.com/uploads/images/2020/0215/105342_e8e19707_5529724.png "屏幕截图.png")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)