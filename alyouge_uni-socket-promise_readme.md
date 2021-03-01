### uni-socket-promise

#### 使用范围

仅支持uniapp

#### 安装
```
npm i @i5920/uni-socket-promise -S
```

#### 亮点
- promise异步获取结果
- 断线重连
- 心跳
- 断线消息队列
- debug
- 支持typescript

#### 使用说明
- App.vue
```
import UniSocketPromise from "@i5920/uni-socket-promise"
export default {
  globalData:{
    socket:null
  },
  onLaunch() {
    this.globalData.socket = new UniSocketPromise({
        url: "ws://127.0.0.1:8080"
    });
  },
  // 必须在这里调用initSocket方法
  onShow() {
    // 连接socket
    this.globalData.socket.initSocket();
    // 登录
    this.loginDemo();
  },
  methods:{
    // 发送socket消息
    loginDemo(){
      this.globalData.socket.send("login",{
          "username":"okcoder",
          "password":"666666"
      },{
        'token':"12345"
      }).then(_=>{
          console.warn(_)
      });
    },
    // 主动关闭socket
    closeSocket(){
      this.globalData.socket.close();
    }
  }
}
```

- 其它页面
```
getApp().globalData.socket.send("事件名称",{
    "username":"okcoder",
    "password":"666666"
}).then(_=>{
    console.warn(_)
});
```

- 后端格式要求

```
{
    event:"标识",   // 要求根据前端发送的数据进行组合加密 -> md5(事件名称字符串+参数字符串)
    data:"数据"
}
```

#### 方法说明
- initSocket(success, fail)
  - 初始化websocket
  - 判断websocket是否连接
  - 参数
    1. success 连接成功,如果是第一次则open可能还没有打开
    2. fail 连接失败


- send(event,data,extraData)
  - 发送socket消息
  - 参数
    1. event:string         事件名称
    2. data?:object         请求参数，必须json对象或者空对象{}或者不传值
    3. extraData?:object    同级参数


- close({code,reason,success,fail,complete})
  - 主动关闭socket
  - 参数(对象)
    1. code?: number
    2. reason?: string
    3. success?: Function
    4. fail?: Function
    5. complete?: Function

- 如果发送其它格式的消息直接使用`uni.sendSocketMessage()`

#### 参数说明
| 参数 | 类型 | 必填 | 默认值 | 说明 |
| ---- | ---- | ---- | ---- |---- |
| url | string | 是 |-| websocket地址,如`ws://127.0.0.1:8080` |
|debug| boolean|否| 开发环境自动打开 | 调试开关 |
|header| object|否| - | 参考https://uniapp.dcloud.io/api/request/websocket?id=connectsocket|
|method| string|否| - | 参考https://uniapp.dcloud.io/api/request/websocket?id=connectsocket|
|protocols| string[]|否| - | 参考https://uniapp.dcloud.io/api/request/websocket?id=connectsocket|
|isReconnect|boolean|否|true|是否断线重连|
|reConnectTime|number|否|3000|断线重连间隔时间,毫秒|
|isHeartData|boolean|否|true|是否发送心跳|
|heartTime|number|否|3000|心跳包间隔事件,毫秒|
|onSocketOpen|Function|否|null|监听到socket打开事件|
|onSocketClose|Function|否|null|监听到socket被关闭事件|
|onSocketError|Function|否|null|监听到socket出错事件|
|onSendMessageBefore|Function|否|null|发送消息前事件,必须返回{event:"",data:''},因为要继续下面的逻辑|
|onSendMessageAfter|Function|否|null|发送消息后事件|
|onSocketMessageBefore|Function|否|null|收到消息前事件,如果返回true则继续逻辑,返回false则终止逻辑,千万注意如果要继续逻辑必须返回true|
|onSocketMessageAfter|Function|否|null|收到消息后事件,返回新数据被promise.resove接收|

#### 赞助二维码

![](https://gitee.com/uploads/images/2018/0623/112959_9f84f1f7_696921.png "3.png")
![](https://gitee.com/uploads/images/2018/0623/113008_0014aa83_696921.jpeg "4.jpg")

#### 更新日志
- v2.0.11

  1. [优化]send方法 data参数必须是json对象或者空对象{}或者不传值,默认发送空字符,方便后端解析与md5加密统一

- v2.0.9

  1. [bug]utility插件不给力,改为md5-ts

- v2.0.8

  1. [bug]Pool使用完后立马删除

- v2.0.7

  1. [bug]send方法添加同级请求参数

- v2.0.6

  1. [优化]send方法添加同级请求参数

- v2.0.5

  1. [优化]onSocketMessageBefore如果返回true可继续逻辑,返回false则终止逻辑

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)