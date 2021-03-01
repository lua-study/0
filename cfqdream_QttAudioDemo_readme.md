# QttAudioDemo

#### 介绍

QttAudioDemo是QttAudio在Windows平台的Demo，支持语音和视频通信。

Note：配置文件为wincfg.txt，可以配置服务器、房间号、帧率、码率等参数。默认房间号为12345，双方必须为同一房间才可通信。  
具体参数说明如下。  
{  
　　　　"server": "cn.qingspeech.com",   //北京服务器，香港服务器是:hk.qingspeech.com，新加坡：sg.qingspeech.com，美国：us.qingspeech.com  
　　　　"port" : 9010,                                //不改动  
　　　　"room": 12345,                        //房间号  
　　　　"role": "TALKER",                         //主播模式，默认都是这个，听众模式为AUDIENCE  
　　　　"fps": 15,                                      //帧率  
　　　　"bitrate": 819200,                       //比特率  
　　　　"cap_width": 640,                        //视频宽  
　　　　"cap_height": 480                       //视频高  
}  
配置文件修改请保存后，重启应用程序方可生效。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)