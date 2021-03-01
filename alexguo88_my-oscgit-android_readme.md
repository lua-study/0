# ScreenShot
![图片描述](./screenshot/Screenshot_1.jpeg)
![图片描述](./screenshot/Screenshot_2.jpeg)
![图片描述](./screenshot/Screenshot_3.jpeg)
![图片描述](./screenshot/Screenshot_4.jpeg)
![图片描述](./screenshot/Screenshot_5.jpeg)
![图片描述](./screenshot/Screenshot_6.jpeg)
 
### Git@OSC非官方android客户端
本产品是Git@OSC非官方客户端，遵循Material Design设计原则，官方客户端界面实在是丑。
参考官方客户端地址：http://http://git.oschina.net/appclient
- 界面采取Material Design设计风格
- 使用android support design中的控件替代原生或者其它开源控件
- 使用RecycleView代替Listview
- 使用谷歌Volley代替android-async-http和universal-image-loader
- 增加切换主题功能

最新代码请到https://github.com/BinJing/my-oscgit-android.git下载

###已知bug
1. ProgressBar,ProgressDialog等控件在android L平台下不会随着主题变化而变化

### 引用到的开源库：
- compile 'com.android.support:design:22.2.0'
- compile 'com.jakewharton:butterknife:6.1.0'
- compile 'com.jenzz:materialpreference:1.3'
- compile 'de.hdodenhof:circleimageview:1.3.0'
- compile files('libs/volley.jar')
- compile files('libs/gson-2.3.1.jar')
- compile 'de.greenrobot:eventbus:2.4.0'

### 开源协议
- [Apache Version 2.0](http://www.apache.org/licenses/LICENSE-2.0.html)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)