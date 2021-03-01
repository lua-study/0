# MTCNN state-of-the-art face detection method

## Last Update 2018.05.7

## 概述

[MTCNN](https://kpzhang93.github.io/MTCNN_face_detection_alignment/index.html)是[Kaipeng Zhang](https://kpzhang93.github.io/)等人提出的多任务级联卷积神经网络进行人脸检测的方法，是迄今为止开放源码的效果最好的人脸检测器之一，[在fddb上有100个误报时的检出率高达90%以上](https://github.com/imistyrain/fddb-windows)，作者提供的版本为[matlab版](https://github.com/kpzhang93/MTCNN_face_detection_alignment),它最终的效果如图所示：

![](https://i.imgur.com/FbglxoX.jpg)

这个项目包含了几乎所有深度学习框架的MTCNN实现，并且都基于最近版进行了测试，所有示例均可正常运行，可跨Windows、Linux和android平台，是当前人脸检测的不二之选

## OpenCV版 C++

将本项目中的Fast-MTCNN设为启动项，安装opencv3.3及以上版本（3.2及以下版本需自行编译dnn库）

添加对应的头文件路径和库文件路径

## caffe版 C++

1.按照[MRHead](https://github.com/imistyrain/MRHead)描述的方法配置好opencv跨平台编译环境

2.编译最新版[caffe](https://github.com/BVLC/caffe)，这个网上已有很多[教程](http://blog.csdn.net/akashaicrecorder/article/details/71016942),恕不赘述
```
git clone https://github.com/BVLC/caffe
cd caffe
git checkout windows
script\build_win.cmd
```

3.打开MTCNN.sln，把MTCNN设为启动项。

4.设置所需的环境变量

打开菜单里的视图->其他窗口里面的属性管理器，依次展开MTCNN、Debug\x64子节点，然后在Microsoft.Cpp.x64.user项上右键，选择属性窗口，找到VC++目录，包含目录，将以下路径添加到包含目录项里

C:\Users\lenovo\.caffe\dependencies\libraries_v140_x64_py27_1.1.0\libraries\include

D:\CNN\caffe\include

D:\CNN\caffe\build

D:\CNN\caffe\build\include

其中lenovo是我的电脑用户名，请换成你自己的名，D:\CNN\caffe是我本机caffe包所在路径

将以下路径加入到库路径：

C:\Users\lenovo\.caffe\dependencies\libraries_v140_x64_py27_1.1.0\libraries\x64\vc14\lib

C:\Users\lenovo\.caffe\dependencies\libraries_v140_x64_py27_1.1.0\libraries\lib

D:\CNN\caffe\build\lib

拷贝以下文件夹下的所有dll文件至系统路径文件夹下(比如C:\Windows\Systems32)

D:\CNN\caffe\build\install\bin

5.编译运行

程序默认会读取imgs文件下的文件，把检测结果输出到results文件夹下，如果想测试摄像头的效果，在main.cpp的main函数里将testcamera();解注释即可

## caffe版 python

修改demo.py中开头处caffe_root的路径为本机路径，然后运行

```
python demo.py
```

## mxnet版 python

编译mxnet的windows版，参考[mxnet VS2015编译
](https://github.com/imistyrain/mxnet-oneclick/blob/master/mxnet%20VS2015%E7%BC%96%E8%AF%91.pdf)，然后打开MTCNN.sln,把MTCNNPy设为启动项.加载此工程需要安装VS python的插件[PTVS 2.2.6 VS 2015](https://github.com/Microsoft/PTVS/releases/v2.2.6)

## ncnn版 C++

编译过ncnn库后，将本项目中的ncnn设为启动项，并修改相应的头文件和库文件路径


## tensorflow版 python

```
pip install tensorflow或pip install tensorflow-gpu(GPU版)
python demo.py
```

## MTCNN-light 快速版本 C++

和普通opencv程序配置方法一致

## 参考

*  [Win10+VS2015 caffe环境搭建](http://blog.csdn.net/akashaicrecorder/article/details/71016942)

* [fddb-windows](https://github.com/imistyrain/fddb-windows)

* [ncnn-mtcnn](https://github.com/Longqi-S/ncnn-mtcnn)

* [mxnet_mtcnn_face_detection](https://github.com/pangyupo/mxnet_mtcnn_face_detection)

* [MTCNN_face_detection_caffe](https://github.com/LucyLu-LX/MTCNN_face_detection_caffe)

* [mtcnn_tf](https://github.com/BobLiu20/mtcnn_tf)

* [MTCNN-Tensorflow](https://github.com/AITTSMD/MTCNN-Tensorflow)

* [MTCNN-light](https://github.com/AlphaQi/MTCNN-light)

* [facenet](https://github.com/davidsandberg/facenet)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)