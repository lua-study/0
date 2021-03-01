## Electron 快速开发框架 doc V1.0
==Author：小狄子 diyuchen@esunny.cc==
#### 快速开始
1. npm i 安装依赖
1. 在config/appconfig.json中修改`"firstview": "./view/app"`为你的应用程序入口视图名
2. 在view/使用html编写你的代码并引入【视图名Controller】
3. 在controller/视图名Controller.js文件中编写你的代码逻辑，jq和nodejs可以混用哦
4. 按需引用service/、common/和model/中的内容
5. 需要跳转视图？在Controller文件中引入BaseController后调用BaseController的`openNewWindow`方法
6. 需要在新的视图接收参数？同样引入BaseController后调用BaseController的`getWindowArgs`
7. 没有需要的方法？到了你自己动手的时候了！
8. Enjoy Coding ~

#### 框架来源
前段时间，我在单位工作过程中，要求完成一个客户端应用程序，但是我并不会QT或者JavaSwing之类的图形界面开发，C#曾经学过一些WinForm和WPF但是都早已忘记，且我的前端设计水平简直就是渣渣，所以就想到了之前在学校曾经接触过的Electron跨平台应用开发程序，用HTML，Css及JavaScript构建跨平台桌面应用程序。

准备开始，我跟着书（《跨平台桌面应用开发：基于Electron与NW.js》作者:（丹麦）Paul B. Jensen（保罗 B. 詹森））尝试编写一些简单的例子，书中的例子还基本易懂，并且可以运行，这是个良好的开端，但是过了一段时间我意识到一个问题，书中的例子都是单页应用，即只有一个index.html文件，或者说只有一个渲染窗口，这个似乎不太符合我的预期。

那么就先看看有没有别人的轮子吧，还别说真的有，但是似乎都是使用诸如React，AngularJs，Vue等主流前端框架进行开发的，这就有点泪奔了，我好菜啊，这些也不会，诶...

学框架来不及，但是应用又要马上开发，磨刀不误砍柴工，我就先给自己设计一套框架吧，思考了一下主流框架都干了哪些事情，我需要做哪些事情，进行了设计。

#### 框架适用场景
如果您的应用不是单页应用而是多页应用，且多页应用之间需要传递参数，比如一个列表页的列表项点击之后可以打开详情，需要传递列表项ID，这样的情况，就适合使用我的框架，我重写了简单的路由，封装了界面加载方法和路由传参，开发者只需要调用`openNewWindow(view,args)`方法即可打开新的路由，框架自动的处理了主进程和渲染进程间的通信，当然你也可以任意添加和修改程序逻辑。

如果你希望自己扩展框架的功能，没问题，框架的各个组件全部都是松耦合的，你完全可以在任意层级添加任意组件以任意可行的写法写任意代码，（当然我不保证你写的代码能正常工作），如果你需要，我提供了几个简单的Service的例子，可以参考我的例子来。

#### 框架设计思想
框架的设计思想为MVC加Service方式，组合而成。
MVC是老生常谈，但是我这里似乎不能完全意义上的称做MVC，只是有MVC结构罢了，（没错MVC也是松耦合且可以按需调整），Model用来专注干数据或者业务该干的事情，（你也可以放在Controller做，没人阻止你这么干）。

框架整体上分为MVC、common、service和process四大结构，common中有Logger，Config，Router三个组件，分别用于日志，配置和路由。service自己封装了一些诸如消息通知，http请求，用`localStorage`本地化存储等服务，开发者可以自行扩展，并按需引用，process中主要针对主进程和渲染进程分别写了`MainProcessHelper`和`RendererProcessHelper`，用来辅助主进程和渲染进程的通信，同时`MainProcessHelper`也负责在electron启动时启动渲染窗口。

#### 框架约定

视图写在view文件夹中，控制器写在Controller文件夹中，建议命名为类似于【DemoController】,控制器代码需要在html用通过script标签的src属性引入，在Controller中可以按需通过require引入服务及common组件，在Controller中可以使用jquery，或者开发者可以自行扩展。
> 建议：
在每个Controller中引用BaseController，可以方便使用openNewWindow方法
在每个Controller中引用RendererProcessHelper，可以方便的像主进程通知消息，方便的注册回调函数。

#### 框架引用的第三方组件
- log4js 日志 `https://www.npmjs.com/package/log4js`
- jquery DOM操作(可以按需引入) `http://jquery.com/`
- unirest 轻量级http请求库 `https://unirest.io/`
- art-template 前端模板框架 `https://github.com/aui/art-template`
- electron-notifications 消息通知 `https://github.com/blainesch/electron-notifications`
- AdminLTE 后台管理系统界面模板 `https://adminlte.io/`

#### 没有解决你的问题？
欢迎自行扩展或者邮件联系我，如果你有更棒的点子也欢迎交流~
大佬们放过我这个渣渣吧，只是还没空学主流框架QAQ后面一定学！

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)