## 介绍

YOLOv3是目前目标检测中最主流的算法，有大量的使用案例及各种框架下的代码实现，该仓库为Udacity课程作业，用YOLOv3实现推理，不包含训练代码。

1. 网络结构

![1586828221715](img/1586828221715.png)

​	DBL:代码中的Darknetconv2d_BN_Leaky，是yolo_v3的基本组件。就是卷积+BN+Leaky relu。

​	resn：n代表数字，有res1，res2, … ,res8等等，表示这个res_block里含有多少个res_unit。

​	concat：张量拼接。将darknet中间层和后面的某一层的上采样进行拼接。拼接的操作和残差层add的操作是不一样的，拼接会扩充张量的维度，而add只是直接相加不会导致张量维度的改变。

2. **backbone**：darknet-53

   - lYolo_v3使用了darknet-53的前面的52层（没有全连接层），yolo_v3这个网络是一个全卷积网络，大量使用残差的跳层连接，并且为了降低池化带来的梯度负面效果，作者直接摒弃了POOLing，用conv的stride来实现降采样。在这个网络结构中，使用的是步长为2的卷积来进行降采样。

   - l为了加强算法对小目标检测的精确度，YOLO v3中采用类似FPN的upsample和融合做法（最后融合了3个scale，其他两个scale的大小分别是26×26和52×52），在多个scale的feature map上做检测。

   - l作者在3条预测支路采用的也是全卷积的结构，其中最后一个卷积层的卷积核个数是255，是针对COCO数据集的80类：3*(80+4+1)=255，3表示一个grid cell包含3个bounding box，4表示框的4个坐标信息，1表示objectness score。

![1586828418248](img/1586828418248.png)

3. **output**
   - 多尺度就是来自这3条预测之路，y1,y2和y3的深度都是255，边长的规律是13:26:52。yolo v3设定的是每个网格单元预测3个box，所以每个box需要有(x, y, w, h, confidence)五个基本参数，然后还要有80个类别的概率。所以3×(5 + 80) = 255。这个255就是这么来的。
   - 网络中作者进行了三次检测，分别是在32倍降采样，16倍降采样，8倍降采样时进行检测,这样在多尺度的feature map上检测跟SSD有点像。在网络中使用up-sample（上采样）的原因:网络越深的特征表达效果越好，比如在进行16倍降采样检测，如果直接使用第四次下采样的特征来检测，这样就使用了浅层特征，这样效果一般并不好。如果想使用32倍降采样后的特征，但深层特征的大小太小，因此yolo_v3使用了步长为2的up-sample（上采样），把32倍降采样得到的feature map的大小提升一倍，也就成了16倍降采样后的维度。同理8倍采样也是对16倍降采样的特征进行步长为2的上采样，这样就可以使用深层特征进行detection。
   - 作者通过上采样将深层特征提取，其维度是与将要融合的特征层维度相同的（channel不同）。如下图所示，85层将13×13×256的特征上采样得到26×26×256，再将其与61层的特征拼接起来得到26×26×768。为了得到channel255，还需要进行一系列的3×3，1×1卷积操作，这样既可以提高非线性程度增加泛化性能提高网络精度，又能减少参数提高实时性。52×52×255的特征也是类似的过程。

![1586828482182](img/1586828482182.png)

4. Anchor Box
   - 三次检测，每次对应的感受野不同，32倍降采样的感受野最大，适合检测大的目标，所以在输入为416×416时，每个cell的三个anchor box为(116 ,90); (156 ,198); (373 ,326)。16倍适合一般大小的物体，anchor box为(30,61); (62,45); (59,119)。8倍的感受野最小，适合检测小目标，因此anchor box为(10,13); (16,30); (33,23)。所以当输入为416×416时，实际总共有（52×52+26×26+13×13）×3=10647个proposal box。

![1586828536020](img/1586828536020.png)

![1586828548398](img/1586828548398.png)

![1586828554993](img/1586828554993.png)

![1586828562360](img/1586828562360.png)

5. LOSS Function

   - YOLOv3重要改变之一：No more softmaxing the classes。
      YOLO v3现在对图像中检测到的对象执行多标签分类。

   - ```
     xy_loss = object_mask * box_loss_scale * K.binary_crossentropy(raw_true_xy, raw_pred[..., 0:2],
                                                                            from_logits=True)
     wh_loss = object_mask * box_loss_scale * 0.5 * K.square(raw_true_wh - raw_pred[..., 2:4])
     confidence_loss = object_mask * K.binary_crossentropy(object_mask, raw_pred[..., 4:5], from_logits=True) + \
                               (1 - object_mask) * K.binary_crossentropy(object_mask, raw_pred[..., 4:5],
                                                                         from_logits=True) * ignore_mask
     class_loss = object_mask * K.binary_crossentropy(true_class_probs, raw_pred[..., 5:], from_logits=True)
     
     xy_loss = K.sum(xy_loss) / mf
     wh_loss = K.sum(wh_loss) / mf
     confidence_loss = K.sum(confidence_loss) / mf
     class_loss = K.sum(class_loss) / mf
     loss += xy_loss + wh_loss + confidence_loss + class_loss
     
     ```

   - 以上是一段keras框架描述的yolo v3 的loss_function代码。忽略恒定系数不看，可以从上述代码看出：除了w, h的损失函数依然采用总方误差之外，其他部分的损失函数用的是二值交叉熵。最后加到一起。

     

## 代码架构

cfg文件夹：用于存储配置文件

data文件夹：存储class-name文件

images文件夹：存储推理用的图片

weights文件夹：存储模型权重

darknet.py：YOLOv3网络脚本

utils.py：包含代码调用的函数

main.py：代码入口



## 安装依赖

python = 3.7.4

opencv = 4.1.1.26

matplotlib = 3.1.1

pytorch = 1.3.0

numpy = 1.16



## 使用说明

1. 修改配置文件

   ```
   cfg_file = './cfg/yolov3.cfg'
   ```

2. 修改模型权重

   ```
   weight_file = './weights/yolov3.weights'
   ```

3. 修改相应的class_names，按ID顺序对应，并修改程序

   ```
   namesfile = 'data/coco.names'
   ```

4. 测试推理图片

   ```
   img = cv2.imread('./images/20200111141620_8441.jpg')
   ```



## 参考

1. 一文看懂YOLO v3

   https://blog.csdn.net/litt1e/article/details/88907542

2. YOLO: Real-Time Object Detection

   https://pjreddie.com/darknet/yolo/

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)