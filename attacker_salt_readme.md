# 介绍

saltstack 原理
Saltstack 基于 C/S 架构，服务端 master 和客户端 minions。minion 与 master 之间通过 ZeroMQ 消息队列通信，使用了 ZeroMq 的 `发布`-`订阅模式` 消息服务。


### Master端口
master 监听 `4505` 和` 4506` 端口:

- 4505 对应的是 ZMQ 的 PUB system，用来发送消息
- 4506 对应的是 ZMQ 的 REP system，是来接受消息

### minion端配置
配置master 地址，需要推送自己的`pub key`



----

## 服务端/客户端部署

- [http://opsbase.cn/detail/89.html ](http://opsbase.cn/detail/89.html "部署实践") 

## 日常操作
- [http://opsbase.cn/detail/70.html ](http://opsbase.cn/detail/70.html "日常操作")   

## 基于api的web开发

- [http://opsbase.cn/detail/87.html ](http://opsbase.cn/detail/87.html "salt-api")


### 快速初始化部署
```
cat /srv/salt/install_and_etc/salt-ssh/roster_nopass
# 配置主机列表

cd   /srv/salt/install_and_etc/salt-ssh/
salt-ssh --roster-file=roster_nopass -i  "*"  --passwd 123456  state.highstate
# 批量初始化roster列表中主机
```





 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)