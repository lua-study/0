# Live2d的看板娘——伊斯特瓦尔(Histoire) 
#### 可用于网页端显示Live2D版的伊斯特瓦尔(Histoire) emlog插件版可以看这里：[传送门](https://www.wikimoe.com/?post=75)
#### 基于[《给博客添加能动的看板娘(Live2D)-将其添加到网页上吧》](https://imjad.cn/archives/lab/add-dynamic-poster-girl-with-live2d-to-your-blog-02)上的源码进行修改。
#### 在原先的基础上加上了如下功能：

	1.可以基于图灵机器人的聊天功能（需要自己写接口，默认隐藏）。
	2.能够随意移动并记录位置（关闭浏览器后失效）。
	3.能够随意唤醒或者关闭并记录状态。
	4.自动判断浏览器是否为IE或者手机浏览器，如果判断为true则不加载伊斯。
	5.给骚扰伊斯加了限制频率，不能狂骚扰伊斯了。

### 准备工作
首先到下载代码。

然后把解压出来的文件夹改名为：live2d 。

### 正式开工，文字部分参考自[在 Web 上展示 Live2D 吧！](https://github.com/galnetwen/Live2D)
在需要页面的头部文件（header）引入界面样式，在 head 标签内插入如下代码：
```html
 
```

在 需要页面的body 标签内找到合适的位置插入 Live2D 看板娘的元素，按照 Html 书写规范写 
```html
 
      
      
     
    	 
        	 
         
         
        	 
             发送 
         
     
     
     
    	  
    	  
          
          
          
         
          
         
         
     
 
 召唤伊斯特瓦尔 
```
如果需要BGM支持可以按照上面的例子添加：
```html
 
```
在 需要页面的 body 标签结束前插入如下代码：
```html
  
 
var message_Path = '/live2d/';//资源目录，如果目录不对请更改
var talkAPI = "";//如果有类似图灵机器人的聊天接口请填写接口路径
 
  
  
```

鼠标放在页面某个元素上时，需要 Live2D 看板娘提示的请修改 message.json 文件。

**示例：**

	{
		"mouseover": [
			{
				"selector": ".title a",  //此处修改为你页面元素的标签名
				"text": ["要看看 {text} 么？"]  //此处修改为你需要提示的文字
			},
			{
				"selector": "#searchbox",
				"text": ["在找什么东西呢，需要帮忙吗？"]
			}
		],
		"click": [  //此处是 Live2D 看板娘的触摸事件提示
			{
				"selector": "#landlord #live2d",
				"text": ["不要动手动脚的！快把手拿开~~", "真…真的是不知羞耻！","Hentai！", "再摸的话我可要报警了！⌇●﹏●⌇", "110吗，这里有个变态一直在摸我(ó﹏ò｡)"]
			}
		]
	}


然后，刷新你的页面，看看效果吧！

注意路径别弄错了噢 ~  
PHP 程序推荐使用主题函数获取绝对路径。

### 效果预览
![](https://t1.aixinxi.net/o_1c3mofql9osmpeb1hfvsbv1hqua.gif-j.jpg)  

	
### 模型说明
本插件仅供学习和交流使用，禁止用于商业用途。
本插件用到的模型为《超次元游戏海王星》系列中的伊斯特瓦尔，动作表情则是取自Live2d官网的demo，故版权归各官方所有。
原项目使用了 GPL v2 开源协议。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)