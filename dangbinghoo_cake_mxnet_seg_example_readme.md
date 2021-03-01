======================================
 MXNET GluonCV segmentation example
======================================

## 0. label data

using labelme from https://github.com/wkentaro/labelme

```
    pip install labelme
```

just tag image and save to json,  makesure all your iamge is jpg format. then using 

https://github.com/wkentaro/labelme/blob/master/examples/semantic_segmentation/labelme2voc.py

to convert labeled dir to VOC format.

prepare a labels.txt before run labelme2voc.py, and labels.txt is like this:
```
__ignore__
_background_
cake
```
your class name should bellow `_background_`, and don't remove or edit the first two lines.


Then convert,

```
python labelme2voc.py --labels  labels.txt YourTaggedDir  VoCFormatOutputDir
```

after that, in VoCFormatOutputDir

```
    mkdir -p ImageSets/Segmentation
```

and then divide your images filename to train.txt, val.txt, trainval.txt, test.txt
in my case, I have 1-100.jpg, so I made train.txt likes this:

```
1
2
3
4
...
51
52
53
```

and then 54-70 in val.txt, and trainval is train.txt + val.txt.

in test.txt, I just have 71-100.



## 1. install mxnet-cuda version and gluoncv

 ```
  pip install mxnet-cu100
  pip install gluoncv
 ```
 
## 2. install cakes_voc to GluonCV model zoo

 copy dir `cakes_voc` to  PYTHONENV/lib/python3.5/site-packages/gluoncv/data
 and edit  `PYTHONENV/lib/python3.5/site-packages/gluoncv/data/__init__.py`
 
 like this:
 
 ``` python
    from .mixup.detection import MixupDetection
    from .cakes_voc.segmentation import CakesVOCSegmentation

    datasets = {
        'ade20k': ADE20KSegmentation,
        'pascal_voc': VOCSegmentation,
        'pascal_aug': VOCAugSegmentation,
        'coco' : COCOSegmentation,
        'citys' : CitySegmentation,
        'cakes_voc' : CakesVOCSegmentation,
    }
 ```
 
## 3. train

 source gluoncv_env/bin/activate
 sh train.sh
 
 NOTE: when 1st train. remove --resume in train.sh
 
## 4. test

 source gluoncv_env/bin/activate
 sh test.sh


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)