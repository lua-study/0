功能介绍
====

本游戏是一款基于Cocos2dx开发的纵版飞行射击单机手游。玩家可以控制一架飞机与敌机进行对战，飞机可以发射子弹、导弹甚至激光，除此之外，玩家还能对自己的飞机进行强化改造，提升基础属性。当玩家完成指定的任务后，还能获取各种类型的道具奖励。游戏操作简单，上手容易，画面逼真炫酷，并有多种道具可供使用。

----------

本游戏支持三种游戏模式：闯关模式、无尽模式、急速模式。

### 1. 闯关模式
这是一种最常见的玩法，即游戏给玩家多个关卡，每个关卡面对的敌人不同，任务也不同，随着任务的完成，剧情也会逐渐展现在玩家面前。

### 2. 无尽模式
所谓无尽就是指这个模式的游戏永远不会结束，除非玩家的战机被击落。这种模式能提供给玩家一种畅快淋漓的游戏体验，因为在游戏中玩家不会受到其他事物的干扰，打飞机一次性打个够。

### 3. 急速模式
此游戏模式考验的是玩家的反应能力。在此游戏模式中，玩家控制的战机会以较高的速度飞行，同时，周围还有飞鸟、山川、陨石等障碍物，玩家需集中注意力快速的躲过这些障碍物才能顺利进行游戏。同时，战机的飞行速度也会越来越快，永无尽头。

程序讲解
====
- [仿《雷霆战机》飞行射击手游开发--游戏简介](https://my.oschina.net/u/1986600/blog/828330)
- [仿《雷霆战机》飞行射击手游开发--项目总览](https://my.oschina.net/u/1986600/blog/828332)
- [仿《雷霆战机》飞行射击手游开发--游戏入口](https://my.oschina.net/u/1986600/blog/828334)
- [仿《雷霆战机》飞行射击手游开发--资源预加载](https://my.oschina.net/u/1986600/blog/828355)
- [仿《雷霆战机》飞行射击手游开发--游戏对象](https://my.oschina.net/u/1986600/blog/828368)
- [仿《雷霆战机》飞行射击手游开发--GameObject](https://my.oschina.net/u/1986600/blog/828371)
- [仿《雷霆战机》飞行射击手游开发--飞机](https://my.oschina.net/u/1986600/blog/828625)
- [仿《雷霆战机》飞行射击手游开发--防破解](http://www.cnblogs.com/thorqq/p/6397611.html)
- [仿《雷霆战机》飞行射击手游开发--新手引导](http://www.cnblogs.com/thorqq/p/6403666.html)
- [仿《雷霆战机》飞行射击手游开发--子弹、跟踪导弹和激光](http://www.cnblogs.com/thorqq/p/6563904.html)
- [仿《雷霆战机》飞行射击手游开发--统一计费接口(未完成)](http://www.cnblogs.com/thorqq/p/6403684.html)
- [仿《雷霆战机》飞行射击手游开发--数据存储(未完成)](http://www.cnblogs.com/thorqq/p/6403691.html)
- [仿《雷霆战机》飞行射击手游开发--后台服务器(未完成)](http://www.cnblogs.com/thorqq/p/6403694.html)
- [仿《雷霆战机》飞行射击手游开发--滚动的背景(未完成)](http://www.cnblogs.com/thorqq/p/6403702.html)


界面展示
====

游戏界面如下图所示：

![主菜单][1]

![战机升级][2]

![战斗画面][3]

![战斗画面][4]

开发环境安装配置
========

本游戏在64位Windows7系统下使用C++开发，因此需安装如下软件：

- 安装VS2013
- 安装cocos2d-x 3 8。注意，如果下载的是3.8.1，请在安装后将目录名3.8.1改为3.8。
- 安装jdk
- 安装android-sdk
- 安装android-ndk
- 下载本项目源代码
- 打开Cocos Studio的”偏好设置“，设置jdk、android-sdk和ndk路径
![Cocos Studio设置][5]

编译运行
====

##Win32

双击proj.win32\Raiden.sln，系统即会用VS2013打开整个项目（如下图），点击工具栏中“本地Windows调试器”，将进行编译，经过漫长的等待后，游戏会自动启动运行。
![VS工程][6]


#注意：本开源版本去掉了设计文档、Java代码、cocos studio工程、弱联网服务代码、计费SDK和渠道SDK接入代码，并强力压缩了所有图片。
### 如需完整版本，或需其他支持，可联系thorqq@163.com


  [1]: http://upload-images.jianshu.io/upload_images/2397007-3e8a4a5fad6916e5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
  [2]: http://upload-images.jianshu.io/upload_images/2397007-38b85d2f69a3ec2a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
  [3]: http://upload-images.jianshu.io/upload_images/2397007-e1f24f84510b70a5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
  [4]: http://upload-images.jianshu.io/upload_images/2397007-fa6b1cd547e113cc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
  [5]: http://upload-images.jianshu.io/upload_images/2397007-262cc9a87dba60b5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
  [6]: http://upload-images.jianshu.io/upload_images/2397007-d8571f0f94c84613.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)