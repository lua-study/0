# 1 结构说明
HiBot架构主要使用C/S架构，其中HibotServer为服务器，Muqutte为消息服务器中间件，HiBotClient为运行在机器人上的客户端。主要实现了机器人任务的远程部署、监控、控制三大功能，机器人平台依赖于ROS。其架构如下图所示
![](imgs/arch.png)
下面是对这三个重要组成部分的说明
## 1.1 HiBotServer
Web服务器则使用Jersey框架[13]，Jersey是开源的RESTful 框架，基于RESTful的Web Service相比传统的web Service具有占用资源少、实现简单等优点。因此，HiBot提供RESTful API,使得各种设备接入HiBot进而进行机器人的操控变得更加简单。
## 1.2 Muqutte
HiBot选择轻量级的MQTT协议作为推送服务器与客户端之间的通信协议，推送服务器的中间代理（broker）则选用了开源推送代理服务器Moquette[12] (https://github.com/andsel/moquette) ，Moquette是基于事件驱动的服务器，支持websocket连接、权限验证、数据加密、服务质量保证等功能。我们在Moquette-0.8版本上进行定制，引入数据库对重要数据进行存储，加入客户端列表功能。
## 1.3 HiBotClient
HiBot客户端，主要负责接收并执行远程任务部署、监控、控制命令。
客户端构建在ROS之上，任务的执行依赖于ROS环境，客户端最核心的工作是接收执行来自服务器的相关命令。客户端主要包括消息解析模块、逻辑处理模块、数据请求和响应模块以及任务池模块。当服务器有消息推送到客户端时，首先消息解析模块解析该条消息并将其提交给逻辑处理模块中相应的功能模块，这些功能模块通过任务池中的任务进行操作来完成消息的执行工作，最终数据请求及分发模块会将执行结果数据上传至web服务器。
# 2 RESTFul接口
服务器接口采用RESTful格式，形式为 http://ip:port/HiBotServer/api/v1 + 具体请求操作
## 2.1 客户端操作
* 查看客户端列表
```
GET
http://ip:port/HiBotServer/api/v1/client/list
# 可选参数
# startPage  
# pageSize
# 例 http://localhost:8080/HiBotServer/api/v1/client/list?startPage=2&pageSize=10
```

* 查看客户端详情
```
GET
http://ip:port/HiBotServer/api/v1/client/id/ 
# id 客户端id
# 例 http://localhost:8080/HiBotServer/api/v1/client/id/1
```

## 2.2 任务/应用操作
* 任务详细信息
```
GET
http://ip:port/HiBotServer/api/v1/task/id/ 
# id 任务id
# 例 http://ip:port/HiBotServer/api/v1/task/id/1
```
* 任务推送(推拉结合)
```
GET
http://ip:port/HiBotServer/api/v1/task/publish/taskId/ /clientIds/ 
# taskId 任务id
# clientIds 客户端id，以逗号相隔
# 例 http://localhost:8080/HiBotServer/api/v1/task/publish/taskId/1/clientIds/1,2,3
```
* 任务推送（直接推送任务二进制包）
```
GET
http://ip:port/HiBotServer/api/v1/task/publishFile/clientId/ /filePath/ 
# clientId 客户端id
# filePath 文件路径
# 例 http://localhost:8080/HiBotServer/api/v1/task/publishFile/clientId/1/filePath/myros.zip
```
* 完成任务（由客户端调用）
```
GET
 http:///ip:port//HiBotServer/api/v1/task/finishTask/clientId/ 
 # clientId 客户端id
 #例 http://localhost:8080/HiBotServer/api/v1/task/finishTask/clientId/1
```

## 2.3 任务节点操作
* 向客户端发送上传任务节点信息请求-1
```
GET
http://ip:port/HiBotServer/api/v1/node/publish/clientIdMac/ 
# clientIdMac 客户端网卡/别名
# 例 http://127.0.0.1:8080/HiBotServer/api/v1/node/publish/clientIdMac/1
```

* 向客户端发送上传任务节点信息请求-2
```
GET
http://ip:port/HiBotServer/api/v1/node/publish/clientId/ 
# clientId 客户端id
# 例 http://127.0.0.1:8080/HiBotServer/api/v1/node/publish/clientId/1
```

* 查看客户端的任务node情况
```
GET
http://ip:port/HiBotServer/api/v1/node/clientId/ 
# clientId 客户端id
# 例 http://127.0.0.1:8080/HiBotServer/api/v1/node/clientId/1
```
* 向客户端上传节点信息（客户端接口）
```
POST
http://ip:port/HiBotServer/api/v1/node/uploadNodeList
# form：data
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)