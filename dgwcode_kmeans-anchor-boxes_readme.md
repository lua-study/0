# kmeans-anchor-boxes
This repository contains an implementation of k-means clustering with the Intersection over Union (IoU) metric as described in the YOLO9000 

在使用XML标注数据时候使用

## 数据规则
```
F:\train\kmeans-anchor-boxes>python test.py
label count: 7581
[[0.03203125 0.05940594]
 [0.01486989 0.03201507]
 [0.0671875  0.11388889]
 [0.01219512 0.0249584 ]
 [0.02363636 0.04697987]
 [0.10532784 0.18011705]
 [0.046      0.079     ]
 [0.01853568 0.0381558 ]
 [0.19672691 0.33701632]]
Accuracy: 81.00%
Boxes:
 [ 20.5          9.51672862  43.           7.80487805  15.12727273
  67.40981554  29.44        11.86283596 125.90522088]-[ 38.01980198  20.48964218  72.88888889  15.9733777   30.06711409
 115.2749114   50.56        24.41971383 215.69044341]
Ratios:
 [0.46, 0.49, 0.49, 0.5, 0.54, 0.58, 0.58, 0.58, 0.59]
 
 使用值:
 anchors = 20,38,  9,20,  43,72,  7,15,  15,30,  67,115,  29,50,  11,24,  125,215
```
## Usage

To try out the results yourself, download the annotations here: http://host.robots.ox.ac.uk/pascal/VOC/voc2007/. Then change the constant ANNOTATIONS_PATH in test/test_voc2007.py and finally run:

```
python3 -m unittest discover -s tests/
```

## References




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)