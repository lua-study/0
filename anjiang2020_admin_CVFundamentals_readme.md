# CVFundamentals
  - computer vision fundamentals 
  - gitee:https://gitee.com/anjiang2020_admin/CVFundamentals
  - week1 
```
CV核心基础WEEK1 :  基本图像处理
https://gitee.com/anjiang2020_admin/CVFundamentals
Pipeline:
0.职业规划
1.Computer Vision 的由来
2.计算机如何看到图像
3.计算机处理图像的方式，方法

作业：
   1 用滤波操作给图片去除噪声，
     选做：将自己的logo水印打到经过滤波后的照片上。
   目的：感受滤波操作的作用，用数字上的滤波操作模拟老照片真实镜头的滤波功能。
   参考步骤：
   1 拿到老师给定的图片：week1/week1_homework.png。
   2 对图片进行滤波操作。参考week1/week1_class_code_after_class.py
   3 修改滤波核的数值和滤波核的大小，调整出最好的效果。
   4 制作自己的logo水印的照片
   5 将水印添加到图片上。参考week1/week1_class_code_after_class.py
```
  - week2
```
 CV核心基础WEEK2 ：认识计算机视觉
 Pipeline:
 1.    图像处理与计算机视觉
 2.    计算机视觉的输入与输出
 3.    如何解决计算机视觉的几个问题
 4.    计算机视觉第一步：图像描述子

 作业：
  
  编写计算机视觉的第0版程序。
  步骤
  1 生成10张图片，对应0,1,2,3,4,5,6,7,8,9.
  2 对这10张图片提取特征x。
  3 用一个判别器f(x)来决策输出结果y。
    这个判别器达到作用：
    当x是 “0”图片对应的特征时，y=f(x)=0
    当x是 “1”图片对应的特征时，y=f(x)=1
    当x是 “2”图片对应的特征时，y=f(x)=2
    当x是 “3”图片对应的特征时，y=f(x)=3
    当x是 “4”图片对应的特征时，y=f(x)=4
    当x是 “5”图片对应的特征时，y=f(x)=5
    当x是 “6”图片对应的特征时，y=f(x)=6
    当x是 “7”图片对应的特征时，y=f(x)=7
    当x是 “8”图片对应的特征时，y=f(x)=8
    当x是 “9”图片对应的特征时，y=f(x)=9
 4 参考代码:week2/recognize_computer_vision.py
```

   - week3[github:https://github.com/anjiang2016/CVFundamentals]
```
CV核心基础WEEK3 ：经典机器学习（一）
Pipeline:
1    监督学习与非监督学习
2    第一个可训练的监督学习模型：线性回归模型的3类解法
3    使用线性模型，解决字符分类问题
4    逻辑回归模型


作业：
编写计算机视觉的第1版程序：用线性回归模型，解决数字图片分类问题，
要求：用pytorch 的auto_grad功能。

步骤：
  1 生成10张图片，对应0,1,2,3,4,5,6,7,8,9.
  2 对这10张图片提取特征x。
  3 用一个线性判别器f(x)来决策输出结果y。
  4 判别器的训练要使用梯度下降法，写代码的时候要用到pytorch 的auto_grad功能。
 达到作用：
    当x是 “0”图片对应的特征时，y=f(x)=0
    ...
    当x是 “9”图片对应的特征时，y=f(x)=9
可参考代码：
  /week3/recognize_computer_vision_linear_model.py,线性模型解决图片识别问题课程代码
  /week3/how_to_use_auto_grad.py,测试pytorch auto_grad使用方法
  /week3/data_display.ipynb 数据显示
  /week3/week2作业答案课堂讲解.ipynb
  /week3/auto_grad使用时的注意事项.ipynb
  /week3/auto_grad形式的梯度下降.ipynb
  /week3/running_jupyter.pdf,jupyter运行命令
  jupyter常用效率快捷键：https://zhuanlan.zhihu.com/p/143919082
```
   - week4[github:https://github.com/anjiang2016/CVFundamentals]
```
CV核心基础WEEK4 ：经典机器学习（二）
Pipeline:
1    线性模型的局限性，以及改进方法 
2    用二分类来进行多分类：感知机
3    用逻辑回归进行多分类
4    神经网络：反向传播网络
5    【遗留】 欠拟合，过拟合与正则化
6    【遗留】 支持向量机SVM推导


作业：
已经刷爆hct66 dataset，这周就开始mnist数据集的挑战；
编写计算机视觉的的第2版程序：用3层反向传播网络来训练mnist中的100张图片。
要求：
   1 使用pytorch的auto_grad功能来编写
   2 要求随着epoch的增加，给出训练的准确度acc,和测试的准确度acc
步骤：
  1 下载并调用mnist数据集：https://github.com/anjiang2016/CVFundamentals/blob/master/week4/mnist/readme.md
  2 对mnist中的数据提取特征x。投影法可以用，但是效果不好，可以尝试用opencv 提取hog/lbp等特征
  3 用反向传播网络来决策输出结果y。
  4 反向传播网络的训练要使用梯度下降法，写代码的时候要用到pytorch 的auto_grad功能。
 期望达到精度：
    训练精度:60%
    测试精度:60%
可参考代码：
  /week4/assignment_week03_answer.py: week3作业参考答案
  /week4/recognize_computer_vision_nonlinear_model.py:用非线性模型来识别数字
  /week4/use_2class_on_multiclass.py:在htc66数据集上使用二分类进行多分类
  /week4/use_2class_on_multiclass_sigmoid.py:在htc66数据集上使用逻辑回归二分类进行多分类：w
  /week4/mnist/readme.md:mnist数据下载，读取，显示代码
  /week4/mnist_use_2class_on_multicalss.py:在mnist上使用二分类进行多分类
  /week4/mnist_bp.py:精度不好得一版bp代码
  /week4/homework_dataset: hct1000数据集【选用】
```
   - week5[https://gitee.com/anjiang2020_admin/CVFundamentals/blob/master/README.md]
```
CV核心基础WEEK5 ：经典机器学习（三）
Pipeline:
5(week4遗留）欠拟合，过拟合与正则化
1    决策树中的Decision Tree,ID3,C4.5,CART 
2    无导师学习中的kmeans++

作业：
必做：使用kmeans++ 对hct66数据集聚三类
可选：使用kmeans++ 对mnist数据集聚10类，查看聚类效果。
要求：
   1 编写名字为keamspp.py的代码，实现hct66数据集三聚类。 
步骤：
  0 数据集hct66.py，可以用from hct66 import * 的方式使用
  1 先编写kmeans代码：kmeans.py，观察kmeans的结果
  2 在kmeans.py的基础上，将kmeans的算法的初始化部分做优化，按照kmeas++的理论思路进行编写
注意：kmeans原理比较清晰，没有提供参考例子，是首次需要大家把算法从原理落地到实际代码，意义非凡。自己编写的过程中，会遇到一些原理细节上实现问题，有的需要用近似得方法实现。不确定的地方要及时的提出来。

课程同步参考代码：
week5/__init__.py
week5/assignment04_code.py:week4参考作业
week5/decision_tree.py: 手动实现得决策树代码，可以看到决策树实现细节
week5/desition_tree.py: 编写decision_tree.py 的中间文件
week5/desition_tree_number.py :中间文件
week5/dt_for_num.py :临时中间文件
week5/dt_sk.py:使用sklearn库，调用数据集iris，并调用决策树工具包，实现分类。然后汇出决策树的图
week5/dt_sk_hct66.py:在hct66数据集上使用sklearn进行分类
week5/dt_sk_regressor.py :使用sklearn进行连续值预测（回归）
week5/dt_sk_regressor1.py:
week5/hct66.py :数据集hct66
week5/landmark_xgboost.py : 使用工具包xgboost完成简单人脸关键点回归
week5/load_mnist_use_xgboost.py: 使用xgboost实现mnist数据集的分类
```
  - week6 [http://yann.lecun.com/exdb/lenet/]
```
[gitee:https://gitee.com/anjiang2020_admin/CVFundamentals/tree/一期]
CV核心基础WEEK6 ：神经网络的卷积化
Pipeline:
1    对客观世界的建模：卷积 
2    从感知机到卷积神经网络 
3    CNN:统一了题特征+决策
4。  如何加速CNN

作业：完成week6/mnist_lenet_homework.py代码的填空，采用Lenet结构的CNN对mnist数据集进行分类训练，并测试

要求：
   1 用pytorch中的nn来实现
   2 采用Lenet结构复现出结果
步骤：
  对week6/mnist_lenet_homework.py填空
  1 89行 完成lenet网络中的C1:第一个卷积层得声明
  2 94行 填入lenet网络中的C3:第二个卷积层得声明
  3 99行 填入lenet网络中的C5:第三个卷积层得声明
  4 25-29行 完成lenet的前向计算过程
  5 运行办法：python week6/mnist_lenet_homework.py 0.00001
其它参考代码：
  1 数据集mnist：参考代码:week6/conv.py 32行
  2 卷积层用nn.conv2d来实现，相关参考代码：week6/conv.py
  3 卷积的声明，更改默认weight，默认bias,对图片进行卷积，示例子代码在：week6/conv.py 的14行,27行,29行,55行
  4 图像滤波器：filter.py
  5 kmeans++资料：kmeans++.pdf
  6 kmeans参考代码1:kmeansAndkmeansPP.py
  7 kmeans参考代码2:kmeans_and_kmeansPlusPlus.py
```
  - week7 [alexnet]
```
[gitee:https://gitee.com/anjiang2020_admin/CVFundamentals/tree/一期]
CV核心基础WEEK7 ：Lenet之后的CNN优化之路
Pipeline:
1    关于优化方向的探讨
2    看看经典模型是如何做的 

作业：完成week7/week7_homework_mnist_alexnet.py代码的填空，主要为熟悉alexnet的网络结构，并掌握flops和参数量的计算方法。

要求：
   1 实现alexnet网络的正向计算过程
   2 实现参数量计算函数:print_params_num
   3 实现计算量flops计算函数:get_flops
步骤：
  对week7/week7_homework_mnist_alexnet.py填空
  1 184-209行 完成alexnet网络结构的构建
  2 162行完成一个层参数量的计算，注意区分卷积层与全连接层
  3 25行完成一个层的flops计算。
  5 运行办法：python week7/week7_homework_mnist_alexnet.py 0.00001
其它参考材料：
  1 week7/初探alexnet网络结构.pdf
  2 week7/Alexnet-imagenet2012.pdf
  3 conv2d的参数意义以及写法参考：week6/conv.py
  4 conv,pool 函数说明：week7/pytorch_api_conv_pool.pdf
```
  - week8 [梯度下降算法一网打尽]
```
[gitee:https://gitee.com/anjiang2020_admin/CVFundamentals/tree/一期]
CV核心基础WEEK8 ：Lenet之后的CNN优化之路（二）
Pipeline:
1  BGD/SGC/mini-batch GD
2  momentum/NAG
3  Ada-grad/RMS-Prop/Ada-delta
4  Ada-m

作业：比较几种optim方法：momentum,Adagrad,RMSRrop,Adadelta,Adam

要求：
   1 使用pytorch函数调用一上优化方法/或者自己按照原理实现
   2 要求，打印出loss,top1 acc，epoch，制作曲线进行比较，横轴eposh,纵轴loss&top1 acc
   3 数据使用 cifar10 dataset
建议步骤：
  1 Common_gradient_optimization_algorithms.py有比较完整的工程训练代码。
  2 参考Common_gradient_optimazation_algorithms.py 写出所需要的optim方法
  3 自己完成loss,top1_acc,epoch的记录并用matplotlib绘图

其它参考材料：
  1. 优化算法原理参考：An_overview_of_gradient_descent_optimization_algorithms.pdf
  2. 优化算法torch代码实现：torch.optm使用办法.pdf
  3. week7作业参考：week7_homework_mnist_alexnet_answer.py
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)