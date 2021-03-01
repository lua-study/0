#[极客开发]WechatRobot - PHP微信机器人开发包

* 首先，欢迎使用WechatRobot！
* 其次，这是一个很简单的开包，但可以协助您快速进行微信开发！
* 最后，Here We Go!

*利用这个短而美的微信包，您可以使用你原来熟悉或者喜欢的框架来进行微信开发。*

##一进，一出，一机器人
结构很简单：一进，一出，一机器人。用文字UML图表示是：   
```
Wechat_InMessage  ---- (A)Wechat_Robot ----  (A)Wechat_OutMessage
```

 ![mahua](http://static.oschina.net/uploads/space/2015/0124/000912_HLoH_256338.jpg)
 
##使用示例
####1. 实现自己的机器人
```
//$ vim ./examples/MyRobot.php 

 setContent('Hello World!');
    }

    //...

}
```
####2. 统一入口文件
```
//$ vim ./examples/index.php 

 run();

    echo $rs;
} catch (Exception $ex) {
    //TODO: 出错的处理
}
```

##快速请求
在部署好环境后，用随便输入一个文本内容，即可以微信上看到这样的效果：

 ![mahua](http://webtools.qiniudn.com/1630110534.jpg)
 
 同时，也可以快速执行下面的命令来模拟请求：
 
 ```
 //$ vim ./examples/test.php 
    
   
 1419757723 
   
   
 6097812988731466682 
 ';

echo "返回给微信的报文是：\n";

require_once dirname(__FILE__) . '/index.php';

echo "\n\n";
 ```
 
 执行一下：
 
  ```
 $ php ./test.php 
模拟发送一条文本消息，内容为：
一个人

返回给微信的报文是：
 
   
   
 1422027410 
   
   
 0 
 
 ```
 
##单元测试
我们不仅提供可以重用的代码，更希望可以把最佳实践分享给大家。所以，在这里，依然，可以看到我们坚持单元测试的身影。

感兴趣的同学可以看下对应的单元测试代码。

```
[tests]$ tree
.
└── Wechat
    ├── OutMessage
    │   ├── Wechat_OutMessage_Image_Test.php
    │   ├── Wechat_OutMessage_News_Test.php
    │   └── Wechat_OutMessage_Text_Test.php
    ├── Wechat_InMessage_Test.php
    └── Wechat_Robot_Test.php
 ```
    
##目录结构
代码很简洁，也很容易理解。我们没有提供过多的功能，因为我们相信：少即是多。
只是对微信的接收、回应做了高层的抽象，即对规约层做了统一，便于各开发人员在自己原有的框架基础上快速引入进行微信开发。

```
[Wechat]$ tree
.
├── InMessage.php
├── OutMessage
│   ├── Image.php
│   ├── Music.php
│   ├── News
│   │   └── Item.php
│   ├── News.php
│   ├── Text.php
│   ├── Video.php
│   └── Voice.php
├── OutMessage.php
├── Plugin
│   ├── DeviceEvent.php
│   ├── DeviceText.php
│   ├── Event.php
│   ├── Image.php
│   ├── Link.php
│   ├── Location.php
│   ├── Text.php
│   ├── Video.php
│   └── Voice.php
└── Robot.php

3 directories, 19 files
```
##帮助
如有问题，欢迎交流，谢谢！
同时，感谢LaneWeChat，因为部分内容参考于它：http://www.oschina.net/p/lanewechat

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)