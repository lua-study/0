# 微信工具集
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/gemgin/WeChatTools/pulls)
[![GitHub stars](https://img.shields.io/github/stars/gemgin/WeChatTools.svg?style=social&label=Stars)](https://github.com/gemgin/WeChatTools)
[![GitHub forks](https://img.shields.io/github/forks/gemgin/WeChatTools.svg?style=social&label=Fork)](https://github.com/gemgin/WeChatTools)

交流QQ群：41977413

## 项目介绍
> 微信域名网址检测
- 微信域名检测("已停止访问该网页","网页包含诱导分享、诱导关注内容，被多人投诉，为维护绿色上网环境，已停止访问")
- 见pro/wxUrlCheck.ashx.cs

> 域名切换
- 微信公众号网页域名随机生成跳转，配合微信域名检测功能，自动切换域名，保证活动正常访问
- 见pro/urlTransfer.ashx.cs

> 微信公众号图片中转
- 微信公众号文章里面的图片不能嵌套其它页面进行访问，做了微信做了防盗链处理，所以我们做了一个中转。
- 见 pro/hdShowImg.ashx.cs

## 使用
- 域名检测试用接口 [http://wx.rrbay.com/pro/wxUrlCheck.ashx?url=http://www.teu7.cn](http://wx.rrbay.com/pro/wxUrlCheck.ashx?url=http://www.teu7.cn "域名检测试用接口")
```
 {"State":true, "Code","101","Data":"teu7.cn",  "Msg":"屏蔽"}
 {"State":true, "Code","102","Data":"rrbay.com","Msg":"正常"}
 {"State":false,"Code","001","Data":"rrbay.com","Msg":"非法访问，访问被拒绝,进qq群交流:41977413"}
 {"State":false,"Code","002","Data":"rrbay.com","Msg":"歇一歇,访问太快了,进qq群交流:41977413"}
 {"State":false,"Code","003","Data":"rrbay.com","Msg":"服务暂停,请联系管理员!"}
```
- 域名检测界面：http://wx.rrbay.com/
 
### 顶尖技术，铸就稳定服务

微信域名检测接口采用基于系统服务开发，接口快速、稳定。

### 官方接口，实时结果

    微信域名检测采用微信官方接口，实时返回查询结果，准确率100%，API接口响应速度快，平均检测时间只需0.2秒

### 在线自助查询/API集成查询

    微信域名检测接口支持多域名不限次数提交查询，web端在线查询返回结果，无需安装插件或客户端。支持API查询、支持集成到自由系统或第三方系统

### 为用户定制的域名自动监测系统

    为了方便用户，可以为用户开发了一套域名自动检测自动切换系统，保证微信公众号活动正常进行。

> 积攒star=18000，微信域名检测核心代码和原理将在码云和github完全公开，如果你需要请star

## 2018-01-29 微信域名检测系统升级说明
- 数据库mongodb连接安全问题（部署不当，会造成重大安全漏洞）
- 微信域名检测key授权与微信域名检测服务分离，方便部署和后期运营
- 优化微信域名检测服务接口
- 检测入口分布式部署以及负载均衡

## 2018-08-20 微信域名防封系统升级说明
- 防封系统接收中转分离
- 中转统一采用redis
- 优化实时检测自动更换逻辑--采用每个小时检测某分钟检测
 
## 2018-08-23 微信域名检测系统升级说明
- 微信域名检测底层服务升级改造
- 采集cookie与检测服务分离
- redis与mongodb分离

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)