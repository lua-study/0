# 系统编程

## Requirement

- PHP >= 5.4
- php socket 扩展开启

## Application structor

```
├── socket                      # socket通信实现
│   ├── tcp_server.php          # tcp server bash
│   ├── udp_server.php          # udp server bash 单播
│   ├── udp_client.php          # udp client bash 单播
│   ├── multicast_server.php    # udp server bash 多播
│   ├── multicast_client.php    # udp client bash 多播
│   ├── client.html             # tcp 网页交互实现
│   └── README.md
├── thread
│   ├── Thread.php              # Simple implementation of threading in PHP using pcntl
│   ├── demo.php                # thread 实现
│   ├── README.md          
├── logs
│   ├── websocket_debug.log     # websocket log
├── README.md
```

## 知识点预热

***什么是多播?***

#### 网络中存在3中传播形式，单播，广播，多播。

 * 1. 单播 : 就是1->1
 * 2. 广播 : 1->多(广播域内)
 * 3. 多播 : 1->组(一组ip)
 
***IP地址（224.0.0.0到239.255.255.255）标记为多播地址***

## 使用说明

### Socket Part

**进入到socket目录**

#### 1.TCP
* 启动server端

```bash
php tcp_server.php
```

* 启动客户端

```text
使用浏览器打开client.html（同时开启多个,效果更明显）
```

#### 2.UDP
* 启动server端

```bash
php multicast_server.php
```

* 启动客户端

```bash
php multicast_client.php
```

### Thread Part

**进入到thread目录**

* 启动
```bash
php demo.php    # 可观察效果
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)