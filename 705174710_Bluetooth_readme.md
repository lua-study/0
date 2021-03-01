# Bluetooth
Arduino-BT-Android文件夹下是使用蓝牙模块HC05和Android通信的App, 以arduino作为蓝牙的控制端

Arduino-BLE-Android文件夹下是使用低功耗蓝牙模块和Android通信的App




### Arduino-BT-Android

 - HC05蓝牙模块：作为Server，设置成从模式
 - 手机：作为Client，在Android中给定蓝牙设备的MAC地址去连接，UUID要设置成串口操作专用的00001101-0000-1000-8000-00805F9B34FB。 连接上蓝牙设备之后通过Handler向主线程传送连接状态、收发消息。主线程更新UI

----

### Arduino-BLE-Android

- 低功耗模块：作为低功耗蓝牙的中心设备，创建Service，添加Characteristic

- 手机：作为Client，连接蓝牙设备后扫描Service，并对检测到的Characteristic进行监听，一旦有更新就显示出来


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)