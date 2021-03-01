#Spring-Boot-Tio
使用SpringBoot，融合[tio即时通讯框架](http://git.oschina.net/tywo45/t-io "tio即时通讯框架")。


tio采用 消息头+消息体的模式，为了兼容现有设备的Socket（无消息头），对Server的Handler进行调整，encode加消息头；decode无消息头。

测试类在test/，直接运行XXXClientTest的main方法即可。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)