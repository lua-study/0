# 一、原作者ReadMe
RTSPtoRTMP
## 1.1 使用JavaCV开发的rtsp流转rtmp流并进行推流的流媒体服务
>**原文章博客地址：[banmajio's blog](https://www.banmajio.com/)**
>**原csdn博客地址：[banmajio's csdn](https://blog.csdn.net/weixin_40777510)**
>**原项目gitee地址：[RTSPtoRTMP](https://gitee.com/banmajio/RTSPtoRTMP)**

> 参考：[javaCV开发详解之8：转封装在rtsp转rtmp流中的应用（无须转码，更低的资源消耗）](https://blog.csdn.net/eguid_1/article/details/83025621)

## 1.2 用到的技术：FFmpeg、JavaCV、ngingx

## 1.3 项目背景：将rtsp流转为rtmp流，配合video.js实现web端播放。

[注]：最基本的核心操作在CameraPush.java这个类中。

## 1.4 该项目需要搭配使用的nginx服务器下载地址：
[http://cdn.banmajio.com/nginx.rar](http://cdn.banmajio.com/nginx.rar)
下载后解压该文件，点击nginx.exe（闪退是正常的，可以通过任务管理器查看是否存在nginx进程，存在则说明启动成功了）启动nginx服务。nginx的配置文件存放在conf目录下的nginx.conf，根据需要修改。项目中的rtmp地址就是根据这个配置文件来的。

## 1.5 存在的问题：
>**项目搭建过程请参考原作者博文：[FFmpeg转封装rtsp到rtmp（无需转码，低资源消耗）](https://www.banmajio.com/post/638986b0.html#more)**
>**开发过程的遇到的问题和解决方法，[banmajio csdn](https://blog.csdn.net/weixin_40777510)**

# 二、二次开发
原作者将FFmpegFrameGrabber 进行重写，是因为需要按照自己项目需求进行开发。
所以，想学习并测试本项目时，将原作者封装的FFmpegFrameGrabber.java类删除，引用Jar包内的即可。

## 2.1 rtsp转rtmp功能测试
修改TestRtspToRtmpController 中对应的rtsp和rtmp地址，执行main方法，然后通过vlc播放转封装后的rtmp地址即可查看到视频正常播放。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)