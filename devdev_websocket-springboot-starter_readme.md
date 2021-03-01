# websocket-springboot-starter

#### 项目介绍
websocket-springboot-starter to develop websocket

#### 软件架构
1.基于springboot websocket 定制，主要完成的功能是WebSocket session的状态管理，具备单机和集群能力。
2.可以定制自己的ServerEndPoint和WebSocketManager。

使用方式参见 https://gitee.com/xxssyyyyssxx/websocket-demo
#### 安装教程

compile 'top.jfunc.websocket:websocket-springboot-starter:1.0'

#### 使用说明

```
/**
 * 1.继承自 top.jfunc.websocket.WebSocketEndpoint
 * 2.标注@Component @ServerEndpoint
 * @author xiongshiyan
 */
@Component
@ServerEndpoint(value ="/websocket/connect/{identifier}")
public class WebSocketEndpoint extends top.jfunc.websocket.WebSocketEndpoint{
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

关于心跳监测，模仿 `top.jfunc.websocket.config.WebSocketSchedulingConfig` 自己配置一下即可
新增三个配置项开启心跳监测

- webSocket.heartCheck.enabled=true
- webSocket.heartCheck.timeSpan=1000
- webSocket.heartCheck.errorToleration=30

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)