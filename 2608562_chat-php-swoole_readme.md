# chat-php-swoole

#### 介绍
这是用php swoole 原生写的 在线聊天

#### 软件架构
--app
--bin
--client
--config
--framework
--log
--server
--src
--test


#### 安装教程

1. xxxx
2. xxxx
3. xxxx

#### 使用说明

1. xxxx
2. xxxx
3. xxxx


# 查看进程
$ pstree -ap|grep swoole_tcp_server

********************** swoole 的实现 ************************

# Reactor(nginx)主进程内的回调函数：
onStart
onShutdown

# Worker(php-fpm)进程内的回调函数
onWorkerStart
onWorkerStop
onConnect
onClose
onReceive
onFinish

# TaskWorker进程内的回调函数
onTask
onWorkerStart

# 管理进程内的回调函数
onManagerStart
onManagerStop

# 备注：
底层会为Worker进程、TaskWorker进程分配一个唯一的ID
不同的Worker和TaskWorker进程之间可以通过sendMessage接口进行通信

*************************************************************

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)