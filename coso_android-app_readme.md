#哎嘛-OSCHINA第三方客户端
===========
点击截图到应用市场下载最新版APP
[![屏幕截图](http://git.oschina.net/tonlin/android-app/raw/master/screenshots/screen_shots.jpg)](http://zhushou.360.cn/detail/index/soft_id/1987733)

#介绍
哎嘛fork于最初版的OSC官方客户端，在此基础上进行了大量的UI界面修改和代码重构并于2014/09/18发布第一个版本。
如果同学你对哎嘛感兴趣，你可以star它关注它的最新动态。如果你有更多宝贵的时间来阅读哎嘛的代码，你将可以学习到如下几大部分内容：
 1. 如何搭建一个Material Design设计风格的APP。
 2. 如何使用FragmentTabHost、Fragment来搭建程序界面的主体框架
 3. 如何创建一个通用的数据适配器BaseAdapter。
 4. 如何使用async-http-loader请求网络数据
 5. 如何解析XML数据
 6. 如何缓存网络数据
 7. 如何使用ImageLoader、 Fresco 显示图片
 8. 如何快速搭建一个IM应用

## 开源协议
本项目采用 GPL 授权协议，欢迎大家在这个基础上进行改进，并与大家分享。
* [GPL](http://www.gnu.org/licenses/licenses.en.html)

## 编译

### 注意
  从V1.3.0.0beta版本开始使用了[环信SDK](http://www.easemob.com/)，在AndroidManifest.xml文件中有关于环信的APPKEY配置。
笔者这里没有上传自己的Key，同学们需要自行到环信官网注册。 同时也使用了[BmobSDK](http://www.bmob.cn/)，
需要在net.oschina.app.v2.base.Config类中配置相应的APPID和ACCESS_KEY，也需要同学们自行到Bmob官网注册配置。

### 使用Gradle编译
最简单的方法是通过安装[Android Studio](https://developer.android.com/sdk/index.html) v1.+和[Gradle](https://www.gradle.org/) v2.2.1进行编译，
安装完成后，你就可以通过AndroidStudio导入工程进行开发了。 具体操作步骤如下：
 1. 确保你的操作系统安装了JDK开发环境。
 2. 确保你已经下载了Android SDK,并且下载了Build-tools v21.1.2 和 Android 5.0.1 SDK。
 3. 确保你已经下载了Android Studio 和 Gradle。
 4. 打开Android Studio导入工程
 剩下工作请交给Gradle它会帮你完成剩下的事情。

### 你可能会遇到的问题
使用gradle 或者 Android Studio会遇到一些网络障碍。这些障碍，使用 [红杏为开发者开放的免费的公益代理](http://honx.in/_VUh8JIkWGiHr2XaA) 可以解决。

## 感谢
 本项目也使用了其他第三方开源库例如：
 * [Android-maven-plugin](https://github.com/jayway/maven-android-plugin)
 * [ViewPagerIndicator](https://github.com/JakeWharton/Android-ViewPagerIndicator)
 * [PhotoView](https://github.com/chrisbanes/PhotoView)
 * [Android-sticky-listheaders](https://github.com/emilsjolander/StickyListHeaders)
 * [Android-ObservableScrollView](https://github.com/ksoichiro/Android-ObservableScrollView)
 * [Nineoldandroids](https://github.com/JakeWharton/NineOldAndroids)
 * [Material Dialogs](https://github.com/afollestad/material-dialogs)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)