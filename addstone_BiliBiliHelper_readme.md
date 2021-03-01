
   

[![codebeat][1]][2] [![Downloads][3]][4] [![Version][5]][6]
[![License][7]][8]

[1]: https://codebeat.co/badges/4171ff04-5cff-4bed-8213-b82944e130e6 "Codebeat badge"
[2]: https://codebeat.co/projects/github-com-thewanderingcoel-bilibilihelper-master "Codebeat"
[3]: https://img.shields.io/github/downloads/TheWanderingCoel/BiliBiliHelper/total.svg "All releases badge"
[4]: https://github.com/TheWanderingCoel/BiliBiliHelper/releases/ "All releases number"
[5]: https://img.shields.io/badge/version-v0.0.6-green.svg?longCache=true
[6]: https://github.com/TheWanderingCoel/BiliBiliHelper
[7]: https://img.shields.io/badge/license-GPL%20V3-blue.svg?longCache=true
[8]: https://github.com/TheWanderingCoel/BiliBiliHelper/blob/master/LICENSE

| OS | Windows | macOS | Linux |
| --- | --- | --- | --- |
| Build Status | [![Build Status Windows](http://badges.herokuapp.com/travis.com/TheWanderingCoel/BiliBiliHelper?style=flat-square&env=BADGE=windows&label=Windows&branch=master)](https://travis-ci.com/TheWanderingCoel/BiliBiliHelper) | [![Build Status macOS](http://badges.herokuapp.com/travis.com/TheWanderingCoel/BiliBiliHelper?style=flat-square&env=BADGE=osx&label=macOS&branch=master)](https://travis-ci.com/TheWanderingCoel/BiliBiliHelper) | [![Build Status Linux](http://badges.herokuapp.com/travis.com/TheWanderingCoel/BiliBiliHelper?style=flat-square&env=BADGE=linux&label=Linux&branch=master)](https://travis-ci.com/TheWanderingCoel/BiliBiliHelper) |

# BiliBiliHelper
B 站直播实用脚本Python版本

## 功能组件

|plugin              |version  |description   |
|--------------------|---------|--------------|
|AsyncioCurl         |19.03.07 |异步的网络请求组件|
|Auth                |19.03.07 |帐号登录组件    |
|Capsule             |19.03.07 |扭蛋机(普通)    |
|Console             |19.03.07 |控制台组件      |
|Coin2Silver         |19.03.07 |硬币换银瓜子组件 |
|Curl                |19.03.17 |非异步的网络请求组件|
|Danmu               |19.03.07 |弹幕监听组件    |
|DailyBag            |19.03.07 |每日礼包领取    |
|Group               |19.03.07 |应援团签到      |
|Guard_Raffle_Handler|19.03.07 |大航海抽奖模块  |
|Heart               |19.04.06 |双端直播间心跳  |
|Silver2Coin         |19.03.07 |银瓜子换硬币    |
|SilverBox           |19.04.11 |免费宝箱领取    |
|Storm_Raffle_Handler|19.03.07 |节奏风暴抽奖模块|
|Task                |19.04.06 |每日任务       |
|Tv_Raffle_Handler   |19.03.31 |小电视抽奖模块 |
|Monitor_Server      |19.12.24 |舰长服务器连接模块|

## 未完成功能
|待续|
|-------|
| ~~节奏风暴抽奖卡死修复~~ |
| ~~代理设置~~ |
| ~~舰长监听服务器~~ |
| 抽奖结果图表可视化 |
| RESTFUL API |
| 动态抽奖 |


## 环境依赖
|Requirement|
|-------|
|Python 3.6+|
|aiohttp  |
|aiosocksy |
|  rsa    |
|requests[socks] |
|configobj|
| flask   |
| tailer  |

通常使用 `pip` 工具安装依赖。


## 使用指南

### 一.源码运行
 1. 下载（克隆）项目代码，初始化项目
```
$ git clone https://github.com/TheWanderingCoel/BiliBiliHelper.git
$ cd BiliBiliHelper
```
 2. 使用 pip 工具进行安装
```
$ pip install -r requirements.txt
```
 3. 按照[说明](https://github.com/TheWanderingCoel/BiliBiliHelper/blob/master/Doc/Account.md)修改配置文件 `Account.conf`，只需填写帐号密码即可
 4. 运行
```
$ python main.py
```

   

### 二.二进制程序运行
1.下载[编译好的程序](https://github.com/TheWanderingCoel/BiliBiliHelper/releases)  
2.按照[说明](https://github.com/TheWanderingCoel/BiliBiliHelper/blob/master/Doc/Account.md)修改配置文件 `Account.conf`，只需填写帐号密码即可  
3.双击**BiliBiliHelper.exe**(Windows)或者**BiliBiliHelper**(macOS,Linux)

### 三.使用Docker运行

1.在命令行里输入
```
docker run -it --rm -e BiliBili_USER=你的B站账户名 -e BILIBILI_PASSWORD=你的B站密码 thewanderingcoel/bilibilihelper

-itd 后台运行
```



## 部署指南
如果你将 BiliBiliHelper 部署到线上服务器时，则需要配置一个进程监控器来监测 `python main.py` 命令，在它意外退出时自动重启。

通常可以使用以下的方式
 - systemd (推荐)
 - Supervisor
 - screen
 - nohup

## systemd 脚本
```
# /usr/lib/systemd/system/bilibili.service

[Unit]
Description=BiliBiliHelper Manager
Documentation=https://github.com/TheWanderingCoel/BiliBiliHelper
After=network.target

[Service]
ExecStart=/usr/local/bin/python3 /root/BiliBiliHelper/main.py
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

## Supervisor 配置
```
[program:bilibili]
process_name=%(program_name)s
command=python /path/to/your/BiliBiliHelper/main.py
autostart=true
autorestart=true
redirect_stderr=true
```

## 直播间 ID 问题
config 文件中有个 `ROOM_ID` 配置，填写此项可以清空临过期礼物给指定直播间。

通常可以在直播间页面的 url 获取到它
```
http://live.bilibili.com/23058
```

所有直播间号码小于 1000 的直播间为短号，该脚本在每次启动会自动修正，无需关心，


## 感谢
 - BilibiliHelper(php) https://github.com/metowolf/BilibiliHelper
 - blivedm             https://github.com/yjqiang/blivedm
 - bilibili-live-tools https://github.com/yjqiang/bilibili-live-tools
 - bili2.0             https://github.com/yjqiang/bili2.0
 - bilibili-raffle     https://github.com/Billyzou0741326/bilibili-raffle
 - bilibili-live-monitor-js https://github.com/Billyzou0741326/bilibili-live-monitor-js



## License 许可证

本项目基于 GPL V3 协议发布。

本项目的所有代码文件、配置项，除另有说明外，均基于上述介绍的协议发布，具体请看分支下的 LICENSE。

此处的文字仅用于说明，条款以 LICENSE 文件中的内容为准。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)