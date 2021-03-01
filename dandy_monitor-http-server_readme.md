monitor-http-server
===================

Simple script to monitor if servers are responding (status 200) or not.

## Screenshot
 ![Sample output](https://raw.github.com/edouard-lopez/monitor-http-server/master/http-monitor-server-screenshot.png)

## Dependencies

You need to have a **mail server** configured to be able to send notification.

* `mail` command to send notification.
* [stylerc](https://github.com/edouard-lopez/stylerc): bash output style ;
* [toolboxrc](https://github.com/edouard-lopez/toolboxrc): some stupid utilities ;

## Install

The project use two submodules, the instructions below cover an *out of the box* installation process:

```
git clone git@github.com:edouard-lopez/monitor-http-server.git
cd monitor-http-server
git submodule init && git submodule update # install the submodules
```

## Usage

First you need to edit the file `monitor-list.txt` and add some servers URLs (using their [FQDN](https://en.wikipedia.org/wiki/Fully_qualified_domain_name)).

Note that lines starting with a `#` (dash) are ignored.

	# ignored hosts
	# http://wont-be.tested.com/
	# test
	http://my.website.com/

Then you are good to go and run your first test

	bash ./monitor-servers.sh me@host.com ./monitor-list-default.txt
	
##微信报警

当检测到非200的请求时，会触发邮件和微信报警。微信报警需要自己维护weixin-send.sh、和weixin-heart.sh这两个文件。  

这两个shell文件其实就是两条curl命令，send文件用来发送微信消息，heart文件用于向腾讯服务器发送心跳，否则时间久了，会踢掉改sid。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)