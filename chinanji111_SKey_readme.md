# SKey小程序

SKey是一款简洁易用的**账号密码管理工具**，它使用可靠的加密技术帮助您加密与管理重要的帐号密码数据。采用小程序云开发方案，不设独立后台。

SKey采用谷歌开源的CryptoJS库对数据进行AES加解密，无论是本地存储还是云存储均进行加密处理，保证安全性。

SKey源代码开源，接受监督，小程序内无任何广告，界面简洁，友好体验。

## SKey名字的由来

SKey读作[s'ki:],S是英文单词security、simple的首字母，即安全、简单。SKey让钥匙变得更安全，让生活变得更简单。

### **扫码体验**

![启动页](doc/gh_344.jpg)

## 组织结构
~~~
src
|———cloudfunctions
|   |———login -- 获取 WX Context (微信调用上下文)
|———miniprogram
|   |——components -- 组件库
|       |——cell -- 列表行
|       |——cell-group -- 列表
|       |——h-modal -- 弹窗
|       |——h-navbar -- 自定义导航栏
|       |——h-void -- 无数据提示
|       |——sticky -- 加强版吸顶器
|       |——sticky-item -- 吸顶器行
|   |——data -- 数据处理
|       |——defaultData -- 生成默认数据
|       |——KeyService -- 账号密码数据处理
|       |——userInfoService -- 用户信息
|   |——pages -- 页面
|       |——center --用户中心
|           |——childgages
|               |——about -- 关于
|               |——category -- 自定义分类
|               |——dataexport -- 数据导出
|               |——guide -- 使用指南
|               |——problem -- 常见问题
|               |——updatelog -- 更新日志
|           |——center --用户设置页
|       |——edit -- 编辑页
|       |——index -- 首页
|       |——verifypwd -- 主密码验证页
|       |——view -- 账号密码查看页
|   |——utils -- 工具库
|       |——cryAes -- CryptoJS的AES库
|       |——cryptoJS -- 对 CryptoJS简单的封装
|       |——log -- 日志记录
|       |——utli -- 常用方法
|——app -- 小程序入口程序
~~~

## 技术点

1. 自定义导航栏：实现自动适配各种机型，包括刘海屏，保证和微信默认导航栏高度一致。
2. 吸顶效果：加强版吸顶效果，在首页自定义导航栏的情况下，实现吸顶效果，可细看吸顶效果的差异，更加友好。（因无法解决IOS上动画抖动问题，在IOS上默认关闭了吸顶效果）
3. CryptoJS：将谷歌开源的js版加解密库移植到小程序，实现 AES、MD5、等加解密
4. 时间轴：详细可查看小程序更新记录页
5. 指纹：利用小程序的指纹功能方便解锁

## 预览图

![启动页](doc/1.jpg)
![验证主密码](doc/2.jpg)
![指纹验证](doc/3.jpg)
![首页](doc/4.jpg)
![查看详情](doc/5.jpg)
![编辑](doc/6.jpg)
![个人设置](doc/7.jpg)
![自定义分类](doc/8.jpg)
![常见问题](doc/9.jpg)
![使用指南](doc/10.jpg)
![更新记录](doc/11.jpg)
![关于](doc/12.jpg)

## 云同步的数据

![关于](doc/ht.png)

## BUG反馈

如果你发现BUG，请发送邮件到 864353016@qq.com 都将及时得到解决。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)