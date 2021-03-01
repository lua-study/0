# goproxy

golang tcp反向代理程序

## 如何启动

```shell
# 在本工程根目录下
go run services/main.go

# 或者编译成二进制文件
cd services
go build -o ../bin/goproxy
../bin/goproxy

# 您还可以指定要启动的配置文件地址
# 系统会自动在当前目录(".")，系统环境变量(PROXY_CONFIG_PATH)，以及本地工程目录文件("$GOPATH/src/github.com/wangff15386/goproxy/config")下查找proxy.json文件
export PROXY_CONFIG_PATH="/home/wangff/go/src/github.com/wangff15386/goproxy/config"
./goproxy
```

## HTTP TEST

```go
/*
	======================= http tests =======================
	curl -X POST "http://localhost:8080/worker-keepalive.do?group=8081&server=localhost:11111"
	curl "http://localhost:8080/worker-list.do?group=8081"
	curl -X POST "http://localhost:8080/group-open.do?group=8081"
	curl -X POST "http://localhost:8080/group-close.do?group=8081"
*/
```

# 需求描述

## 0 概述

使用golang开发tcp反向代理程序 实现ha(热备)/lb(负载均衡)的效果  
console app即可，无需gui界面  
提交go源码和可执行文件  


## 1 基本要求

面向对象设计  
代码规范 注释充分 逻辑清晰 可读性好  
长时运行无内存泄露  
不使用非开源或版权受限的第三方库代码  


## 2 系统配置

使用json文件配置系统参数  


## 3 tcp端口转发

根据配置文件监听tcp端口  
当有client连接进来时 创建TCPProxySession对象  
所有TCPProxySession使用ProxySessionService进行状态监测和生命周期管理  
根据lb策略连接后台server  
使用独立goroutine 读client连接并写入server连接  
使用独立goroutine 读server连接并写入client  
client/server断开时 注销TCPProxySession并释放所有资源  
长时间cleint/server无读无写时 注销TCPProxySession  




## 4 lb策略

支持ha Round-Robin ip_hash 多种LB策略，可根据系统配置切换  
ha - 热备，总是把所有请求转发到在线服务器列表的首台服务器，直至其掉线移除  
round-robin - 循环，每一次把来自用户的请求轮流分配给所有在线服务器，从1开始，直到N(内部服务器个数)，然后重新开始循环。  
ip_hash - 根据客户端ip计算hash code，然后取在线服务器数量的模得到N，然后转发到第N台服务器  
抽象IBalancePolicy接口，并使用工厂模式创建实例  




## 5 http接口

import "net/http/pprof"以方便内存诊断  
worker-keepalive.do?group= &server= :  接收服务器注册和心跳 更新在线服务器列表  
worker-list.do?group=  查看在线服务器列表  
group-open.do?group=  打开端口监听  
group-close.do?group=  关闭端口监听  
管理接口的输入使用get 返回使用json: { "ok" : true | false, "msg" : "错误提示", ... }  
所有管理接口的参数持久化到系统配置文件 下次重启直接生效  


## 6 日志

所有client/server连接和断开事件写日志  
所有http请求和输出有日志  
每隔5秒定时打印日志：在线client，在线server  


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)