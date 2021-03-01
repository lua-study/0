# camHumDetect

#### 项目介绍
OpenCVCamera行人检测及跟踪

#### 环境
Python 3.5+

#### 安装教程

	pip3 install -r requirements.txt

若依赖包有增加，请更新requirements文件

	pip freeze > requirements.txt



#### 使用说明

camShift.py 网络DEMO [基于camShift算法的视频物体跟踪](https://blog.csdn.net/zhangruijerry/article/details/79088945)

hik.py 海康摄像头取流

hikHumDetect.py 基于海康摄像头的行人检测

hikTransform.py 基于海康摄像头的坐标转换 3D->2D

humdetect.py [基于静态图片的行人检测](https://blog.csdn.net/garfielder007/article/details/50441048)

transform.py [原始坐标转换代码3D->2D](http://note.youdao.com/noteshare?id=5739daddb83b6a04dc208fa70c9b2c97)

vLocation.py 基于海康相机的行人检测并标注转换后的坐标  
[如何优化检测速率](https://www.zhihu.com/question/27662700)  
1、高斯背景法建模  
2、对检测出的运动团块用面积，复杂度，位置，外接矩形长宽比等进行粗略的分类  
3、最后在这个范围附近区域进行hog+svm  
[训练行人检测模型](https://blog.csdn.net/zhazhiqiang/article/details/20723425)

xyTrans.py xy坐标转换前后标注效果测试

temp.py 乱七八糟测试代码

PeopleDetect.py 使用识别库demo

face.xml 识别库

start.py 项目启动，开发ing

Mat&UMatVideo.py 两种模式性能测试.视频

Mat&UMatImg.py 两种模式性能测试.图片

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)