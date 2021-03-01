# 简介
https://edu.csdn.net/topic/ai115

# TinymMind上GPU运行费用较贵，每 CPU 每小时 $0.09，每 GPU 每小时 $0.99，所有作业内容推荐先在本地运行出一定的结果，保证运行正确之后，再上传到TinyMind上运行。初始运行推荐使用CPU运行资源，待所有代码确保没有问题之后，再启动GPU运行。


# 作业
使用tensorflow，构造并训练一个神经网络，在测试机上达到超过98%的准确率。
在完成过程中，需要综合运用目前学到的基础知识：
- 深度神经网络
- 激活函数
- 正则化
- 初始化
- 卷积
- 池化


并探索如下超参数设置：
- 卷积kernel size
- 卷积kernel 数量
- 学习率
- 正则化因子
- 权重初始化分布参数


## 数据集
```
下载地址：
http://yann.lecun.com/exdb/mnist/
或
https://storage.googleapis.com/cvdf-datasets/mnist/train-images-idx3-ubyte.gz
https://storage.googleapis.com/cvdf-datasets/mnist/train-labels-idx1-ubyte.gz
https://storage.googleapis.com/cvdf-datasets/mnist/t10k-images-idx3-ubyte.gz
https://storage.googleapis.com/cvdf-datasets/mnist/t10k-labels-idx1-ubyte.gz

```
Mnist 数据集由Yann LeCun（杨立坤）建立，基础数据部分来自美国国家标准与技术研究所（National Institute of Standards and Technology，NIST）。训练集 (training set) 由来自 250 个不同人手写的数字构成，其中 50% 是高中学生, 50% 来自人口普查局 (the Census Bureau) 的工作人员。测试集(test set) 也是同样比例的手写数字数据。
整个数据集包括60000张训练图片，10000张测试图片。每张图片为一个28x28的灰度图片。每个像素的数据类型为uint8，取值从0（背景）到255（前景）。

## 评价标准

- 准确度达到98%或者以上60分，作为及格标准，未达到者本作业不及格，不予打分。
- 使用了正则化因子或文档中给出描述：10分。
- 手动初始化参数或文档中给出描述：10分，不设置初始化参数的，只使用默认初始化认为学员没考虑到初始化问题，不给分。
- 学习率调整：10分，需要文档中给出描述。
- 卷积kernel size和数量调整：10分，需要文档中给出描述。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)