# Salient-Object-Detection
This is tensorflow implementation for cvpr2017 paper "Deeply Supervised Salient Object Detection with Short Connections"

 Pretrained Model 
https://drive.google.com/open?id=0B6l9O8aWij8fUGtVNldUTXA4eHc

 Usage 
1. Download pretrained model and put them under folder "salience_model" ,(need to create folder yourself) 
2. run code 

If you want to test whole folder images, run this:  

```
python inference.py --rgb_folder=[your folder]
```

sample:  

```
python inference.py --rgb_folder=./test
```

If you want to test only one image,run this:  

```
python inference.py --rgb=[your image]
```

sample:

```
python inference.py --rgb=animal1.jpg
```

 Sample 

![Sample](samples/1.png)

more detail please read source code.


### 2018-03-02

I'm considering to open source training code recently(in several months), but to be honest, I don't understand why this model works so well(even there is some mis-using of tensorflow, but it works..). 



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)