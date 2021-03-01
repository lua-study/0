# 目录

[点击这里查看所有博文](https://blog.csdn.net/weixin_44570083/article/details/104285283)

&emsp;&emsp;本系列博客所述资料`均来自合宙官方`，并不是本人原创（只有博客是自己写的），csdk只是得到了`口头的允许公开授权`。出于热心，本人将自己的所学笔记整理并推出相对应的使用教程，方面其他人学习。为国内的物联网事业发展尽自己的一份绵薄之力，`没有为自己谋取私利的想法`。若出现侵权现象，请告知本人，本人会立即停止更新，并删除相应的文章和代码。

&emsp;&emsp;本系列博客基于紫光展锐的`RDA8910  LTE Cat 1` bis芯片平台开发。理论上适用于合宙的Air720U、Air724U、广和通L610以及安信可的cat-01模块。

&emsp;&emsp;各个厂家的部分配置文件可能不一样，也许会导致设备出现奇怪的问题，其他的模块我也不确定能不能用，自行测试。但是有一点`编译下载和监视流程基本一样`，可供参考。

&emsp;&emsp;先不管支不支持，如果你用的模块是是紫光展锐的RDA8910，那都不妨一试，也许会有意外收获（`也有可能变砖，慎重！！！`）。

&emsp;&emsp;我使用的是`Air724UG`开发板，如果在其他模块上不能用，那也不要强怼，也许是开发包不兼容吧。这里的代码是没有问题的。例程仅供参考！
# 一、环境搭建前准备
## 1.1、准备硬件
&emsp;&emsp;这里我选用的是合宙商城推出的的Air724UG开发板，前段时间合宙搞活动19.9可以买一个开发板加一个芯片，抢到的小伙伴也都陆陆续续收到货了。

&emsp;&emsp; 该开发板在淘宝和合宙商城都有出售。价格199软妹币，还可以接受。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020051911371329.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)

* Air724UG淘宝链接：[淘宝购买点我](https://item.taobao.com/item.htm?spm=a1z10.5-c-s.w4002-22701068354.15.60712761TuYlsJ&id=614125604268)
* Air724UG合宙商城：[商城购买点我](http://m.openluat.com/product/1264)，也可关注合宙的微信公众号自行购买

&emsp;&emsp;这个模块安信可也有得卖，动手能力强的小伙伴可以自己画板子，不行的话那就等等，据八卦消息，安信可的开发板也快出来了。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519114453900.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)

* 安信可cat-01淘宝链接：[淘宝购买点我](https://item.taobao.com/item.htm?spm=a1z10.5-c-s.w4002-16491566042.17.24216e465toAYL&id=615816689044)

## 1.2、准备软件
* Windows10 USB驱动下载：[点我](https://download.csdn.net/download/weixin_44570083/12438107)
* Win7/Win8 USB驱动下载：[点我](https://download.csdn.net/download/weixin_44570083/12438113)
* coolwatch_win32_R2.0.0002(调试软件)：[点我](https://download.csdn.net/download/weixin_44570083/12438131)
* UpgradeDownload_R23.0.0001(下载软件)：[点我](https://download.csdn.net/download/weixin_44570083/12438137)

&emsp;&emsp;上面3个链接全部下载（驱动USB选一个就行了，没必要全部下载），如下图所示，将它们全部解压
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519115448691.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
## 1.3、准备开发包
&emsp;&emsp;这里将开发包托管到了码云上面，获取开发包需要安装Git
，自己去百度下载安装就行了，这里就不放链接了。
&emsp;&emsp;右键选择`Git Bash Here`，打开Git窗口。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519120045783.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
&emsp;&emsp;输入这条指令，回车开始克隆仓库（`开发包不要放在c盘，放在c盘会编译失败`）。

```c
git clone --recursive https://gitee.com/chenxiahuaxu/RDA8910_CSDK.git
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020051912061543.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
&emsp;&emsp;克隆完成后会在目录下生成一个`RDA8910_CSDK`的文件夹。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519120716605.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
# 二、开始环境搭建
 ## 2.1、安装驱动
 
&emsp;&emsp;打开解压后的`RDA8910DriversForWin10`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519121107623.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
&emsp;&emsp;根据自己的操作系统位数，选中安装程序，如下图所示。
&emsp;&emsp;基于x64那就选择`DPInst64.exe`安装
&emsp;&emsp;基于x86那就选择`DPInst32.exe`安装
&emsp;&emsp;我这里电脑是64位的，所以选择`DPInst64.exe`安装程序
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200212211325596.png)
&emsp;&emsp;安装成功后将开发板插上电脑，将开关拨到On，并且按下开机键，稍等一会正常情况下，开发板三个灯都会正常亮起，并伴随着闪烁

&emsp;&emsp;打开，设备管理器查看端口，是否有如下三个设备，如果没有，那就是驱动没有安装成功，回去重新安装驱动
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519121346224.png)

`注意`：如果是win10系统，需要禁用驱动程序强制签名，否则安装失败，自行百度相关教程这里不多做赘述

 ## 2.2、编译固件
&emsp;&emsp;这里使用的是VsCode作为开发的IDE，用Code打开`RDA8910_CSDK`文件夹（`开发包不要放在c盘，放在c盘会编译失败`）。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519142046862.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
&emsp;&emsp;将`demo`里面的`0_HelloWorld`文件夹里面所有的内容复制到`USER`目录下，并覆盖。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519142240520.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
&emsp;&emsp;鼠标右击`USER`文件在，选择在终端打开
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020051914233082.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
&emsp;&emsp;输入`.\Debug.bat  -b`回车，开始编译，编译时间大概十秒左右。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200621195146282.png)
&emsp;&emsp;提示`[67/67] Generating ../hex/RDA8910_CSDK_USER/RDA8910_CSDK_USER_APP.pac, .....CSDK_V541_RDA8910.map, ../hex/RDA8910_CSDK_USER_map/CSDK_V541_RDA8910.elf` 代表编译成功
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200621195204572.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
 ## 2.3、下载固件
 ### 2.3.1、通过软件下载
&emsp;&emsp;打开`UPGRADEDOWNLOAD_R23.0.0001\Bin`，双击`UpgradeDownload.exe`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519142814722.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519142858589.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
&emsp;&emsp;点击第一个齿轮图标![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519142940241.png)

&emsp;&emsp;加载RDA8910_CSDK目录`RDA8910_CSDK\build\hex\RDA8910_CSDK_USER\RDA8910_CSDK_USER.pac`下的固件，
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519143203637.png)
&emsp;&emsp;点击第三个![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519143231263.png)图标，软件进入等待下载状态。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519143254755.png)
&emsp;&emsp;将开发板连接到电脑（`确保驱动是安装正确`），开机后设备管理器显示
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519143445248.png)
&emsp;&emsp;按住boot按键`不放`，按复位键松开，系统提示正在下载就可以松开boot按键了
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519143533391.png)
&emsp;&emsp;此时设备管理器只有一个`SPRD U2S Diag`，


![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519143611975.png)
&emsp;&emsp;等待下载完成，重启按一下复位键，使开发板退出Download模式，进入运行模式。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519143659654.png)
 ### 2.3.2、通过命令行下载（推荐）
 &emsp;&emsp;两种下载方式二选一，建议选用命令行下载，更简单。
  &emsp;&emsp;编译完成后，在命令行输入`.\Debug.bat  -f`，进入全自动下载模式。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200621195442943.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
    &emsp;&emsp;编啥都不要管，等待下载完成即可。
    ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200621195518938.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)


 ## 2.4、运行监视
 ### 2.4.1、使用软件运行监视
&emsp;&emsp;打开`\coolwatch_win32_R2.0.0002`，双击`coolwatcher.exe`。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519143947859.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
&emsp;&emsp;软件左侧选择`8910`，右侧的`lastcomport`，填写设备管理器中`RDA8910 USB Device 2 AP Diag`所对应的COM口，我这里是COM9，所以填写9。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519144129339.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519144330706.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
&emsp;&emsp;点击OK进入软件，如果软件如下图所示，则代表连接成功。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519144426819.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
&emsp;&emsp;点击任务栏Plugins选择Tracer打开监视窗口，右下角会出现监视窗口。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519144544988.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020051914455431.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
&emsp;&emsp;这时候发现点击![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519144722538.png)绿色箭头没有任何反应。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519144751573.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)


&emsp;&emsp;打开串口调试助手，随便哪个都行，记住设备管理器中`RDA8910 USB Device 1 AT`所对应的COM口，我这里是COM8。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519144831327.png)
&emsp;&emsp;在串口调试助手中，选择COM8端口，波特率设置为921600，发送`AT^TRACECTRL=0,1,3`命令，后面必须要加一个`回车换行`。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519144931212.png)
&emsp;&emsp;提示OK代表日志信息打开成功，`默认不会打开日志输出`。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519145722966.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
&emsp;&emsp;这时候再次点击绿色按钮![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519144722538.png)发现调试信息已经开始输出了，HelloWorld成功打印。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200519150142208.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
 ### 2.4.2、使用命令行运行监视（墙裂推荐）
&emsp;&emsp;上面的2.4.1是不是看着头晕眼花，贼麻烦。
![在这里插入图片描述](https://img-blog.csdnimg.cn/202006212003319.png)
&emsp;&emsp;失败了也没关系，这里有更简单的方法。
&emsp;&emsp;只需要在命令行输入`.\Debug.bat  -m`，所有的东西控制台帮你搞定。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200621200830623.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200621200854458.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDU3MDA4Mw==,size_16,color_FFFFFF,t_70)
> 不会下载的[点击这里](https://blog.csdn.net/weixin_44570083/article/details/104285283)，进去查看我的`RDA8910 CSDK二次开发入门教程`专题第一篇博文`1、RDA8910CSDK二次开发：环境搭建`里面讲了怎么下载
> 这里只是我的学习笔记，拿出来给大家分享，欢迎大家批评指正，本篇教程到此结束


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)