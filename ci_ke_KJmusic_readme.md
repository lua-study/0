KJmusic
=======
# **KJ音乐 Android 客户端** #
KJ音乐是一个Android手机端音乐播放器，最低支持3.0版本。

## KJmusic 相关链接
* blog：http://my.oschina.net/kymjs/blog 
* QQ群：[257053751](http://jq.qq.com/?_wv=1027&k=WoM2Aa)(开发者群1)，[201055521](http://jq.qq.com/?_wv=1027&k=MBVdpK)(开发者群2)
* github项目地址：[https://github.com/KJFrame/KJMusic](https://github.com/KJFrame/KJMusic)

如你希望通过源码学习，请先查看[KJFrameForAndroid](https://github.com/kymjs/KJFrameForAndroid)开发框架用法
启动Eclipse，点击菜单并导入Android客户端项目，请确保你当前的Android SDK是最新版。 
如果编译出错，请修改项目根目录下的 project.properties 文件。 
推荐使用Android 4.0 以上版本的SDK,请使用JDK1.6编译：

> target=android-17

## 运行截图
[![image1](http://imgsrc.baidu.com/forum/pic/item/0047dcdda144ad34057480b5d4a20cf430ad8599.jpg)](https://github.com/KJFrame/KJMusic)
[![image2](http://imgsrc.baidu.com/forum/pic/item/74b9ac1190ef76c6dd3ffc199916fdfaae5167f3.jpg)](https://github.com/KJFrame/KJMusic)
[![image3](http://imgsrc.baidu.com/forum/pic/item/98479654564e925842ff81dc9882d158cdbf4e99.jpg)](https://github.com/KJFrame/KJMusic)

## 授权协议
本项目采用 GPL v2授权协议: 
GPLV2协议说明：GPL协议的主要内容是只要在一个软件中使用(“使用”指类库引用，修改后的代码或者衍生代码)GPL 协议的产品，则该软件产品必须也采用GPL协议，既必须也是开源和免费。这就是所谓的”传染性”。GPL协议的产品作为一个单独的产品使用没有任何问题，还可以享受免费的优势。 
你拥有的权利: 
    以任何目的运行此程序的自由; 
    再发行复制件的自由; 
    改进此程序，并公开发布改进的自由. 
你需要注意: 
                如果在发布源于GPL的软件的时候，同时添加强制的条款，以在一定程度上保障其它一些人的权益，那么将无权发布该软件。 
********欢迎大家在这个基础上进行改进，并与大家分享。 

			Copyright (C) 2014  Tao Zhang

    This program is free software; you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation; either version 2 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License along
    with this program; if not, write to the Free Software Foundation, Inc.,
    51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.

## **一、项目的目录结构** ##
> 根目录 
> ├ src 
> ├ libs 
> ├ res 
> ├ AndroidManifest.xml 
> ├ LICENSE.txt 
> ├ proguard.cfg 
> └ project.properties 

下面是src目录的子目录（未来可能变更）： 
	> src 
	> ├ org.kymjs.music 
	> ├ org.kymjs.music.ui 
	> ├ org.kymjs.music.ui.fragment 
	> ├ org.kymjs.music.ui.widget 
	> ├ org.kymjs.music.adapter 
	> ├ org.kymjs.music.utils 
	> ├ org.kymjs.music.bean 
	> ├ org.kymjs.music.service 
	> ├ org.kymjs.music.db 
	> └ org.kymjs.music.resolve 
	> └ org.kymjs.music.receiver 
	
	org.kymjs.music	- APP启动及管理包
	org.kymjs.music.ui - APP界面包
	org.kymjs.music.ui.fragment - APP碎片界面
	org.kymjs.music.ui.widget - APP自定义控件
	org.kymjs.music.adapter - APP适配器包
	org.kymjs.music.util - APP工具包，帮助类
	org.kymjs.music.bean - APP实体类包
	org.kymjs.music.service - APP所需服务
	org.kymjs.music.db - APP数据库相关
	org.kymjs.music.resolve - APP网络数据解析器
	org.kymjs.music.inter - 所需接口包
	org.kymjs.music.receiver - 接收全局广播
	
## **二、项目的功能流程** ##
#### 1、APP启动流程 ####
	应用首次启动，将跳转至org.kymjs.music包下的AppStart，在载入动画和资源的同时判断是否为首次安装程序，之后跳转到相应的Activity（欢迎界面Welcome或主界面Main）。 

#### 2、APP访问API流程 ####
	**1) 初始化控件** 
		首页Activity(Main.java)在initWidget()方法里面加载布局文件(Main.xml)，初始化底部栏bottomBar并设置点击事件监听。 
		注：布局文件在/res/layout目录，点击事件监听器写在widgetClick()方法中。 
	**2) 异步线程访问** 
	**3) 解析数据显示** 
		数据解析类统一写在resolve包下 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)