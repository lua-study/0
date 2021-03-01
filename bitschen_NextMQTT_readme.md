# Next-MQTT

基于MQTT的封装库，实现点对点消息通讯:

- `Req-Rep`的**请求-响应**模式;
- `Pub-Sub`的**发布-订阅模式**

## 一、Topic规则

NextMQTT在Topic设计上，已经区分不同服务之间和不同客户端之间的消息路由。基于MQTT的Topic分层设计，NextMQTT设计的Topic各个分层类目的规则说明如下：

> /${string:domain}/${string:target-node-id}/${string:pattern-type}/${long:request-id}/${string:sender-node-id}/${string:tag}

- `domain` String类型值，消息目标服务名称。
- `target-node-id` String类型值，消息目标的客户端节点ID。
- `pattern-type` String类型值，模式类型。目前有以下三个模式值：
    * `requests` 请求消息Request的模式值；
    * `replies` 响应消息Reply的模式值；
    * `pubsub` 通知类消息PubSub的模式值；
- `request-id` Long类型值，在Request和Reply模式中，request-id是一个基于时间变化的Long类型ID。在PubSub模式中为固定值，默认为0。
- `sender-node-id` String类型值，发送消息来源的终端客户端节点ID；
- `tag` String类型值，用于扩展：可以实现基于Topic实现一级消息路由，无须在消息payload层次增加路由标识。

## 二、消息模式

NextMQTT在Topic设计上区分每个终端的域，由`domain`和`node-id`组成。

Topic规则上的`/${domain}/${node-id}`路径是发送消息给指定终端的重要规则。由此，NextMQTT内置实现以下二种模式。

### 2.1 Req-Rep 点对点通讯模式

`Req-Rep模式`类似HTTP协议，由一个终端作为客户端，另一终端作为服务端，实现`请求-响应`模式。
在Topic规则上，使用`${string:pattern-type}`段来区分Request和Reply消息。

#### 客户端发送消息过程

> 客户端向服务端发送消息，是通过作为客户端一方，向指定`node-id`的服务端发送request消息。
> 而作为服务端一方，监听发送给自己的request消息。

**第一步：服务端监听Request消息**

服务端监听发送给自己的request消息。对应地，终端订阅消息Topic为：

> /${domain}/${`SERVER`.node-id}/`requests`/#

**第二步：客户端发送Request消息**

客户端向服务端发送Request消息，需要知道服务端的NodeId。其发送Request消息的Topic为：

> /${domain}/${`SERVER`.node-id}/`requests`/${request-id}/${`CLIENT`.node-id}/${tag}

#### 服务端响应消息过程

> 客户端监听发送给自己的replies消息。
> 服务端返回响应时，根据收到的Request消息，生成Reply消息，发送消息给客户端。

**第一步：客户端监听Reply消息**

接收响应的客户端，订阅消息Topic为：

> /${domain}/${`THIS`.node-id}/`replies`/#

**第二步：服务端发送Reply消息**

服务端发送Reply消息的Topic为：

> /${domain}/${`CLIENT`.node-id}/`replies`/${request-id}/${`THIS`.node-id}/${tag}

演示代码：

```java
final MQTTSocket server = MQTTSocket.context()
            .domain("next-mqtt")
            .nodeId("SERVER")
            .address("tcp://iot.eclipse.org:1883")
            .socket();

final MQTTSocket client = MQTTSocket.context()
            .domain("next-mqtt")
            .nodeId("CLIENT")
            .address("tcp://iot.eclipse.org:1883")
            .socket();

server.connect();
client.connect();

// 订阅发送给本服务端终端的Request消息，其订阅Topic为 "/next-mqtt/SERVER/requests/#"
final long reqrepId = server.addRequestMessageHandler(new MessageHandler() {
    @Override
    public void onMessage(MQTTSocket socket, Message request) {
        // 返回响应消息给客户端终端。发送消息的主题为 "/next-mqtt/CLIENT/replies/${req-id}/SERVER" 的消息
        server.send(server.newReplyMessageOf(request, request.payload));
    }
});

// 发送给服务端，并同步接收响应消息
System.out.println("客户端收到同步响应消息: " +
        client.sendCall(client.newRequestMessageFor("SERVER", "ECHO-SYNC".getBytes()).builder()
                .tag("ping-tag")
                .build()).execute());

// 发送给服务端，并异步接收响应消息
final Latched  reply = new Latched<>();
client.sendCall(client.newRequestMessageFor("SERVER", "ECHO-ASYNC".getBytes())).enqueue(new MessageCallback() {
    @Override
    public void onError(Exception error) {
        error.printStackTrace();
        reply.set(null);
    }

    @Override
    public void onMessage(MQTTSocket socket, Message message) {
        reply.set(message);
    }
});

System.out.println("客户端收到异步响应消息: " + reply.get());

server.removeRequestMessageHandler(reqrepId);

client.disconnect();
server.disconnect();

```

### 2.2 Pub-Sub 点对点通讯模式

Pub-Sub模式为事件广播模式，由客户端向服务端终端发布事件广播消息，服务端订阅消息并不作响应。

服务端终端订阅消息的Topic为：

> /${domain}/${`SERVER`.node-id}/`pubsub`/#

作为发送事件消息的客户端，其发送事件消息的Topic为：

> /${domain}/${`SERVER`.node-id}/`pubsub`/0/${`CLIENT`.node-id}/${tag}

需要说明的是，Pub-Sub消息的request-id是固定值，默认为为`0`。

在Pub-Sub模式中，客户端只发送事件消息，不等待响应；服务端只处理事件消息，不作响应。

演示代码：

```java
final MQTTSocket server = MQTTSocket.context()
            .domain("next-mqtt")
            .nodeId("SERVER")
            .address("tcp://iot.eclipse.org:1883")
            .socket();

final MQTTSocket client = MQTTSocket.context()
            .domain("next-mqtt")
            .nodeId("CLIENT")
            .address("tcp://iot.eclipse.org:1883")
            .socket();

server.connect();
client.connect();

// 订阅指定发送给本服务端终端的PubSub类消息
final long pubsubId = server.addSubMessageHandler(new MessageHandler() {
    @Override
    public void onMessage(MQTTSocket socket, Message receivedMessage) {
        System.out.println("服务端收到Pub消息：" + receivedMessage);
    }
});

// 客户端终端向指定NodeId的服务端发送Pub消息可以实现两个终端之间的点对点广播通讯。
client.send(client.newPubMessageFor(NODE_SERVER, "YOOJIA".getBytes()).builder()
        .tag("fun-tag") // 扩展用：可以基于Topic的tag来实现消息路由
        .build());
client.send(client.newPubMessageFor(NODE_SERVER, "CHEN".getBytes()));
server.removeSubMessageHandler(pubsubId);

client.disconnect();
server.disconnect();

```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)