# JTT1078-media-server

JTT1078 media server 是car-eye团队开发的基于JT1078 协议开发的视频服务器。

## 为什么我们要开发JT1078 视频服务器

JTT1078 协议是基于JT808协议制定的车载视频标准。这个协议采用TCP/UDP传输负载到流媒体服务器。与通用的RTSP和RTMP服务器不同，目前市场上的用户主要在TCP数据包转发成通用便于浏览器或者移动客户端所识别的RTMP，HLS等数据流上遇到很大困难。我们这个服务器主要解决视频转发和转换。方便快速开发自己的流媒体平台。

## JT1078 视频服务器在整个车载视频平台中的位置

一个通常的视频平台通常由下面框架构成：

![](https://github.com/Car-eye-team/JTT1078-media-server/blob/master/%E5%B9%B3%E5%8F%B0%E6%9E%B6%E6%9E%84.png)    

其中JT1078视频服务器解释了JTT1078 协议中的5.5.3 负载包，并将其中的流转化成通用的RTSP/RTMP数据流给流媒体服务器，方便客户端使用。


# 商业合作

JTT1078-media-server 商业用户需要鉴权，具体请联系团队管理人员


# 联系我们   

car-eye 开源官方网址：www.car-eye.cn     

car-eye 流媒体平台网址：www.liveoss.com     

car-eye 技术官方邮箱: support@car-eye.cn   

car-eye技术交流QQ群: 590411159      

![](https://github.com/Car-eye-team/Car-eye-server/blob/master/car-server/doc/QQ.jpg)    

CopyRight©  car-eye 开源团队 2018 




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)