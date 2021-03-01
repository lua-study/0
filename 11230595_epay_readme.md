# epay

[![Build Status](https://travis-ci.org/dianbaer/epay.svg?branch=master)](https://travis-ci.org/dianbaer/epay)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/dd6af1d7af8940b284a0e5b15846ecfb)](https://www.codacy.com/app/232365732/epay?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=dianbaer/epay&amp;utm_campaign=Badge_Grade)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

# epay是一个标准的支付平台，作为支付应用APP、第三方支付平台、身份系统三方对接的标准中间服务器。提供注册应用APP，创建用户订单，用户支付跳转，用户支付结果跳转与通知等功能。开发者只需关心1个创建订单接口、1个支付跳转url、1个支付结果回跳url、1个支付结果通知url即可。

	
	
## 流程图1（注册app流程图）

![流程图1](./epay1.png "epay1.png")

## 流程图2（支付流程图）

![流程图2](./epay2.png "epay2.png")


## 项目目录结构：


### EpayServer（目录结构 4144行）

	|--src.main.java（服务器代码）
		|--EpayServer.properties---------------配置文件（需要修改）
		|--generatorConfig.xml--------------------mybatis自动生成配置文件（重新生成时，需要修改）
		|--org.epay
			|--action.IdentityAction.java---------从第三方身份系统获取数据（对接非默认身份系统时，需要修改）
			|--server.Expand.java-------------------扩展启动类
			|--plugin.PaginationPlugin.java-------mybatis自动生成配置文件启动类
			|--http
				|--AlipayNotifyServlet.java-------支付宝异步通知接收类
				|--AlipayReturnServlet.java-------支付宝同步通知接收类
			
		|--com.alipay-----------------------------支付宝调用包（整合了MD5与RSA，通过配置可选）
	|--protobuf（消息包生成工具）
	|--WebContent
		|--*.html（请求接口测试）
		|--js（请求接口测试）
		|--html（请求接口测试）


## 打版本：在项目根目录下，执行

	ant

	
## 如何使用epay


### 1、配置并部署epay





 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)