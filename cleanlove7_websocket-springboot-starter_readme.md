# websocket-springboot-starter

#### 项目介绍
websocket-springboot-starter to develop websocket

项目主要适用于服务端有数据变动想主动通知客户端场景，例如web网络聊天室，服务端数据变动通知web页面等。解决服务端和客户端的双向通信，可以代替ajax轮询技术。在服务端主动通知的场景下可以大幅度降低架构复杂度。
在开发WebSocket的时候一般会遇到两个问题：

1. 如何存储Session？
2. 如何集群？

我们一般都用一个`Map`来存储`Session`，你会在`@ServerEndPoint`类中见到类似`public static final Map  sessions = new ConcurrentHashMap<>();`这样的代码。基于此也能开发，
但是一个很大的问题就是不易扩展。基于此考虑，本项目将针对`Session`的处理的代码提成接口`WebSocketManager`，实现了单机版的和集群的，于是在两种场景下使用方式完全一样。
```java
public interface WebSocketManager {
    /**
     * 在容器中的名字
     */
    String WEBSOCKET_MANAGER_NAME  = "webSocketManager";
    /**
     * 根据标识获取websocket session
     * @param identifier 标识
     * @return WebSocket
     */
    WebSocket get(String identifier);

    /**
     * 放入一个 websocket session
     * @param identifier 标识
     * @param webSocket websocket
     */
    void put(String identifier, WebSocket webSocket);

    /**
     * 删除
     * @param identifier 标识
     */
    void remove(String identifier);

    /**
     * 获取当前机器上的保存的WebSocket
     * @return WebSocket Map
     */
    Map  localWebSocketMap();

    /**
     * 统计所有在线人数
     * @return 所有在线人数
     */
    default int size(){
        return localWebSocketMap().size();
    }

    /**
     * 给某人发送消息
     * @param identifier 标识
     * @param message 消息
     */
    void sendMessage(String identifier, String message);

    /**
     * 广播
     * @param message 消息
     */
    void broadcast(String message);

    /**
     * WebSocket接收到消息的函数调用
     * @param identifier 标识
     * @param message 消息内容
     */
    void onMessage(String identifier , String message);

    /**
     * 在OnMessage中判断是否是心跳,
     * 从客户端的消息判断是否是ping消息
     * @param identifier 标识
     * @param message 消息
     * @return 是否是ping消息
     */
    default boolean isPing(String identifier , String message){
        return "ping".equalsIgnoreCase(message);
    }

    /**
     * 返回心跳信息
     * @param identifier 标识
     * @param message 消息
     * @return 返回的pong消息
     */
    default String pong(String identifier , String message){
        return "pong";
    }
}
```

集群版的基于Redis的发布订阅功能，为什么要整这么复杂呢？不能像`HttpSession`一样直接存储到Redis吗？不能，因为WebSocket的`Session`无法序列化。`java.io.NotSerializableException`。

使用时面向接口`WebSocketManager`，支持单机（基于内存）和集群（基于Redis的发布订阅）

#### 软件架构
1.基于springboot websocket 定制，主要完成的功能是WebSocket session的状态管理，具备单机和集群能力。
2.可以定制自己的ServerEndPoint和WebSocketManager。

JFinal或者其他Web架构下开发WebSocket参见 https://gitee.com/xxssyyyyssxx/jfinal-websocket


#### 安装教程

compile 'top.jfunc.websocket:websocket-springboot-starter:1.8.2.3'

使用方式参见 https://gitee.com/xxssyyyyssxx/websocket-demo

#### 使用说明

```
/**
 * 1.继承自 top.jfunc.websocket.BaseWebSocketEndpoint
 * 2.标注@Component @ServerEndpoint
 * @author xiongshiyan
 */
@Component
@ServerEndpoint(value ="/websocket/connect/{identifier}")
public class WebSocketEndpoint extends top.jfunc.websocket.BaseWebSocketEndpoint{
}
```

```
@EnableMemWebSocketManager 单机管理
或者
@EnableRedisWebSocketManager 利用Redis的订阅/发布机制实现集群管理
```

```
@Configuration
public class WebSocketConfig {
    /**
     * @see https://www.cnblogs.com/betterboyz/p/8669879.html
     * 首先要注入ServerEndpointExporter，这个bean会自动注册使用了@ServerEndpoint注解声明的Websocket endpoint。
     * 要注意，如果使用独立的servlet容器，而不是直接使用springboot的内置容器，就不要注入ServerEndpointExporter，
     * 因为它将由容器自己提供和管理， 否则就会报重复的endpoint错误。
     */
    @ConditionalOnProperty(prefix = "server.websocket.exporter" ,
                                name = "enable" ,havingValue = "true")
    @Bean
    public ServerEndpointExporter serverEndpointExporter() {
        return new ServerEndpointExporter();
    }


    /**
     * 可以使用自己的WebSocketManager，注意名字是固定的
     */
    /*@Bean(WebSocketManager.WEBSOCKET_MANAGER_NAME)
    public WebSocketManager webSocketManager(){
        return new WebSocketManager...();//继承自WebSocketManager
    }*/
}
```

如果使用了 ** Nginx ** 作为负载均衡器，则需要在配置中添加

```
Nginx反向代理要支持WebSocket，需要配置几个header，否则连接的时候就报404
       proxy_http_version 1.1;
       proxy_set_header Upgrade $http_upgrade;
       proxy_set_header Connection "upgrade";
       proxy_read_timeout 3600s; //这个时间不长的话就容易断开连接
```

关于心跳监测，模仿 `top.jfunc.websocket.config.WebSocketSchedulingConfig` 自己配置一下即可
新增三个配置项开启心跳监测

- webSocket.heartCheck.enabled=true
- webSocket.heartCheck.timeSpan=1000
- webSocket.heartCheck.errorToleration=30

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)