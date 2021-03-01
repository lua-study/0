##环境
- python3.7

- pytorch1.1.0

- torchvision 0.3.0

- cuda 9.0以上
##项目框架

-  Audio-and-video-demo
   - bgm   (背景语音播报文件)
   - images
     - ffempeg-img
     - rec-img 
   - model （自训练模型保存）
   -  video （输入输出视频文件）
   -  bgm.py
   -  combination.py
   -  ffempeg-img-recognition.py
   -  main.py
   -  putlabel.py

##模块
###ffempeg-img-recognition.py
&ensp;&ensp;&ensp;&ensp;将手势视频按帧分解为图片并保存

###bgm.py
&ensp;&ensp;&ensp;&ensp;给视频按照手势识别标签制作添加音频

###combination.py
&ensp;&ensp;&ensp;&ensp;将识别完并打上标签的手势图片合成为视频


###putlabel.py
&ensp;&ensp;&ensp;&ensp;对视频分解为帧的图片进行手势识别并贴上标签

###main.py
&ensp;&ensp;&ensp;&ensp;主函数



##使用
命令行使用

example：

 ```
  python main.py test.mp4(输入) out.mp4（输出）
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)