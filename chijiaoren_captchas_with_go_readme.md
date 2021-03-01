
# captchas_with_go
关于go语言验证码，网上都资料很少，特别是支持中文验证码的更少，所以自己抽空了封装一下，免费分享给大家，希望能给大家提供思路和方法～

![img](bin/00001.png)
![img](bin/0002.png)
![img](bin/00003.png)
![img](bin/0005.png)
![img](bin/00006.png)

Feature 特色：支持中文验证，字体可选！！
-------
* 支持中文验证码
* 支持自定义词库、字库
* 支持自定义滤镜机制，通过滤镜来增加干扰，加大识别难度
* 当前的滤镜包括：
	* 支持干扰点
	* 支持干扰线
	* 支持其他模式的干扰
	* 更多模式，可实现imagefilter接口来扩展
* 支持自定义存储引擎，存储引擎可扩展
* 目前支持的存储引擎包括:
	* 内置(buildin)
	* memcache
	* redis (from https://gitee.com/shirdonl/captchas_with_go)
	* 如需扩展存储引擎，可实现StoreInterface接口

Useage
------
**安装**

	go get gitee.com/shirdonl/captchas_with_go

**Quick Start**

参考 [captcha_test.go](captcha_test.go)

参考 [examples/main.go](examples/main.go)


**文档地址**

[[captcha.go Wiki](https://github.com/shirdonl/captchas_with_go/wiki)]

LICENCE
-------
captchas_with_go[[GPL v3](https://opensource.org/licenses/GPL-3.0)]



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)