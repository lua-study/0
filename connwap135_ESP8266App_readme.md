 This project is a app collections of ESP8266 WiFi SoC.
 
Include: 
1.App as fireware using SDK. 
but not include SDK,which provide by www.espressif.com. 
2.Arduino app using ESP8266Lib,a opensource lib. 
At https://git.oschina.net/supergis/ESP8266Lib 
3.Other MCU app based esp8266 module. 
4.Apps for Android/iOS/Linux/Windows. 
5.Utilies for test and flash IC. 

 2014-12-30:
 Add more Interesting project for esp8266 with opensource.
 include: **nodemcu,nodelua,mpython,rtos,at,mqtt,frankstein**.
 can using x-git clone this project quickly.
 latest build placed at ./firmware.

 2014-12-28:
 Add a esp8266 resource list, on **./resources/esp8266_resources.txt**.

 2014-12-26:
 Add esp8266-examples and wixcmd all sourcecode. wixcmd implement XCMD protocol,which transmit data with Arduino or other MCU smartly.
 XCMD like AT commandset,but with "@+" head other than "AT+".
 If data-string not begin with "@",then transmit data between uart and wifi Immediately, which fast and simple than any other protocol.
=======
# Low Power Voltage Measurement

This is a project for ESP8266 for low power sensor applications. 
The chip powers on once every 1 minute, and sends the data to the 
server, once every 20 minutes. 

The project is based on Espressif's SDK version 0.9.5. More details
about the project can be found in the Wiki. 
>>>>>>> upstream/master


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)