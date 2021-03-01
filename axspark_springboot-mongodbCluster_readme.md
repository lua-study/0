#springboot-mongodbCluster

项目主框架采用springboot，介绍mongodb集群安装及和spring-boot结合使用的方法！

##mongodb 集群搭建

### 虚拟机安装

```
安装一个虚拟机 ，虚拟机安装非本文范畴，可查阅相关资料。
本文虚拟机IP设置为：10.16.70.133。此处可根据自己网络环境自行设置。
在安装mongodb之前需要先将虚拟机防火墙关闭，并配置好网络。
需保证虚拟机可连接外网，以方便执行wget、yum等安装相关软件。
```

### 安装mongodb

```
　　wget https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-amazon-3.2.10.tgz
    tar xvzf mongodb-linux-x86_64-amazon-3.2.10.tgz
    mv mongodb-linux-x86_64-amazon-3.2.10 mongodb
```
* 如果wget命令执行失败，或者较慢，则手动从https://www.mongodb.com/download-center下载相应版本

### 配置

```
cd mongodb
mkdir -p data/master
mkdir -p data/slaver
mkdir -p data/arbiter
mkdir log
# 三个目录分别对应主，备，仲裁节点

```
* 在mongodb目录下添加三个文件master.conf、slaver.conf、arbiter.conf

```
#master.conf
dbpath=data/master
logpath=log/master.log
pidfilepath=master.pid
directoryperdb=true
logappend=true
replSet=testrs
bind_ip=10.16.70.133
port=27017
oplogSize=10000
fork=true
noprealloc=true

#slaver.conf
dbpath=data/slaver
logpath=log/slaver.log
pidfilepath=slaver.pid
directoryperdb=true
logappend=true
replSet=testrs
bind_ip=10.16.70.133
port=27018
oplogSize=10000
fork=true
noprealloc=true

#arbiter.conf
dbpath=data/arbiter
logpath=log/arbiter.log
pidfilepath=arbiter.pid
directoryperdb=true
logappend=true
replSet=testrs
bind_ip=10.16.70.133
port=27019
oplogSize=10000
fork=true
noprealloc=true
```

### 启动mongodb

```
./bin/mongod -f master.conf
./bin/mongod -f slaver.conf
./bin/mongod -f arbiter.conf
```

### 配置主，备，仲裁节点

```
# 可以通过客户端连接mongodb，也可以直接在三个节点中选择一个连接mongodb。
./bin/mongo 10.16.70.133:27017   #ip和port是某个节点的地址
> use admin
> cfg={ _id:"testrs", members:[ {_id:0,host:'10.16.70.133:27017',priority:2}, {_id:1,host:'10.16.70.133:27018',priority:1},
{_id:2,host:'10.16.70.133:27019',arbiterOnly:true}] };
> rs.initiate(cfg)             #使配置生效，如下提示
```

* 执行rs.status()命令会看到如下信息：

```
{
	"set" : "testrs",
	"date" : ISODate("2016-10-25T10:13:00Z"),
	"myState" : 1,
	"members" : [
		{
			"_id" : 0,
			"name" : "10.16.70.133:27017",
			"health" : 1,
			"state" : 1,
			"stateStr" : "PRIMARY",
			"uptime" : 50228,
			"optime" : Timestamp(1477340235, 1),
			"optimeDate" : ISODate("2016-10-24T20:17:15Z"),
			"self" : true
		},
		{
			"_id" : 1,
			"name" : "10.16.70.133:27018",
			"health" : 1,
			"state" : 3,
			"stateStr" : "RECOVERING",
			"uptime" : 50137,
			"optime" : Timestamp(0, 0),
			"optimeDate" : ISODate("1970-01-01T00:00:00Z"),
			"lastHeartbeat" : ISODate("2016-10-25T10:13:00Z"),
			"lastHeartbeatRecv" : ISODate("2016-10-25T10:12:58Z"),
			"pingMs" : 0,
			"lastHeartbeatMessage" : "syncThread: 14031 Can't take a write lock while out of disk space"
		},
		{
			"_id" : 2,
			"name" : "10.16.70.133:27019",
			"health" : 1,
			"state" : 7,
			"stateStr" : "ARBITER",
			"uptime" : 50137,
			"lastHeartbeat" : ISODate("2016-10-25T10:12:59Z"),
			"lastHeartbeatRecv" : ISODate("2016-10-25T10:12:58Z"),
			"pingMs" : 0
		}
	],
	"ok" : 1
}

```

* 集群搭建完成。

### 期望

欢迎提出更好的意见，帮助完善我们的项目，以督促我们前行！

### 版权

[Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0)

### 捐赠

![捐赠 springboot-mongodbCluster](http://git.oschina.net/uploads/images/2016/1023/084255_833edeac_364262.png "支持一下springboot-mongodbCluster")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)