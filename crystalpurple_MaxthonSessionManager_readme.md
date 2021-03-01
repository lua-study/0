# Maxthon Session Manager

作者：NoAnyLove  
博客： 

## TL;DR

傲游浏览器【上次未关闭页面】增强工具，一个通过书签加载的JavaScript脚本，实现了导入、导出以及管理【上次未关闭页面】的功能。

## 说明

作为一个【上次未关闭页面】重度依赖症患者，总喜欢把没来得及看，但又感觉有用的文章留在【上次未关闭页面】中。久而久之就积累了数百条网址。在经历了几次浏览器意外关闭，导致【上次未关闭页面】中的数据彻底丢失的惨痛经历之后，傲游官方也一直没有推出有效的备份方案，于是只好自己动手丰衣足食，用JavaScript开发了这个【上次未关闭页面】增强工具。

【上次未关闭页面】通过JavaScript访问一个特殊的对象`runtime.ConfigManager`获取未关闭页面的数据。但因为傲游浏览器的插件机制限制了对一些特殊页面（比如上次未关闭页面和历史页面等）和对象（`runtime.ConfigManager`对象）的访问，所以对【上次未关闭页面】的操作不能通过编写傲游插件实现。

在看过【上次未关闭页面】自带的app.js文件后，用JavaScript写了这个增强工具，需要通过收藏夹书签进行加载。缺少艺术细胞，所以界面丑陋大家就不要嘲笑我了。

## 功能

* 管理多个【上次未关闭页面】数据（保存在浏览器的LocalStorage中）
* 导入/导出【上次未关闭页面】数据
* 将【上次未关闭页面】导出为HTML网页（仅作为链接列表，不具备傲游浏览器【上次未关闭页面】的功能）

**PS**：因为不确定出现丢失【上次未关闭页面】数据时，浏览器的LocalStorage数据是否会受到影响，所以如果有特别重要的数据，还是导出为文件比较靠谱。

## 使用说明

将下面的代码保存为书签，然后在【上次未关闭页面】中点击该书签，启用增强工具。

```JavaScript
javascript:(function(path){var head=document.getElementsByTagName('head')[0];var script=document.createElement('script');script.src=path;head.appendChild(script);})('http://git.oschina.net/noanylove/MaxthonSessionManager/raw/master/Init.js');void(0);
```

脚本文件放在了Git@OSC的服务器上，根据个人网速快慢，加载该工具的时间大概会在1~5秒之间。

具体操作可以参见下面的GIF动图

![安装说明](http://git.oschina.net/noanylove/MaxthonSessionManager/raw/master/Screenshot/t1.gif)

**图一：安装说明**

## 预览图

![界面图](http://git.oschina.net/noanylove/MaxthonSessionManager/raw/master/Screenshot/2.png)

**图二：Maxthon Session Manager界面效果**

![另存为文件](http://git.oschina.net/noanylove/MaxthonSessionManager/raw/master/Screenshot/3.png)

**图三：将【上次未关闭页面】另存为文件**

## 感谢

* Eli Grey的[FileSaver.js](https://github.com/eligrey/FileSaver.js/)
* Henrik Joreteg的[templatizer.js](https://github.com/HenrikJoreteg/templatizer)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)