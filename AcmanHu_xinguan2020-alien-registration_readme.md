项目负责人：DCloud_UNI_GSQ。在QQ群797192690里。

项目预览地址：[wlry.m3w.cn](https://wlry.m3w.cn)。体验账户用户名：admin；密码：12345678。此地址为测试体验地址，具体某单位上线时，需要单独部署。

本项目已经在几十家社区成功应用。
![](https://images.gitee.com/uploads/images/2020/0204/152518_2d336b8c_1628277.jpeg)

本项目是基于木兰宽松许可证的开源项目，代码全部开源，开发者可自由使用其中的代码，自己部署相关的系统。

## 项目运行说明

1. 下载HBuilderX

本项目需要HBuilderX 2.5.11以上版本才能运行。**切记看清版本号，要最新alpha版**

[下载地址]((https://www.dcloud.io/hbuilderx.html))

![输入图片说明](https://images.gitee.com/uploads/images/2020/0213/022916_c822f4df_1628277.png "hx下载.png")

下载时选alpha版。然后根据自己的操作系统下载，下载标准版即可，运行项目时会自动安装依赖的插件。

HBuilderX是绿色的，Windows版解压后直接运行里的HBuilderX.exe即可。

2. 拉取项目源码

从本项目中复制git地址：https://gitee.com/dcloud/xinguan2020-alien-registration.git

在HBuilderX中点菜单文件-导入，选择从git导入，粘贴刚才复制的git地址。

![输入图片说明](https://images.gitee.com/uploads/images/2020/0213/023848_7da44ece_1628277.png "导入git.png")

如果Windows版，在HBuilderX安装Git插件时，需同时安装TortoiseGit软件。

如不参与开源项目开发，也可以在gitee仓库里下载zip包，解压到硬盘，将目录拖到HBuilderX中（注意根目录需包含项目的manifest文件）

3. 登陆

如果以前注册过HBuilderX，请保持登陆状态。如没有，在HBuilderX左下角点登陆。

4. 申请appid

源码项目不含appid，需要自己在manifest.json中申请。

具体操作方式为打开项目下的manifest.json文件，在右边点击申请appid。
![输入图片说明](https://images.gitee.com/uploads/images/2020/0213/024405_8fda3fb5_1628277.png "申请appid.png")

5. 申请和绑定服务空间

本项目构建在uniCloud云开发模式下，使用的是阿里云severless引擎，通过js云函数方式完成后台开发。开发者需要创建一个阿里云的serverless空间，并把服务端代码（也就是云函数）部署到自己的服务空间里。

DCloud和阿里云合作，疫情期间免费提供服务器，没有容量和并发限制。即便瞬间进入几百万用户也毫无影响。基于这套serverless架构，开发者无需关心双机热备、并发扩充、DDoS攻击等问题。详见uniCloud的官网：[https://uniapp.dcloud.io/uniCloud/README](https://uniapp.dcloud.io/uniCloud/README)

对项目下的cloudfunctions目录点右键，选择你的服务空间。如果没有服务空间，需要创建，创建时会引导登录和注册uniCloud。（如果看不到服务空间选择菜单，说明你使用的HBuilderX版本过低）

项目需要注册和开通uniCloud，因阿里云审核要求，需要实名认证。疫情期间，工作时间一般半小时内完成审核。

创建好服务空间后，继续对项目下的cloudfunctions目录点右键，选择你之前创建的服务空间，完成绑定。

![输入图片说明](https://images.gitee.com/uploads/images/2020/0213/030258_f6af6547_1628277.png "选择服务空间.png")

6. 初始化服务空间

服务空间包括云数据库和云函数。刚建的服务空间，在uniCloud的web控制台看，里面数据库和云函数都是空的，需要建表和上传云函数。

（云数据库是mogodb，基于nosql）

数据库的结构说明在项目文件根目录下的`db.md`文件中。同时HBuilderX提供了快捷初始化数据库的方法，打开cloudfunctions目录下的`db_init.json`文件，点右键，初始化云数据库，会自动完成表的创建。

![输入图片说明](https://images.gitee.com/uploads/images/2020/0213/030538_e0126f37_1628277.png "初始化数据库.png")

下一步是上传云函数到你的服务空间。对cloudfunctions目录点右键，上传所有云函数到你的服务空间中。

![输入图片说明](https://images.gitee.com/uploads/images/2020/0213/030645_553e3f4c_1628277.png "上传所有云函数.png")

你可以在uniCloud的web控制台，查看云端的数据库和云函数情况。打开web控制台的方式是对cloudfunctions目录点右键，打开uniCloud web控制台。

 

7. 运行项目

项目初始化完毕，可以运行了。

uni-app框架开发的项目，都可以运行在所有平台，不管是浏览器还是小程序，或者iOS、Android的App。点击工具栏的运行，或者`Ctrl+r`快捷键，可看到运行菜单。

点击运行到内置浏览器，或者不通过运行菜单，直接点HBuilderX右上角的预览，可以在直接运行H5版。

![输入图片说明](https://images.gitee.com/uploads/images/2020/0213/032435_6796712b_1628277.png "运行到内置浏览器2.png")

若之前下载的HBuilderX是标准版，此时会开始安装uni-app插件，插件安装完毕后重新运行一下。

若编译控制台提示node_module条件编译报错，可忽略。

如果要运行在外部浏览器，需要在uniCloud的web控制台的H5安全域名界面绑定安全域名，否则会有跨域问题。

如果要运行在手机App上，请通过数据线连接手机和电脑，然后点运行菜单，会刷出识别到的手机设备，进一步运行。

8. 创建管理员账户并登陆

运行起来的系统，需要登陆。因账户密码是通过算法加密存储的，所以之前的数据库初始化无法直接把admin账户预置进去。目前系统也暂无可视化界面创建用户，所以提供了一个创建用户用的云函数。

在cloudfunctions目录下找到云函数`create-user`，在其目录上右键点击上传并运行。
![输入图片说明](https://images.gitee.com/uploads/images/2020/0213/033201_b94e9bfd_1628277.png "创建管理员账户.png")


这个云函数运行后会在云数据库的user表里插入以下操作员信息。

```
{
  username: 'admin',
  password: '123456'
}
```

然后就可以在前端界面里，用上述账户密码登陆了。

实际部署时应更换`cloudfunctions-module/src/utils/constants.js`内的`passSecret`为自己的key，更换之后重新编译上传云函数，导入操作员信息。

阿里云serverless的云函数第一次调用时，有冷启动过程，访问较慢，大约5秒左右才能联网返回数据。第二次调用是正常速度。目前阿里云在一定时间后会回收一直没再运行的云函数资源，回收后再执行仍然需要冷启动过程。这个问题阿里云正在优化。

## 项目发布和部署
点击HBuilderX的发布菜单，可以发布到H5、App和小程序。
- 发布小程序
	* 注意uniCloud的域名要加入小程序的安全白名单，详见：[https://uniapp.dcloud.io/uniCloud/quickstart?id=%e5%b0%8f%e7%a8%8b%e5%ba%8f%e4%b8%ad%e4%bd%bf%e7%94%a8unicloud](https://uniapp.dcloud.io/uniCloud/quickstart?id=%e5%b0%8f%e7%a8%8b%e5%ba%8f%e4%b8%ad%e4%bd%bf%e7%94%a8unicloud)
	* 需要修改/pages/tabbar/my.vue文件中的如下内容
	```
	// #ifdef MP-WEIXIN
	//微信的话这里要写死为小程序的二维码地址或者是H5平台的二维码地址，或者直接填 '' 则在微信小程序中不显示二维码
	val: "https://wlry.m3w.cn/#/pages/tabbar/add?id=" + uni.getStorageSync('username'),
	// #endif
	```

- 发布H5
首先在发布菜单中发布H5，生成前端html页面文件，将页面部署到自己的web服务器，比如NGINX下面。

然后自己准备一个域名，将域名解析到NGINX的服务器ip。

最后在uniCloud的web控制台配置安全域名，参考：[https://uniapp.dcloud.io/uniCloud/quickstart?id=h5%e4%b8%ad%e4%bd%bf%e7%94%a8unicloud](https://uniapp.dcloud.io/uniCloud/quickstart?id=h5%e4%b8%ad%e4%bd%bf%e7%94%a8unicloud)


## 项目功能说明
底部5个tab：列表、图表、+、搜索、我的

本软件设计为操作员必须登录，访客无需登录。但操作员登陆后，可以在“我的”里看到一个二维码，把这个二维码出示或打印张贴给外来人员，外来人员可以扫描此码，打开一个H5页面，自助填写表单。

### 列表
主屏是来访人员列表，点击人员item进详情，详情里每个人的电话可以点击拨叫。

如果访客登记时填写了春运车次航班情况，列表显示时会自动去危险车次数据源查询，验证外来人员乘坐的车次、航班，是否是国家通告的已发现确诊人员的车次。

### 图表
显示按时间为横轴的曲线，表达隔离、发烧、疑似、确诊、死亡的曲线

### +
表单，按数据库字段填写。

姓名、联系电话是必填项。如部署时各单位有定制需求，比如删减一些字段、改一些字段为必填项，可在开源项目基础上自行修改。

电话是人的标记，同一个电话，再次录入时，会更新之前的基本信息。

保存入库时，除了表单填写内容，还需要在数据库里同时存入操作人员的姓名、id、操作时间、操作ip。

### 搜索
可以按人名、手机号、登记时间来查询外来人员登记记录，搜索结果同列表。

在pc浏览器打开本页面后，在界面右上角可以看到导出按钮，导出格式是csv，可以用excel打开。如果需要对导出的字段删减。自行在开源代码中删减。

### 我的
操作员登陆、登出、修改密码。

本系统不支持注册。操作员账户由管理员通过云函数创建，然后每个操作员登陆后，可自行修改密码。

如忘记密码，请管理员在云函数中重置其密码。

云函数`create-user`目录上右键点击上传并运行。

如开发者有精力，欢迎贡献一个管理员可视化创建用户、重置用户密码的界面。


## 请外来人员自助填写。
操作员登陆后，点tab中的”我的“，会展现一个二维码。外来人员可以扫描此码，自助填写。

第二次填写时，重复信息会辅助填写。

## 后续值得完善的功能
- 支持多单位托管，目前只能一个小区部署一套，如果支持托管方式，可以在线申请和开户，小区的部署速度会大幅加快。（有开发者提供了托管版本，但后台是java方式，[详见](https://gitee.com/windfly/UserRecordBiz)）
- 目前只登记进，没关联出
这些功能欢迎开发者持续贡献和完善。

## 关于源码的二次开发

本项目基于木兰宽松许可证，代码可自由使用和更改。

- 项目前端基于uni-app框架开发，它是一个通过vue.js编写所有平台应用的多端框架。你需要了解uni-app以便于更深度的定制。uni-app的文档详见：[https://uniapp.dcloud.io/README](https://uniapp.dcloud.io/README)
- 项目后端基于uniCloud，它是一个基于js的云开发模式，与微信、支付宝小程序的云开发类似，但可以跨端使用。它基于serverless模型，优势众多。建议开发者通读一遍uniCloud的介绍和快速上手，以方便做二次开发。uniCloud的文档详见：[https://uniapp.dcloud.io/uniCloud/README](https://uniapp.dcloud.io/uniCloud/README)

本开源项目的完成，感谢众多开发者的贡献DCloud_UNI_GSQ、DCloud_UNI_WYQ、DCloud_UNI_HDX、躺希腊额阿毛、反复再反复、King、丛林野战军、AHello、kagstest。

欢迎加入QQ群797192690交流。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)