# OpenCV加Zxing二维码识别

#### 项目介绍
OpenCV+zxing实现二维码识别，用于弥补单独使用zxing无法识别复杂环境下二维码无法识别的情况，比如黑色二维码在黑色背景下识别困难等情况。
项目转自： [https://blog.csdn.net/lldbuaa/article/details/80333718](https://blog.csdn.net/lldbuaa/article/details/80333718)

#### 说明
本项目直接运行的debug包大小超过100M，主要是由OpenCV的jinLibs占据， 
建议使用时根据情况精简 openCVLibrary330\src\main\jniLibs目录下的文件，可以只留armeabi包下的libopencv_java3.so文件，能够满足大部分的需求， 
如果用不到全部内容可以对OpenCV的java代码精简，不使用libopencv_java3.so文件而是只保留用到的.a文件 
![image](https://gitee.com/prpr894/QRCode_OpenCV_zxing/raw/master/Screenshots/OPENCV.PNG)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)