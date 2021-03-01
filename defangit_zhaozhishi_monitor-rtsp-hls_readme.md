# monitor-rtsp-hls

#### 介绍
视频监控RTSP转RTMP转HLS解决方案

由于公司业务，需要实现基于WEB访问监控摄像头实时流的预览，经过各种百度，补充了不少相关知识，了解到了很多大神的实现方法，也因为很多过时的帖子，而踩了不少的坑。

尝试过nginx+ffmpeg的方案，虽然可行，但是实现单摄像头还行，想不明白如何实现多摄像头预览，尝试过写脚本，同时处理多个摄像头，但结果是服务器卡死。

后来尝试通过代码，动态根据当前要访问的设备，来调用ffmpeg命令处理该设备，最终因效果不好，而且各种无法控制而告终。

最终无意间浏览到一大神写的使用javacv实现通过调用ffmpeg库的实现方法，于是就尝试用此方法推流给nginx，由nginx负责将流切片保存，并配置nginx自动删除旧的切片，以节省硬盘空间。

#### 运行流程
![输入图片说明](https://images.gitee.com/uploads/images/2020/0324/185845_f351918b_107658.png "Untitled Diagram.png")


#### 使用说明

1.  参考根目录下的nginx.conf来配置自己的web代理nginx
2.  解压nginx-rtmp-server.zip，这是作为rtmp流服务器用的nginx版本，可自行修改conf/nginx.conf配置
3.  导入monitor-rtsp-hls至eclipse，右键Main.java运行即可，生产环境可打成jar包来运行也可导出为war包部署tomcat运行

#### 打jar包

代码中是集成的Undertow服务器，在项目根目录下执行mvn clean package即可执行打包操作，在target目录下生成项目同名release压缩包，上传服务器解压，修改conf目录中monitor.properties设备配置信息后，即可执行start.bat运行

#### 2020-06-10 补充说明

本项目中的代码是研究参考了很多方案后实现的，和大神的比起来确实是比较糙，但是我的目的只是希望能贡献一个方法，以帮助和我当初有同样困扰的朋友解决问题。

另外说到延迟，我觉得延迟是有，不过就我个人认为，转存后再提供对外访问的实现方式都是存在延迟的，万幸的是好在我们的业务不在乎这个问题。

#### 2020-06-16 奉上整理的几个厂家（主要是海康、大华和宇视）RTSP地址格式

[分享链接](https://mubu.com/doc/4IvOBWbQq-P)

#### 感谢

1.  JFinal作者波总开发这么好用的框架，让我爱不释手
2.  参考网上整理的各主流摄像头的rtsp地址格式
3.  还有网上大神写的基于javacv将rtsp推至nginx rtmp的帖子，现在找不到了

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)