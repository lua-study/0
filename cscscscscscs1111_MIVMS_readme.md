# MIVMS

#### 介绍
鼹鼠智能售货机系统(Mole intelligent vending machine system)是一套物联网控制系统性的解决方案。  
主要涉及到的语言和库有c,c++,js,nodejs,vue.js,thinkphp。
整套系统主要作用是打通网站后台，网站前端，手机前端，单片机和微型电脑之间的通信和系统的构建。  

现阶段已经实现下面功能：  
1. 网站后台部分，采用YZNCMS作为后台管理部分，已经实现各种支付场景，语音识别和合成功能，和MQTT服务器的通信功能；  
2. 网站前端和手机前端部分，采用vue.js作为前端开发，已经实现和网站后台的跨域通信，和MQTT服务器的通信功能；  
3. 单片机部分，已经实现ESP8266,ESP32配网功能，ESP8266,ESP32和MQTT服务器的通信功能；  
4. 微信电脑部分，主要基于树莓派加linux系统，编程语言主要是node.js，已经实现和网站后台服务器基于http协议的通信功能，基于MQTT协议的和服务器通信功能，与单片机通信的串口功能；  

官方网站:  
http://mivms.kfapp8.cc/  
   
整套系统主要分为4个部分：  
1. MQTT服务器 - 主要采用开源项目Eclipse Mosquitto™作为整个系统的通信系统；
2. 后台管理 - 主要基于开源系统YZNCMS开发；
3. 手机监控和管理端 - 主要基于开源前端框架vue.js开发;
4. websocket和其它服务相关 - 主要基于开源软件node.js开发；
5. 单片机部分主要基于ESP8266,ESP32
6. 微型电脑部分主要基于树莓派，编程语言为node.js

#### 软件架构
Mosquitto在整个系统中处于最中心的作用，它将连接我们在线的所有设备，包括售货机，手机，后台管理，服务器等等。  
售货机通过Mosquitto发送系统到手机或者后台服务器用于储存数据库或者在手机上监控。  

#### 未来计划
1. 接入百度AI系统，实现和小度音响的交互；
2. 通过ESP32，实现实时监控功能；
3. 基于神经网络的机器学习部分

#### 截图预览
![机器桌面截图和摄像头截图](https://gitee.com/akinggw/MIVMS/raw/master/screen/screen1.png)
![机器实时在线监控](https://gitee.com/akinggw/MIVMS/raw/master/screen/screen2.png)
![机器购买界面](https://gitee.com/akinggw/MIVMS/raw/master/screen/screen3.jpg)
![扫码付款界面](https://gitee.com/akinggw/MIVMS/raw/master/screen/screen4.jpg)
![实时监控机器温度和订单情况](https://gitee.com/akinggw/MIVMS/raw/master/screen/screen5.jpg)
![后台管理系统](https://gitee.com/akinggw/MIVMS/raw/master/screen/screen6.jpg)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)