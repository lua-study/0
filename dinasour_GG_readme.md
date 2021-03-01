## 可在广域网部署运行的QQ高仿版
***
#### 项目地址：[http://www.cnblogs.com/justnow/p/3382160.html](http://www.cnblogs.com/justnow/p/3382160.html)

**特别说明一下**：我不是作者。查看详细，请访问[作者博客](http://www.cnblogs.com/justnow/)。

***

　 *（最新版本：V4.2，2015.03.25）*

　　GG是QQ的高仿版，包括客户端和服务端，可在广域网部署使用，目前最新版本为4.0。我想写一个类似汇总的文章，通过这篇文章，大家可以了解到GG的全貌和最新进展，以及关于一些常见问题的解答也汇总在这里。

　　言归正传，对我个人而言，我的目标并不是做一个QQ高仿版的玩具，而是希望做成一个能够真正使用的产品（这个过程还有很长的路要走），并持续维护下去。

###一.已实现的功能
1. 注册、登录、添加好友、好友列表。
2. 自拍头像。
3. 文字聊天、字体设置、GIF动态表情、窗口震动、截图、手写板、登录状态（在线、离开、忙碌、勿打扰、隐身）、输入提醒
4. 群功能：创建群、加入群、退出群、群聊天
5. 文件传送、文件夹传送（支持断点续传）
6. 语音视频聊天
7. 远程磁盘
8. 远程协助
9. 共享桌面（可以指定要共享的桌面区域）
10. 可靠的P2P
11. 网盘
12. 离线消息
13. 离线文件
14. 托盘闪动：跟QQ完全一样，当接收到消息时，托盘会闪动对应好友的头像。点击头像，将弹出与好友的聊天框。
15. 最近联系人列表
16. 系统设置：开机自动启动、麦克风设备索引、摄像头设备索引，叉掉主窗口时关闭程序还是隐藏窗口。
17. 聊天记录：支持本地保存和服务器端保存两种方式。
18. 好友分组：新增/删除分组，修改分组名称，改变好友的所属分组。
19. 打开聊天窗口时，自动显示上次交谈的最后一句话。
20. 输入提醒：像QQ一样，当对方正在输入消息时，我这边的聊天框可以看到对方“正在输入”的提示。
21. 自动记录：GG2014会自动记录上次打开的主界面的位置、大小；最后一次打开的聊天窗口的大小；最后一次设定的字体的颜色、大小等。
22. 主窗体靠边自动隐藏。
 

###二.后续待实现的功能
1. 增加持久化支持
2. 视频会议


###三.开发环境
1. 开发环境：VS2010 ，开发语言：C#， .NET Framework 版本： 2.0 
2. 部署客户端时，客户端机器还需要安装VC++2008 runtime、VC++2010 runtime。
   

###四.相关说明
1. 如果要将GG部署到广域网，则可以在服务端的配置文件中设置监听的端口；而在客户端的配置文件中，则可以指定服务器的IP和Port。
2. 虚拟数据库
    1. 为了部署测试更简单，GG没有采用真实的物理数据库，而是在内存中虚拟了一个数据库（即服务端的VirtualDB类），用于存储用户注册信息、好友关系、群信息等。
    2. GG内置了几个用户：10000、10001、10002、10003，它们的登录密码都是"1"。
    3. GG内置的这几个用户之间都是好友关系。
    4. GG内置了两个群：G001、G002。G001群包含所有内置测试用户，G002群包含10000和10001两个用户。
    5. 上述的这些内置信息，在VirtualDB类的构造函数中设定。

3. 麦克风、摄像头的选择可在客户端系统设置窗口（SystemSettingForm）中指定。
4. 语音视频：也有很多朋友问语音视频设备的工作怎么不正常，或者语音视频不流畅，这个可以直接参考OMCS官方文档：摄像头、麦克风、扬声器、设备测试 、带宽要求。
5. 特别说明一下：GG项目中，只要是我写的代码，全部都放出来了。拜托喜欢每一个dll都有源码的朋友不要再问我要其它的源码了：）


###五.版本记录
2013.08.07  --  V1.0， 登录、好友列表、文字聊天、文件传送、文件夹传送

2013.09.02  --  V1.8， 语音视频聊天

2013.09.23  --  V2.0， 网盘、远程磁盘

2013.11.05  --  V2.4， 远程协助、共享桌面

2014.04.15  --  V3.0， 注册、加好友、加入群、群聊

2014.05.16  --  V3.2， 离线消息、离线文件

2014.05.28  --  V3.4， 系统设置、最近联系人

2014.06.30  --  V3.5， 自拍头像、修改密码、删除好友

2014.08.06  --  V3.6， 语音消息、语音留言 

2014.09.16  --  V3.7， 优化视频聊天 

2014.11.06  --  V4.0， 聊天记录、好友分组、登录状态、GIF动态表情

2014.12.31  --  V4.1， 托盘闪动消息提醒、公开JustLib源码。

2015.03.25  --  V4.2， 主窗体靠边自动隐藏

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)