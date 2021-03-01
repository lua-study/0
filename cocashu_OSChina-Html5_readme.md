## oschina-html5-app
## 开源中国社区 html5 客户端项目简析

#### 注：本程序基于phonegap构建。目前只支持安卓版本。

本文假设你已经有Android开发环境，启动Eclipse，点击菜单并导入 *OSChina-Html5/platforms/android* 客户端项目，请确保你当前的Android SDK是最新版。
如果编译出错，请修改项目根目录下的 project.properties 文件。

target=android-17

本项目采用 GPL 授权协议，欢迎大家在这个基础上进行改进，并与大家分享。

下面将简单的解析下项目：

### 1、项目的目录结构

OSChina-Html5 
├ platform ----- 存放平台项目，目前只有安卓项目 
├ plugins ----- phonegap插件 
└ www ----- 存放html、css、js文件


### 2、www目录简介

入口文件为：www/news/index.html

www 
├ base ----- 基础包，包含：基础样式，公共方法 
├ commom ----- 通用组件，包含：评论组件 
├ my ----- 我的空间模块 
├ news ----- 资讯模块 
├ project ----- 开源软件库模块 
├ question ----- 问答模块 
├ tweet ----- 动弹模块 
├ user ----- 用户信息模块 
└ piece ----- 基础依赖库

### 3、如何编译项目

直接导入*OSChina-Html5/platforms/android* 客户端项目，编译，打包即可。

### 4、如何修改html文件。

直接修改*OSChina-Html5/www/*下的文件，然后拷贝到 *OSChina-Html5/platforms/android/assets/www/*下文件，run，即可看到效果。

### 5、页面访问规则

通过backbone的router来做路由，采用的是hash的方式。
访问地址的主要理解为： 

index.html（模块入口）# 要访问的模块 / 访问模块的视图

通过piece/js/core/cocrouter.js检测url上的哈希变化，然后加载要访问的模块和视图，然后通过piece/js/core/mainview.js来切换页面的内容。
例如，我要访问资讯列表页面，
地址为：http://127.0.0.1/OSChina-Html5/www/news/index.html#news/new-list

### 6、如何调试

使用--disable-web-security参数打开chrome。然后打开 *www/news/index.html* 即可调试页面。由于部分页面使用到phoengap插件，需要在android应用内才可以体现。

如果需要在Android webview内调试，推荐使用weinre。

### 7、开发工具

推荐使用sublime text 2\3 。

### 8、软件截图

#### 最新资讯：

![44FCA404573530C95207C36FD065667B](http://git.oschina.net/uploads/images/2014/0121/174918_5fab240e_1151.jpeg)
  
#### 软件详情：

![8D31DC493486133FC1857649FC87DD2F](http://git.oschina.net/uploads/images/2014/0121/174917_051425ae_1151.jpeg)

#### 新闻正文：

![7380D25C2329263E7F2E0587151BEF73](http://git.oschina.net/uploads/images/2014/0121/174919_f8103ef9_1151.jpeg)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)