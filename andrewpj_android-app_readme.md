android-app
===========

# **开源中国社区 Android Design客户端项目简析** #

根据OSChina的android开源代码修改而来的。适用于Android手机使用。
依赖的项目：
android-support-v4，使低版本的Android支持Fragment。
android-support-v7，使低版本的Android支持ActionBar。
android-support-v4-preferencefragment，使低版本的Android支持PreferenceFragment。

与原项目的变化：
删除Main.java类，用MainActivity.java来代替，MainActivity来管理其它的MainFragment。

Mian.java中的功能分别由以下文件代替:

> ——————————————————————————————————NewMainFragment              三个页面
						  			     |
					  			             管理
					  		    	     |
 	   			    最新新闻    NewsFragment———BlogFragment     最新博客、推荐阅读



> ————————————————————————————————QuestionMainFragment           五个页面
										  |
					 	  			       管理
					  					  |  
 	          	   				   QuestionFragment     问答、分享、综合、职业、站务
 		 

 
> —————————————————————————————————TweetMainFragment             三个页面
										  |
								 	       管理
					  					  |
	         最新动弹、热门动弹   TweetFragment————UesrTweetFragment   我的动弹
	
	
	
> —————————————————————————————————ActiveMainFragment            五个页面
					 					  |
								 	       管理
					  					  |
 最新动态、我、评论、我自己   ActiveFragment————MessageFragment     我的消息
 
 		  
BadgeView的状态和页面数据分离到BadgeManager.java和HandlerManager.java这两个单例来管理。


未完成待续...



*注：本文假设你已经有Android开发环境*

启动Eclipse，点击菜单并导入Android客户端项目，请确保你当前的Android SDK是最新版。 
如果编译出错，请修改项目根目录下的 project.properties 文件。 
推荐使用Android 4.0 以上版本的SDK,请使用JDK1.6编译：

> target=android-15

**本项目采用 GPL 授权协议，欢迎大家在这个基础上进行改进，并与大家分享。**

下面将简单的解析下项目：

## **一、项目的目录结构** ##
> 根目录 
> ├ src 
> ├ libs 
> ├ res 
> ├ AndroidManifest.xml 
> ├ LICENSE.txt 
> ├ proguard.cfg 
> └ project.properties 

**1、src目录** 
src目录用于存放项目的包及java源码文件。

下面是src目录的子目录：
> src 
> ├ com.weibo.net 
> ├ greendroid.widget 
> ├ net.oschina.app 
> ├ net.oschina.app.adapter 
> ├ net.oschina.app.api 
> ├ net.oschina.app.bean 
> ├ net.oschina.app.common 
> ├ net.oschina.app.fragment 
> ├ net.oschina.app.interface 
> ├ net.oschina.app.ui 
> └ net.oschina.app.widget 

- com.weibo.net — 新浪微博SDK源码包
- greendroid.widget — 快捷菜单栏组件(国外UI库[GreenDroid](http://www.oschina.net/p/greendroid))
- net.oschina.app — APP启动及管理包
- net.oschina.app.adapter — APP列表适配器包
- net.oschina.app.api — API访问包
- net.oschina.app.bean — APP实体包
- net.oschina.app.common — APP工具包
- net.oschina.app.ui — APP界面包
- net.oschina.app.widget — APP控件包
- net.oschina.app.interface — 新增的接口
- net.oschina.app.fragment — 新增的碎片


**2、libs目录** 
libs目录用于存放项目引用到的jar包文件。

下面是在原项目上增加的jar包文件：
> libs 
> └ android-support-v4.jar 

- android-support-v4.jar — Google的扩展包，使低版本的Android支持Fragment等组件。

**3、res目录** 
res目录用于存放项目的图片、布局、样式等资源文件。

下面是res目录的子目录：
> res 
> ├ anim 
> ├ color 
> ├ drawable 
> ├ drawable-hdpi 
> ├ drawable-ldpi 
> ├ drawable-mdpi 
> ├ layout 
> ├ menu 
> ├ raw 
> ├ values 
> ├ values-14 
> └ xml 

- anim — 动画效果
- color — 颜色
- drawable/drawable-hdpi/drawable-ldpi/drawable-mdpi — 图标、图片
- layout — 界面布局
- menu — 菜单
- raw — 通知音
- values — 语言包和样式
- xml — 系统设置

**4、AndroidManifest.xml** 
AndroidManifest.xml用于设置应用程序的版本、主题、用户权限及注册Activity等。

## **二、项目的功能流程** ##

#### 1、APP启动流程 ####
AndroidManifest.xml注册的启动界面为"AppStart"，具体文件为net.oschina.app\AppStart.java文件。 检查是否安装后的第一次启动，是的话显示欢迎界面之后，通过意图(Intent)跳转到首页（net.oschina.app.ui\Main.java）。 不是第一次启动的话，直接跳转到首页。 
*注：除启动界面之外，其他所有界面都放在src\net.oschina.app.ui和src\net.oschina.app.fragment包中。*

#### 2、APP访问API流程 ####

以首页资讯列表显示访问API数据为例：

**1) 初始化控件** 
首页MainActivity(MainActivity.java)在onCreate()方法里面加载布局文件(main_activity_layout.xml)，对下拉刷新列表控件(PullToRefreshListView)进行了初始化，并设置了数据适配器(ListViewNewsAdapter)。 
*注：main_activity_layout.xml布局文件在res\layout目录下；PullToRefreshListView控件在net.oschina.app.widget包；ListViewNewsAdapter适配器在net.oschina.app.adapter包。*

**2) 异步线程访问** 
列表控件初始化后，开启一个线程方法(loadLvNewsData())，该方法中调用全局应用程序类(AppContext)来访问API客户端类(ApiClient)。通过ApiClient以http方式请求服务器的API。返回响应的XML数据，再通过实体Bean(NewsList)解析XML，返回实体(NewsList)给UI控件(PullToRefreshListView)展示。 
*注：AppContext全局应用程序类在net.oschina.app包；ApiClient API客户端类在net.oschina.app.api包。*

**3) 解析数据显示** 
服务得到请求，将返回对应的资讯XML数据，再通过资讯实体类(NewsList)解析XML，返回实体(NewsList)给UI控件(PullToRefreshListView)展示。 
*注：NewsList实体类在net.oschina.app.bean包。*

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)