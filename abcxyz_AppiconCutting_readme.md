# AppiconCutting

#### 介绍
用Python为xcode剪切APP图标

#### 软件架构
使用Python3、pillow


#### 安装教程

1. 安装Python3
2. 安装pillow：python3 -m pip install Pillow

   

#### 使用说明

1. 把源码文件：cutting.py 和 png图片（1024*1024）放到同一个文件夹下；
2. 打开命令行定位到该文件夹下；
3. 运行命令：$ python3 ./cutting.py -i appicon.png
4. 把Contents.json文件丢进刚刚生成的AppIcon.appiconset中
5. 把整个AppIcon.appiconset文件夹拖进xcode中即可

如果有其他尺寸需求，可以去源代码里面添加相应的尺寸，添加后，Contents.json里也要对应添加指定的字段。

尺寸规范参考苹果官方文档：https://developer.apple.com/library/archive/qa/qa1686/_index.html

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)