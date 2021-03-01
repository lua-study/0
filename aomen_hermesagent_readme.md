# hermesagent

#### 项目介绍
android群控系统，使用xposed+RPC实现方法级别的群控

hermesagent是hermes系统的客户端模块，也是系统最核心的模块了，他是种植在手机里面的一个agent，同时他也是一个xposed的模块插件，agent本身启动了一个service，agent插件模块将会自动注册钩子函数，并且和service通信。Android设备外部请求可以通过暴露在agent上面的一个http端口，和agent通信，然后agent和目标apkRPC。
如此实现外部请求到任何一个app的任何功能的外部调用

你可以用它来进行Android数据抓取，hermes应该能够实现绝大部分有反抓防范的app的数据获取

### 申明
受限于商业竞争原因，我删除了所有的wrapper。可能后续我在维护一些个人版demo的的apk破解逻辑吧

#### 关联项目
HermesAdmin ：https://gitee.com/virjar/hermesadmin
hermesAdmin用来管理多个hermesAgent，进行简单的服务治理和agent运维工作

#### 软件架构
软件架构说明
![termesAgent](img/termesAgent.png)




#### 合作

开源即免费，我不限制你们拿去搞事情，但是开源并不代表义务解答问题。如果你发现了有意思的bug，或者有建设性意见，我乐意参与讨论。
如果你想寻求解决方案，但是又没有能力驾驭这个项目，欢迎走商务合作通道。联系qq：819154316，或者加群：569543649。
拒绝回答常见问题！！！


#### 捐赠
如果你觉得作者辛苦了，可以的话请我喝杯咖啡
![alipay](img/reward.jpg)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)