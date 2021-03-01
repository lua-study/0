# hermesagent

#### 项目介绍
android群控系统，使用xposed+RPC实现方法级别的群控

hermesagent是hermes系统的客户端模块，也是系统最核心的模块了，他是种植在手机里面的一个agent，同时他也是一个xposed的模块插件，agent本身启动了一个service，agent插件模块将会自动注册钩子函数，并且和service通信。Android设备外部请求可以通过暴露在agent上面的一个http端口，和agent通信，然后agent和目标apkRPC。
如此实现外部请求到任何一个app的任何功能的外部调用


#### 关联项目
HermesAdmin ：https://gitee.com/virjar/hermesadmin
hermesAdmin用来管理多个hermesAgent，进行简单的服务治理和agent运维工作

#### 软件架构
软件架构说明
![termesAgent](img/termesAgent.png)


#### 安装教程

1. 修改server服务器地址
2. 编译app正式版
3. 安装app到手机上面
4. Android手机安装xposed环境，并且启用我们的xposed模块，然后重启xposed（xposed项目的标准流程）
5. 书写目标app插件代码，实现 com.virjar.hermes.hermesagent.plugin.AgentCallback
6. 安装目标app到手机，并启动目标app
7. 通过浏览器访问app所在ip的5597端口，查看服务列表
8. 通过invoke接口，调用服务api

#### 使用说明

1. 要安装xposed
2. xposed启用本模块之后，第一次需要重启，后续不需要重启了
3. 钩子函数写到com.virjar.hermes.hermesagent.hookagent路径下，能够被框架自动识别，其他地方不会识别
4. agent必须提供空参构造（我们是类扫描机制实现的）
5. 开启网络访问权限，有些手机在后台运行之后，将会禁止后台访问网络。请放开这个配置
```
设置——无线和网络——WLAN设置——高级设置——WLAN休眠策略——永不休眠

     小米手机：
     1、设置--其他高级设置--电源和性能--神隐模式
     2、标准(限制后台应用的网络和定位功能)
     3、关闭(不限制后台应用的功能)
     4、默认是标准,在屏保后4分钟左右会限制后台应用的网络功能

```
关于小米系统神隐模式拆解方案：对应的设置app为``com.miui.powerkeeper``，用户权限为：``android:sharedUserId="android.uid.system"``
代码地址：``/data/dalvik-cache/arm/system@app@PowerKeeper@PowerKeeper.apk@classes.dex``,apk地址：``/system/app/PowerKeeper/PowerKeeper.apk``
apk设置api：``com.miui.powerkeeper.provider.UserConfigureHelper.updateToTable``,方法内使用ContentResolver：
```
    public static void updateToTable(Context context, ContentValues contentValues) {
        ContentResolver contentResolverForUser = ContextHelper.getContentResolverForUser(context, UserHandle.OWNER);
        if (contentValues.getAsInteger("userId") == null) {
            Log.e(TAG, "Missed userId");
        } else if (contentValues.getAsString("pkgName") == null) {
            Log.e(TAG, "Missed pkgName");
        } else if (contentValues.containsKey("_id")) {
            contentResolverForUser.update(ContentUris.withAppendedId(UserConfigure.CONTENT_URI, contentValues.getAsLong("_id").longValue()), contentValues, null, null);
        } else {
            contentResolverForUser.insert(UserConfigure.CONTENT_URI, contentValues);
        }
    }
```
两条关于微视由无限制到小米只能策略切换日志：
```
 content resolver update, URI content://com.miui.powerkeeper.configure/userTable/5264 contentValues:[bgControl=noRestrict, _id=5264, userId=0, pkgName=com.tencent.weishi]
 content resolver update, URI content://com.miui.powerkeeper.configure/userTable/5264 contentValues:[bgControl=miuiAuto, _id=5264, userId=0, pkgName=com.tencent.weishi]
```
```
09-22 17:35:16.240  4829  5917 I weijia  : content provider update, URI content://com.miui.powerkeeper.configure/userTable/1112 contentValues:[bgControl=noRestrict, _id=1112, userId=0, pkgName=tv.danmaku.bili]
09-22 17:35:16.240  4829  5917 I weijia  : 接收到神隐模式配置命令,process: com.miui.powerkeeper:service package:com.miui.powerkeeper providerClass:com.miui.powerkeeper.provider.PowerKeeperConfigureProvider
```
输入入库了，数据库建库代码：``com.miui.powerkeeper.provider.UserDatabaseHelper``，数据库地址：``/data/data/com.miui.powerkeeper/databases/user_configure.db``
数据库内容：
```
sqlite> select * from userTable;
3|0|com.miui.gallery|1520247935689|miuiAuto||
9|0|com.android.providers.downloads.ui|1520247936451|miuiAuto||
12|0|com.xiaomi.gamecenter|1520247936886|miuiAuto||
..
723|0|com.umetrip.android.msky.app|1524650024364|miuiAuto||
1111|0|com.sina.weibo|1525451454542|miuiAuto||
1112|0|tv.danmaku.bili|1537608916242|noRestrict||
```
对应的控制指令为noRestrict，就是不限制后台了。逻辑基本破解

6. 如果在AndroidStudio上面编译本项目，需要安装lombok插件，见：[projectlombok](https://projectlombok.org/setup/android)

7. 允许程序开机自启
为了让app全自动提供服务，需要让手机开机便启动agent，有些系统会禁止该行为。如果你的手机有存在该行为的话，请放开自启动限制
[stackoverflow](https://stackoverflow.com/questions/32032329/process-is-not-permitted-to-autostart-boot-complete-broadcast-receiver)
*一定要打开自启动，每个相关的都要打开*

对于小米系统来说，已经默认拆解了自启动拦截问题。可以不关心程序自启动配置


### 演示
1. 查看首页，观察可以提供的接口
![index.png](img/index.png)

2.观察已经注册成功，可以提供调用的服务
![servicelist.png](img/servicelist.png)

3.调用目标接口
![invoke.png](img/invoke.png)

其中，本demo提供了微视的话题搜索接口破解，可以通过一个关键字搜索微视的视频数据。微视demo的地址为：

https://gitee.com/virjar/hermesagent/blob/master/app/src/main/java/com/virjar/hermes/hermesagent/hookagent/WeiShiAgent.java

### 运维相关
Q: agent意外死掉，但是没有自动被拉起   
A: 大多数情况是没有放开自启动限制导致的，在小米系统上面，将会限制app被广播启动的功能，此时app启动广播将会被操作系统拦截。
极少可能是Hermes系统所有节点在同一时刻被杀死，此时系统进程之间无法实现多进程相互守护了。

Q: 手机运行一段时间之后，突然请求卡顿，接口请求全部超时   
A: 观察系统日志，系统内部master和slave可以正常通信，此时可能是你没有开启后台的网络权限。一些操作系统可能在app被切到后台之后，禁止网络通信

Q:master和slave都正常运行，但是在agent上面查看服务列表，对应服务一直不在服务列表中   
A:服务注册的原理是，在slave中注入钩子代码，驱动slave主动注册service到master。一般注册不成功的原因是钩子代码注入失败   
我们使用xposed作为代码注入的base lib，可以观察是否xposed本身模块启动失败。1.xposed未安装完整；2.xposed中没有开启本插件；3.高版本中，xposed存在一个bug，导致在Android启动的时候，使用错误的插件apk地址进行加载，进而无法加载到插件代码（同一个apk，覆盖安装，系统重启之后，apk代码地址将会被系统整理而改变路径，xposed模块管理使用的整理之前的apk地址）
第三个原因，是系统拦截了xposedInstaller自启动广播导致的。目前Hermes已经自动处理了这个问题，只要是Hermes模块正常启动的过程，XposedInstall安装过程会放开对应广播传递

#### 参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request

#### 合作

开源即免费，我不限制你们拿去搞事情，但是开源并不代表义务解答问题。如果你发现了有意思的bug，或者有建设性意见，我乐意参与讨论。
如果你想寻求解决方案，但是又没有能力驾驭这个项目，欢迎走商务合作通道。联系qq：819154316，或者加群：569543649。
拒绝回答常见问题！！！

#### todo list

1. 自动配置网络，如果系统系统启动，网络不正常，根据配置策略配置网络连接参数。如wiki账号密码，系统代理等
2. 拆解后台网络流量拦截限制（小米系统）。目前app安装之后，需要放开多个app的网络后台限制配置。可以通过app内嵌代码统一拆解
3. 垃圾文件异步清理，在IPC过程中，可能存在大问题传递，由于某种原因，可能临时文件没有清除成功。这可能导致手机存储被无效文件占用。导致磁盘被打爆
4. Hermes系统日志整理，目前hermes相关日志没有统一tag。无法方便排查Hermes本身的问题，需要考虑串联Hermes系统日志
5. 内网穿透方案，考虑Android手机运行在私有网络，server在公有网络。server可以转发invoke请求到达处于私有网络下面的Android手机中
6. 定时重启adb远程服务，

#### 捐赠
如果你觉得作者辛苦了，可以的话请我喝杯咖啡
![alipay](img/reward.jpg)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)