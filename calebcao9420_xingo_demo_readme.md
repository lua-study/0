# xingo_demo xingo mmo大型多人在线游戏 带unity3d 客户端的服务器端demo
 **xingo框架需要切换到no reflect 分支 git checkout noreflect_veriosn**  
该demo实现了mmo游戏的基础模块aoi(基于兴趣范围的广播), 世界聊天， 空间管理等
xingo地址(https://git.oschina.net/viphxin/xingo)
客户端demo地址(https://git.oschina.net/viphxin/xingo_demo_unity3d)
截图展示： 
链接服务器： 
![alt text](unity3d/pictures/p1.png)
游戏主场景:  
![alt text](unity3d/pictures/p2.png)
测试步骤:
1) 开启服务器xingo_demo
./server (配置文件路径xingo_demo/conf/server.json)
2)开启机器人
./client_walk
3)在window上面跑unity pc客户端测试, pc包路径： xingo_demo/unity3d/bin/client.exe

消息对应关系如下 

|msgId            |client                 |server               |描述|
| -------- | -------- | -------- | -------- |
|1                  |-                    |SyncPid              |同步玩家本次登录的ID(用来标识玩家)|
|2                  |Talk                 |-                    |世界聊天|
|3                  |MovePackege          |-                    |移动|
|200                |-                    |BroadCast            |广播消息(Tp 1 世界聊天 2 坐标(出生点同步) 3 动作)|
|201                |-                    |SyncPid              |广播消息 掉线/aoi消失在视野|
|202                |-                    |SyncPlayers          |同步周围的人位置信息(包括自己)|

sudo protoc3 -I=/home/huangxin/workspace/go_fighting/src/xingo_demo/pb --go_out=/home/huangxin/workspace/go_fighting/src/xingo_demo/pb /home/huangxin/workspace/go_fighting/src/xingo_demo/pb/*.proto

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)