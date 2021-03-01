# 摄像头视频采集与存储系统

#### 项目介绍
主要利用FFmpeg和Qt实现摄像头视频流的采集与本地存储，将摄像头对的视频流显示到界面上，并存储到本地为.avi格式。

主要转换思路：视频流rtsp--->yuv--->.h264--->.avi。

####联系方式
/**
 * 李震
 * 我的码云：https://git.oschina.net/git-lizhen
 * 我的CSDN博客：http://blog.csdn.net/weixin_38215395
 * 联系：QQ1039953685
 */

#### 软件架构

编译器：VS2015+qt win32
外部库：FFmpeg-20180614-win32

1. 类V10：视频显示类，用于接受来自vidoeplayer类解码后的QImage图像，并可实现对类V20的调用.
2. 类VideoPlayer:视频流解码类，主要实现视频流的解码，yuv图像的存储，光源中心坐标的识别.
3. 类V20：YUV转h.264参数设置界面类，主要用于设置YUV->h.264转换时的参数设置.
4. 类Convert:将YUV转换为最终的.avi视频格式，命名为output.avi.


#### 程序运行界面
![输入图片说明](https://images.gitee.com/uploads/images/2018/0710/091826_d444e949_1477507.png "1.png")
![输入图片说明](https://images.gitee.com/uploads/images/2018/0710/091836_5856b035_1477507.png "2.png")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)