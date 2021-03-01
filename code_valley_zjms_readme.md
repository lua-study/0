# zj
Ultimate jms(jump server) written in C and raft.

## 亮点
- 业务流程：        
    - 以DevGroup(开发组)为基本单位进行授权管理，免去了繁杂的单台申请流程；
    - 使用投票制管理DevGroup成员变动，即：加入或删除成员时，只需要半数以上成员投票通过，而不必每次通过超管审批授权，实现了DevGroup团队内部的“灵活自管理”；

- 可用性：        
    - 中枢系统采用基于raft算法开发的分布式架构，避免了单点故障，提供高可用服务；

- 性能：        
    - 分布式多节点，可承载更多的客户端连接，提供更强、更流畅的服务能力；
    - zj服务端采用单进程直接跳转模式，较之现存的跳板机，每个连接节省一个进程的开销；
    - 已获授权的DevGroup及主机信息，缓存于客户端本地，而非每次无谓的访问服务端，客户端体验得到提升；

- 功能：        
    - zj服务端采用的单进程直接跳转模式，是原子性的，由此杜绝了过往常见的多进程不协调导致的花屏、终端尺寸失灵、僵死进程残留等影响体验及性能的问题；
    - 客户端与最终服务器之间，可进行方便的双向文件传输；
    - 支持高效的批量管理功能（类似于ansible功能）；

- 安全性：        
    - 传统的跳板机必须允许用户在服务端停留，以选择要登陆的主机，且此服务器通常拥有最高权限连通大量的最终服务器，由此埋下了巨大的安全隐患，一旦此中心服务器被攻破，即意味着大量最终服务器的完全沦陷；
    - zj服务端采用的单进程直接跳转模式，提供了更强的安全保障，因为提供跳转连接功能的节点，本身无须拥有连接任何最终服务器的权限，而且由于客户端是在本地选择待连接的目标机，因此跳转节点完全不需要提供客户端中途停留的机会；

- 开发稳健性：        
    - 测试代码量 > N * 正文代码量；
    - 极少的依赖，极简的代码(Less code, More security!)。

## 宏观架构图
- register 服务于所有从前端页面上发起的请求    
- raft 服务于所有 SSH 终端的登陆请求    
![](demo/宏观架构图.jpeg)

## 前端模块设计示例
![](demo/前端模块设计示例.png)

## TODO
- 完善审计功能    
    
# API wiki
#### 字段定义：
|方向|名称|类型|备注|
|:-:|:-:|:-:|:-:|
|req-->|params|any||
| |uname|string|user name|
| |gname|string|group name|
| |hname|string|host name|
| |rid|int|rpc ID|
| |uid|int|user ID|
| |xuid|int|user(initiator) ID|
| |gid|int|group ID|
| |hid|int|host ID|
| |vid|string|vendor ID|
| |aid|string|asset ID|
| |tid|int|transaction ID|
| |ttype|string|"user-add"/"user-del"/"host-add"/"host-del"|
| |pid|int|page ID|
| |psiz|int|page siz(how many items per page)|

## {1.1} 创建用户
> http://[ADDR]/v1/user/create       
> 系统协同接口，与其它系统同步账号数据：批量添加用户元信息
```
req-->
[
    {"params": {"uname": "张三"}, "rid": 1},
    {"params": {"uname": "李四"}, "rid": 2},
    {"params": {"uname": "王五"}, "rid": 3}
]

  http://[ADDR]/v1/user/destroy       
> 系统协同接口，与其它系统同步账号数据：批量清理用户元信息、开发组关联、公钥等
```
req-->
[
    {"params": {"uid": 1}, "rid": 1},
    {"params": {"uid": 2}, "rid": 2},
    {"params": {"uid": 9}, "rid": 3}
]

  http://[ADDR]/v1/user/pubkey/update       
> 用户 SSH 连接凭证，会覆盖已有信息
```
req-->
[
    {"params": {"xuid": 1, "pubkey": "..."}, "rid": 1},
    {"params": {"xuid": 2, "pubkey": "..."}, "rid": 2}
]

  http://[ADDR]/v1/user/groups_and_hosts    
```
req-->
{"params": {"xuid": 1}, "rid": 1}

  http://[ADDR]/v1/user/group/join        
> 半数以上成员投票赞成且无否决票，或超管审批；空开发组直接通过，无需审批
```
req-->
[
    {"params": {"xuid": 1, "gid": 1}, "rid": 1},
    {"params": {"xuid": 2, "gid": 1}, "rid": 2}
]

  http://[ADDR]/v1/user/group/quit    
> 即时生效；用户对主机的引用计数为0时，该主机上的用户公钥将被清除；成员数为0的开发组，将被自动删除
```
req-->
[
    {"params": {"xuid": 1, "gid": 1}, "rid": 1},
    {"params": {"xuid": 1, "gid": 2}, "rid": 2}
]

  http://[ADDR]/v1/group/create       
> 不允许与现有开发组重名
```
req-->
[
    {"params": {"xuid": 1, "gname": "dev-01"}, "rid": 1},
    {"params": {"xuid": 1, "gname": "dev-02"}, "rid": 2}
]

  http://[ADDR]/v1/group/member/del    
> 半数以上成员投票赞成且无否决票，或超管审批；用户对主机的引用计数为0时，该主机上的用户公钥将被清除
```
req-->
[
    {"params": {"xuid": 1, "gid": 1, "uid": 1}, "rid": 1},
    {"params": {"xuid": 1, "gid": 1, "uid": 2}, "rid": 2}
]

  http://[ADDR]/v1/group/host/add    
> 所有拥有此台主机的开发组（批量操作会自动分割为多个单台主机的投票请求）的半数以上成员投票且无否决票，或超管审批
```
req-->
[
    {"params": {"xuid": 1, "gid": 1, "hid": 1}, "rid": 1},
    {"params": {"xuid": 1, "gid": 1, "hid": 2}, "rid": 2}
]

  http://[ADDR]/v1/group/host/del    
> 所有拥有此台主机的开发组（批量操作会自动分割为多个单台主机的投票请求）的半数以上成员投票赞成且无否决票，或超管审批
```
req-->
[
    {"params": {"xuid": 1, "gid": 1, "hid": 1}, "rid": 1},
    {"params": {"xuid": 1, "gid": 1, "hid": 2}, "rid": 2}
]

  http://[ADDR]/v1/group/all    
> 从中选择待加入的开发组
```
req-->
{"params": {"pid": 1, "psiz": 20}, "rid": 1}

  http://[ADDR]/v1/group/info    
> 成员列表、主机列表等
```
req-->
{"params": {"gid": 1}, "rid": 1}

  http://[ADDR]/v1/host/all    
> 资产所属平台、资产ID、主机ID、主机名称、网络地址、网络类型、开发组列表等
```
req-->
{"params": {"pid": 1, "psiz": 20}, "rid": 1}

  http://[ADDR]/v1/trans/active          
> 事务ID、事务类别、关联组的名称、发起时间、发起人、操作目标、额外信息
```
req-->
{"params": {"xuid": 1, "pid": 1, "psiz": 20}, "rid": 1}

  http://[ADDR]/v1/trans/agree    
> 不可撤销
```
req-->
[
    {"params": {"xuid": 1, "tid": 1}, "rid": 1},
    {"params": {"xuid": 1, "tid": 2}, "rid": 2}
]

  http://[ADDR]/v1/trans/reject    
> 不可撤销
```
req-->
[
    {"params": {"xuid": 1, "tid": 1}, "rid": 1},
    {"params": {"xuid": 1, "tid": 2}, "rid": 2}
]

  http://[ADDR]/v1/trans/ignore      
> 不可撤销
```
req-->
[
    {"params": {"xuid": 1, "tid": 1}, "rid": 1},
    {"params": {"xuid": 1, "tid": 2}, "rid": 2}
]

<--resp
[
    {"result": "", "rid": 1},
    {"result": "", "rid": 2}
]
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)