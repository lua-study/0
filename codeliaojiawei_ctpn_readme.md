# ctpn

#### 项目介绍
使用tensorflow对文字检测网络(Connectionist Text Proposal Network)的复现，代码简单易懂，适合初学者学习
if you are in china ,you can visit https://gitee.com/hengk/ctpn. 
#### 软件架构


软件架构说明

- core

    - datalayer.py 根据网络输入的image和label数据生成计算loss时需要的数据

    - resnet.py 网络中的cnn模块

    - lstm.py  网络中的rnn模块

    - loss.py  网络的loss计算方式

    - proposallayer.py 将网络输出的数据转化为最后的Proposal region

    - textdetector.py  conect the proposal boxes

    - c_utils.c  使用纯c写的nms算法以及iou算法

    - c_textproposalconnector.c 使用纯c写的基于图的文本构造算法
    
    - c_datalayer.c  to handle training data
    
    - c_proosallayer.c to handle the output of newwork

    - make.sh  将uitls.c 编译为 so文件

    - data

    - prehandle.py  对图片进行前期的预处理，包括对gt_box的分割，还有对图片的宽高比进行排序


#### 使用说明
1. 标签的生成
    在data目录下面，首先生成新的图片以及对应的标签（因为要将源标签拆分为宽度为16的框框，以及对原图进行大小的缩放）
    
    python  prehandle.py -g [src_iamge_folder] [src_label_folder] [new_image_folder] [new_label_folder]
    
    然后生成一个文件，里面内容是图片按照宽高比进行排序所得
        
    python prehandle.py -s [image_folder] [file]

    在core目录下生成c_utils.so
        
    ./make.sh

2. 训练参数设置
    在Config.py中设置一些参数


3. 测试程序

    
    调用 python test.py [src_image]  [dst_image]来测试


4.图片效果
   ![输入图片说明](https://images.gitee.com/uploads/images/2019/0103/160521_a6abe477_1861688.jpeg "m.jpg")

   ![输入图片说明](https://images.gitee.com/uploads/images/2019/0103/160814_e756d016_1861688.jpeg "m1.jpg")
    



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)