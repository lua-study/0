简介----[开源地址](http://git.oschina.net/ethanzhu/stockhelper)
--
股票小助手 WebApp，提供股票计算小工具包括补仓、加仓、保本价、止盈止损价计算等.

* 应用了html5 应用缓存manifest技术，可以断网访问.

* 基于mobile-angular-ui，[angularjs中文社区](http://www.angularjs.cn/)

> Mobile Angular UI is an HTML5 mobile UI framework that will let you use Angular Js and     Bootstrap 3 for mobile app development.

> GettingStarted, Demo, Docs at http://mobileangularui.com.

操作本地localStorage用到了[StoreDB](https://github.com/djyde/StoreDB/)
.StoreDB是一个基于localStorage的本地储存库，通过模拟MongoDB的一些API和概念（如“集(collection)”和“文档(document)”），使你能使用 localStorage 储存复杂数据。

> 已经上线到UC浏览器轻应用中心，请在UC浏览器上扫描或者搜索"股票小助手"使用

![uc轻应用二维码](http://plus.uc.cn/qrcode?appId=5224)


项目结构
----
**master分支：html源码，将部署到SAE[演示平台1](http://qmxlabs.sinaapp.com/StockHelper/)，[演示平台2](http://stockhelp.oschina.mopaas.com/)**
> 根目录 
> ├ dist （框架js库及bootstrap css） 
> ├ StockHelper （WebApp源码） 
> ├ 截图  
> ├ demo (mobile-angular-ui Demo源码，可以去演示平台2查看效果) 
> ├ examples (mobile-angular-ui 案例，可以去演示平台2查看效果) 

安装配置
----

**安装配置**

1. git clone源码到本地；
2. 直接放到服务器下运行;


更新记录
----

 - 2015.2.1：git配置  ---Ethan
 - 2015.2.2： 加入html5应用manifest缓存功能  ---Ethan
 - 2015.2.2： 提交应用到UC浏览器、qq浏览器开放平台


演示截图
----

![QQ截图20150201184829](http://git.oschina.net/uploads/images/2015/0201/190834_db3beba5_77541.png)

![QQ截图20150201185015](http://git.oschina.net/uploads/images/2015/0201/190834_cca32977_77541.png)

![QQ截图20150201185024](http://git.oschina.net/uploads/images/2015/0201/190834_ff349d85_77541.png)

![QQ截图20150201185042](http://git.oschina.net/uploads/images/2015/0201/190834_bb687c9c_77541.png)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)