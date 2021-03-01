# SafeHatDetect

#### 介绍
安全帽检测

#### 软件架构
采用yolo3训练的darknet


#### 安装教程

1. 安装darknet GitHub：https://github.com/pjreddie/darknet
2. 代码提供了Windows编译好的exe，可直接使用
3. 数据：链接：https://pan.baidu.com/s/1ZZLaFi7fDxuwxu1EJlEGDQ 提取码：9qni 

#### 使用说明

1. train:darknet.exe detector train cfg/voc.data cfg/xxx.cfg darknet53.conv.74
2. val:darknet.exe detector valid cfg/voc.data cfg/xxx.cfg backup/xxx.weights -out 123 -thresh 0.5
3. 计算map参考val/voc_eval.py
#### 结果分析
达到实时效果，准确率在83%左右

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)