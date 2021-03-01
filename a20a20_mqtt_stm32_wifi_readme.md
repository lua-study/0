#mqtt_stm32_wifi

发布:mosquitto_pub.exe -h 10.0.24.3 -t 18124615747/strongbox/in/test -m success8
订阅:mosquitto_sub.exe -h 10.0.24.3 -t 18124615747/strongbox/out/+

可接收离线消息设置，QoS不能等于0
mosquitto_pub.exe  -h 10.0.24.2 -i wcliu2 -t 18124615747/strongbox/out/test -r -q 1 -m 51
mosquitto_sub.exe -h 10.0.24.2 -c -i wcliu1 -q 1 -t 18124615747/strongbox/out/+

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)