#JFinal-mqtt插件说明
坚持努力学习JFinal一直坚持的一切从简的光荣传统，为JFinal的为发展壮大提供绵薄之力。

###插件在JFinal中的使用说明
```java
public void configPlugin(Plugins me) {
    //使用配置文件
    me.add(new MqttPlugin("mqtt.properties"));
    //不使用配置文件
    //MqttPlugin plugin = new MqttPlugin("tcp://127.0.0.1:1883", "clientId");
    //plugin.setAutomaticReconnection(true);
    //plugin.setCleanSession(true);
    //plugin.setConnectionTimeout(10);
    //plugin.setKeepAliveInterval(10);
    //plugin.setManualAcks(true);
    //plugin.setMaxConnections(20);
    //plugin.setUserName("test");
    //plugin.setPassword("test");
    //plugin.setVersion("3.1.1");
    //plugin.setReConnectionTimeInterval(10);
    //me.add(plugin);
}
public void afterJFinalStart() {
    try {
        //订阅消息
	MqttKit.sub("/hello", MqttKit.QOS_AT_LEAST_ONCE, new IMqttMessageListener() {
            public void messageArrived(String topic, MqttMessage message) throws Exception {
                System.out.println("主题:"+topic+"\t"+new String(message.getPayload()));
            }
        });
	//发布消息
	MqttKit.pub("/hello", "world".getBytes(), MqttKit.QOS_AT_LEAST_ONCE, false);
	//取消订阅
	MqttKit.unSub("/hello");
    } catch (MqttException e1) {
        e1.printStackTrace();
    } catch (Exception e) {
	e.printStackTrace();
    }
}
```
###mqtt插件配置文件说明
```text
#JFinal-mqtt插件配置文件

#MQTT Broker连接地址 默认地址:tcp://127.0.0.1:1883
mqtt.brokerURL=tcp://127.0.0.1:1883

#MQTT ClientId 默认值:"jf_mq_p_"+System.nanoTime()
mqtt.clientId=

#MQTT Client连接MQTT Broker时使用的用户名，密码 默认不设置
mqtt.userName=
mqtt.password=

#是否手动发送消息应答 该设置只在Qos=1有效 默认false
mqtt.manualAcks=false

#是否自动重连 默认false
mqtt.automaticReconnection=false

#自动检测连接重连时间 默认5s 该参数只在mqtt.automaticReconnection=生效
mqtt.reConnectionTimeInterval=5

#是否清理session，false时可接收离线消息 true忽略离线消息 默认true
mqtt.cleanSession=true

#连接MQTT Broker超时时间 默认:30s
mqtt.connectionTimeout=60

#MQTT 心跳时间间隔 默认60s
mqtt.keepAliveInterval=60

#使用MQTT协议的版本 默认3.1.1
mqtt.version=3.1.1

#MQTT最大连接数 默认:10
"mqtt.maxConnections=10

#MQTT SSL配置文件地址
mqtt.sslProperties=

#MQTT 消息保存方式 如果不设置，默认保存在内存中，设置了则保存着指定的目录下
mqtt.stroageDir=
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)