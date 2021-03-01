# OSChina Android [客户端](http://www.oschina.net/app/)

**源代码请切换置对应的分支，master分支中今后不再放源代码。**

##历史分支

编号 | 标签名 | 发布版本 | 备注
------- | ------- | ------- | -------
1 | [v2.6.2](http://git.oschina.net/oschina/android-app/tree/v2.6.2/)  |v2.6.2(1606121625)| 当前最新版
2 | [v2.4](http://git.oschina.net/oschina/android-app/tree/v2.4/) | -- | -- |
3 | [v2.3](http://git.oschina.net/oschina/android-app/tree/v2.3/) | -- | 迁移到AndroidStudio |
4 | [v2.2.1](http://git.oschina.net/oschina/android-app/tree/v2.2.1/) | -- | Eclipse可用 |


##写在前面的话
从2.3版本开始，项目已经完成了gradle化，完全迁移到了android studio，如果想使用eclipse进行该项目的学习，可以clone [tag v2.2.1](http://git.oschina.net/oschina/android-app/tree/v2.2.1/)，不过需要注意的是，eclipse需要按照开发环境中提到的：进行butterknife注解设置

##开发环境
由于使用了较多的Eclipse项目Library，项目目前使用的是Eclipse。需要提示的是，由于butterknife注解特性，Eclipse需要开启注解功能，详细方法参考[这里](http://www.jcodecraeer.com/a/anzhuokaifa/androidkaifa/2015/0102/2247.html)。对于使用Android Studio的开发者，可能你们需要等待一段时间，项目目前正在Gradle化。当然，我们也欢迎由你来转换项目并通过PullRequest提交给我们，充分发挥社区化协作的优势。  

##项目简述
1. 底部导航  
    * 主界面的底部TAB导航采用[FragmentTabHost](http://git.oschina.net/oschina/osc-android-app/blob/master/osc-android-app/src/net/oschina/app/ui/MainTab.java)点击底部按钮时切换Fragment。中间的快捷操作按钮使用的是[自定义dialog](http://git.oschina.net/oschina/osc-android-app/blob/master/osc-android-app/src/net/oschina/app/ui/QuickOptionDialog.java)，通过点击时加入动画效果实现。  
2. 一级界面  
    * 包括资讯、动弹两个模块，采用[ViewPagerFragment](http://git.oschina.net/oschina/osc-android-app/blob/master/osc-android-app/src/net/oschina/app/viewpagerfragment/NewsViewPagerFragment.java)根据滑动到不同页面显示不同信息。  
3. 详情界面  
    * 详情界面包括[博客详情](http://git.oschina.net/oschina/osc-android-app/blob/master/osc-android-app/src/net/oschina/app/fragment/BlogDetailFragment.java)，[动弹详情](http://git.oschina.net/oschina/osc-android-app/blob/master/osc-android-app/src/net/oschina/app/fragment/TweetDetailFragment.java)，[新闻详情](http://git.oschina.net/oschina/osc-android-app/blob/master/osc-android-app/src/net/oschina/app/fragment/NewsDetailFragment.java)，[帖子详情](http://git.oschina.net/oschina/osc-android-app/blob/master/osc-android-app/src/net/oschina/app/fragment/PostDetailFragment.java)， [活动详情](http://git.oschina.net/oschina/osc-android-app/blob/master/osc-android-app/src/net/oschina/app/fragment/EventDetailFragment.java)等……是通过在Fragment中的WebView直接loadData()加载一段html数据并显示。  
    * 而详情Fragment的显示则是通过一个外部DetailActivity，来根据传入的参数不同来加载不同的Fragment。  
4. 链接跳转  
    * 整个应用打开链接的规则都定义在UIHelper.openBrowser()方法中，本方法会根据不同的url去解析，如果是www.oschina.net的链接，则会调用相应的界面去展示；如果是git.oschina.net我们目前会使用手机自带的浏览器打开(之后会改为使用[OscGit客户端](http://git.oschina.net/oschina/git-osc-android-project)打开)；如果不是oschina的站内链接，则使用内置浏览器打开。  
5. 侧滑菜单  
    * [侧滑菜单](http://git.oschina.net/oschina/osc-android-app/blob/master/osc-android-app/src/net/oschina/app/ui/NavigationDrawerFragment.java)采用系统的DrawerLayout实现。关于很多朋友好奇的左上角箭头，是采用的开源控件[DrawerArrowDrawable](http://git.oschina.net/oschina/osc-android-app/blob/master/osc-android-app/src/net/oschina/app/widget/DrawerArrowDrawable.java)(准确的说不应该是控件而是一个Drawable)

##依赖包介绍
1. jar包依赖  
  * 网络请求库 **android-async-http** ：http://loopj.com/android-async-http/  
  * 注解绑定控件 **butterknife** http://jakewharton.github.io/butterknife/  
  * 网络图片加载库 **KJFrameForAndroid** http://git.oschina.net/kymjs/KJFrameForAndroid  
  * XML解析库 **xstream** http://xstream.codehaus.org/  
2. 源码依赖  
  * **PhotoView-library** ：用于图片预览界面展示
  * **UmengShareLib** ：用于分享到第三方平台

##开源协议
 
	The MIT License (MIT)
	
	Copyright (c) 2016 OSChina.net
	
	Permission is hereby granted, free of charge, to any person obtaining a copy
	of this software and associated documentation files (the "Software"), to deal
	in the Software without restriction, including without limitation the rights
	to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
	copies of the Software, and to permit persons to whom the Software is
	furnished to do so, subject to the following conditions:
	
	The above copyright notice and this permission notice shall be included in all
	copies or substantial portions of the Software.
	
	THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
	IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
	FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
	AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
	LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
	OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
	SOFTWARE.
	
	




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)