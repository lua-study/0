LogMaster4Net  [![Build Status](https://travis-ci.org/kerryjiang/LogMaster4Net.svg?branch=master)](https://travis-ci.org/kerryjiang/LogMaster4Net)
=============

**LogMaster4Net** is a central log server which can receive log messages of your other applications and organize them as your demand. It can help you to manage your all applications log messages in a central place. So if you have lots of different applications running and most of them have their own logging, this project will be pretty useful for you.

**LogMaster4Net** actually is a UDP server which is base on **SuperSocket**


1. Server Configuration

		 
	     

2. Server Logging Configuration

		\Config\log4net.config: the logging confuguration of the server self;
		\Config\log4net.[LogAppName].Config : the logging configuration for your application whose name is [LogAppName]};

3. Application Setting
	- Set LogAppName

			log4net.GlobalContext.Properties["LogAppName"] = "MyTool1";

	- Logging Configuration
	
			 
		       
		       
		       
		           
		       
		     



*The logging framework used by the log server and applications must be log4net. LogMaster4Net will support other logging frameworks later.*


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)