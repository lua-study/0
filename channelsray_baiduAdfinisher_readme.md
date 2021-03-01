# baiduAdfinisher
屏蔽百度线上产品页面广告chrome扩展程序，兼容各大“国产”浏览器急速版(360、搜狗、猎豹、百度、UC、QQ等)以及其他webkit内核浏览器。

 
### 离线chrome扩展程序（.crx文件）安装方式： 
1、打开chrome扩展程序页面(chrome://extensions/ 或者 菜单 > 更多工具> 扩展程序)； 
2、把.crx文件拖进该页面（国产浏览器直接拖入任意页面）。 
 

效果截图：  
![github](https://raw.githubusercontent.com/unclehking/baiduAdfinisher/master/screenshot/sp01.png "github")   



 ###2016-05-25 
 现已支持百度全线线上产品页面广告屏蔽(搜索、新闻、贴吧、知道、音乐、图片、视频、文库、百科等)。 

 ###2016-05-26 
 新增：点击扩展图标打开(如果已打开则切换到)百度页面，当书签用，省去每次输入地址链接的麻烦 ^_^ 
### 2016-06-04 
 ES6编写 / "use strict"
 ```java
 const  url="d3d3LmJhaWR1LmNvbQ==";
 chrome.browserAction.onClicked.addListener((tab) =>{
 	chrome.tabs.getAllInWindow(null, fuckBat = tabs =>{
 		for(var t of tabs){
 			if (t.url.match(atob(url))) {
 				fuckBat.bTab = true;
 				chrome.tabs.update(t.id, {selected:true});
 				break;
 			}
 		}
 		!fuckBat.bTab && chrome.tabs.create({"url":`https://${atob(url)}`, "selected":true});
 	});
 });
 ```
### 2016-06-04 
1、屏蔽“音乐盒”播放页广告
![github](https://raw.githubusercontent.com/unclehking/baiduAdfinisher/master/screenshot/q0.jpg "github")   
![github](https://raw.githubusercontent.com/unclehking/baiduAdfinisher/master/screenshot/q1.jpg "github")   

### 2016-06-05 
1、修正贴吧置顶帖被当做广告屏蔽的bug。

### 2016-06-07 
1、修正百度翻译被当做广告屏蔽的bug。
###2016-06-13 
1、屏蔽音乐盒播放暂停时展示的广告。

### 2016-06-15 
1、新增音乐盒歌词显示“K歌”模式(双击歌词区域进入、退出)。
![github](https://raw.githubusercontent.com/unclehking/baiduAdfinisher/master/screenshot/q2.jpg "github")   

### 2016-07-08 
1、修复贴吧回帖之后所有回帖被隐藏的bug。

### 2016-07-28 
1、修复贴吧广告屏蔽css规则失效的bug。


 持续更新中...


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)