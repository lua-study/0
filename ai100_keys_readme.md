#《人工智能工程师》- 重难点提示

# 公共课

## 第一周

### 第一章 计算机视觉引论：你好，视觉世界！

#### 什么是计算机视觉

- 计算机视觉的概念
- 计算机视觉发展以及应用趋势

#### 构建第一个视觉程序

- 介绍win10+vs+opencv环境搭建
- 运行视觉HelloWorld程序-lena图像

#### 视觉系统构成

- 视觉系统的构成要素：光源、成像、主机、软件处理
- 对一些典型应用系统构成进行分析

#### 让程序做点事情

- 在HelloWorld基础上增加一些基本图像处理操作：改变大小、平滑、阈值化

#### 课程体系结构

- 视觉计算理论架构
- 计算机视觉研究发展
- 课程架构以及组织形

### 第二章 数字成像系统

#### 照明模型

- **光通量和辐照度的概念-重点**
- 常见光源种类和特点

#### 颜色模型

- RGB和CMKY颜色模型
- **颜色空间概念和HSI颜色空间模型-重点**
- 颜色空间变换的opencv实现

#### 图像的采集与传输

- **图像传感器的基本原理-重点：CCD传感器、Bayer格式**
- 图像的伽马矫正：人眼视觉和照明的非线形关系
- 图像传输的常见方式：模拟、数字传输，RGB方式

#### 图像/视频的压缩与显示

- 常用的图像和视频压缩标准：JPEG、MPEG及变种
- 显卡和显示器的主要参数：显存、流处理器、位数；分辨率、亮度对比度等

## 第二周

### 第一章 视觉处理算法基础

#### 图像的滤波与去噪

- 了解图像滤波基本原理
- **基本图像预处理方法-重点**
- 数学形态学滤波

#### 图像的边缘检测

- 了解边缘检测基本思想
- **基本边缘检测算子-重点**
- **熟悉Canny算子的基本思想及实现步骤-难点**

#### 直方图与图像分割

- 掌握直方图的基本概念
- **掌握大津算法的基本思想及实现-重点**
- 了解区域生长法的基本思想及实现步骤

#### 图像特征描述

- 掌握图像特征的简单描述指标
- 掌握最小包围矩形及D-P多边形拟合方法
- 了解图像不变矩

#### 再论图像分割

- 了解图像分割方法的分类和发展
- 掌握局部阈值法分割的基本思想
- **掌握分水岭算法的基本思想-难点**
- 了解基于边缘的分割方法及OpenCV实现

#### 综合示例

- 了解视觉算法的基本开发步骤
- **掌握使用OpenCV完成图像分割及区域描述-重点**

### 第二章 视觉特征提取

#### 直线检测

- **掌握Hough变换的基本思想-难点**
- 掌握OpenCV的Hough变换实现

#### Harris角点检测

- 掌握角点的直观意义
- 掌握Harris角点检测的基本思想

#### SIFT特征提取

- 了解SIFT变换的整体思路
- **掌握图像的尺度空间思想-重点**
- 了解SIFT特征检测的计算过程

#### ORB特征检测

- 了解ORB的基本原理
- 了解FAST基本思想及rFAST改进
- 了解BRIEF基本思想及oBRIEF改进

#### 特征检测综合示例

- 学习Harris角点检测示例
- 掌握使用角点检测和匹配的一般流程
- 掌握SURF和ORB角点检测的实现

## 第三周

### 第三章 运动估计

#### 背景建模

- 了解基于背景提取的运动估计的基本思想
- **掌握混合高斯模型及迭代计算方法-重点-难点**

#### 光流估计

- 掌握光流估计的基本模型
- 掌握L-K光流估计方法

#### 视觉运动估计综合示例

- 使用OpenCV完成基于背景提取的运动估计
- 使用OpenCV完成光流估计

#### 视觉编程工具

- 介绍OpenCV和Visual Studio的几个常用辅助工具

# 讲师衔接 屈老师->卿老师

下周课程会介绍机器学习中最简单的模型，线性模型。

重点内容：

- 线性模型的基本形式
- 线性模型的优化方式，lasso，岭回归，特点与区别
- 初步理解并掌握模型效果评估，参数调优
- 初步理解并掌握特征工程的流程

## 第四周

### 第0章  机器学习简介，第一章  线性回归

**机器学习简介**

- 理解机器学习的定义
- 掌握机器学习任务的类型
- 理解机器学习的工作流程

**机器学习课程环境简介**

- 了解课程学习所需的工具包

**线性回归简介**

- 理解回归任务的定义
- 掌握线性回归模型
- 掌握线性回归模型的目标函数:损失函数和正则项
- 了解线性回归模型求解的优化算法
- 理解交叉验证
- 掌握用交叉验证评估模型性能
- 运用线性回归模型解决实际问题

**回归中的损失函数**

- 掌握回归模型中的损失函数:L2损失、L1损失和Huber 损失
- 理解上述损失的适用场景

**损失函数的概率解释**

- 理解回归模型的噪声模型:正态分布
- 理解极大似然估计
- 理解最小L2损失和正态分布噪声模型极大似估计的等价性

**过拟合**

- 掌握机器学习中过拟合的概念
- 掌握抑制过拟合的方法

**Scikit-Learn中带正则的线性回归模型**

- 掌握带正则项的线性回归模型
- 掌握Scikit-Learn中的线性回归模型:LinearRegression, Ridge, Lasso, ElasticNet

**正则的概率解释**

- 了解正则的概率解释
- 了解带正则的回归等价于贝叶斯估计

**线性回归模型解析求解**

- 理解OLS和岭回归的解析求解

**线性回归模型优化求解之梯度下降法**

- 理解梯度下降法
- 理解随机梯度下降法
- 掌握OLS和岭回归的梯度下降法求解

**线性回归优化求解之坐标轴下降法**

- 理解次梯度概念
- 理解坐标轴下降法
- 掌握Lasso坐标轴下降法求解
- 理解为什么Lasso能得到稀疏解

**回归模型预测性能评价指标**

- 理解回归模型预测性能的评价指标

**交叉验证与模型选择**

- 理解验证集的概念和作用
- 掌握交叉验证用于模型选择/超参数调优

## 第五周

### 第二章  Logistic回归

**Logistic回归简介**

- 理解分类任务定义
- 掌握Logistic回归模型的定义
- 理解Logistic回归模型的目标函数
- 了解Logistic回归模型求解的优化算法
- 掌握用交叉验证评估Logistic回归模型性能
- 运用Logistic回归模型解决实际问题2. 

**Logistic回归之损失函数**

- 理解替代损失函数
- 掌握Logistic回归模型的负log似然损失/交叉熵损失

**Logistic回归之正则项**

- 掌握Logistic回归模型的目标函数:损失函数+正则项

**牛顿法**

- 了解牛顿法及拟牛顿法

**Logistic回归之优化求解**

- 理解Logistic回归参数求解方法

**Logistic回归之多类分类**

- 掌握Logistic回归多类分类器:Softmax分类器

**类别样本不均衡**

- 理解分类任务中类别样本不均衡的处理方法

**分类模型的性能评价指标**

- 理解分类模型预测性能的评价指标
- 掌握Scikit-Learn中的分类模型预测性能的评价指标

**Scikit-Learn中的Logistic回归模型实现**

- 掌握Scikit-Learn中Logistic回归分类器的调用接口

# 讲师衔接 卿老师->孙老师

下周将会介绍神经网络的起源及发展简史。深度神经网络的前身感知器，其特点和局限。同时针对感知器的种种局限，新的激活函数，以及全连接神经网络的出现。

重点内容：

- 全连接 神经网络的前向计算和反向传播，公式推导一定要掌握，面试必考



## 第六周

### 第一章 深度学习入门

#### 深度学习起源和发展

- 了解深度学习的収展历史

####  深度学习解决的问题

- 理解非结构化数据的定义
- 了解深度学习对非结构化数据的自动特征提取
- 了解深度学习研究的细分领域

#### 感知器介绍

- **掌握感知器的定义、前馈计算和学习规则-重点**
- 了解感知器的实际运用
- 理解多层感知机的概念

#### 神经网络的拟合能力

- 理解神经网络与感知机的区别
- 掌握基本的神经网络激活函数

#### 全连接神经网络介绍

- 了解全连接神经网络
- 理解全连接神经网络的基本结构

#### 前向传播

- 掌握神经网络前向传播的概念与计算

#### 反向传播

- 掌握神经网络的反向传播算法
- **通过学习能够手推反向传播-重点**



## 第七周

### 第一章 深度学习基础，第二章 深度学习网络结构，第三章 深度学习训练与优化，第一章  tensorflow基础

#### 整体介绍

- 了解深度学习标准结构

#### 数据预处理

- 掌握常用数据的预处理方法

#### 神经网络

- 理解神经网络与感知器的区别
- 掌握神经网络的常见激活函数

#### 激活函数

- 掌握与激活函数性质有关的一些概念
- **掌握常见激活函数的数学表达式、性质以及优缺点-重点-难点**
- 了解一些新的激活函数

#### Batch Normalization

- 理解Batch Normalization的目的、思路和具体的做法

#### Dropout

- 理解Ｄropout的目的、思路和具体做法

#### 网络连接方式

- **掌握神经网络的全连接方式-重点**
- **理解神经网络的卷积连接方式-重点-难点**
- **理解神经网络的循环连接方式-重点-难点**

#### 输出层与ground truth

- **掌握神经网络输出层在分类和回归任务中的形式-重点-难点**

- 掌握ground truth的含义及作用

#### 损失函数

- **熟练掌握交叉熵损失函数-重点**
- 理解其他改进的损失函数

#### 学习率

- 掌握学习率的概念，以及学习率衰减的原因与策略

#### 神经网络的优化算法

- 掌握神经网络的各种优化算法
- 理解优化算法的计算过程

#### 过拟合与欠拟合

- 掌握欠拟合和过拟合的概念以及产生原因
- 了解欠拟合和过拟合的解决方法

#### 正则化

- 掌握正则化的概念

#### 参数的初始化

- 掌握权重的初始化方法

#### tensorflow基础

- 了解tensorflow的安装和使用


# 讲师衔接 孙老师->卿老师，屈老师



卿老师内容：

SVM相关的内容非常重要，作为上一个人工智能时代的遗产，SVM的思想仍然对目前人工智能的发展有着深远的影响。

重点内容：

- SVM的LargeMargin思想
- SVM核化方法
- Scikit-Learn中的SVM使用实例



屈老师内容:

xxxxx

# 推荐系统方向



## 第一周

### 第一章SVM，决策树 

**SVM简介**

- 理解线性SVM分类原理
- 理解核方法
- 掌握核化SVM模型原理
- 理解SVM回归(SVR)
- 运用SVM模型解决实际问题

**带松弛变量的SVM:C-SVM**

- 理解松弛变量概念
- 掌握带松弛变量的SVM:C-SVM分类模型
- 理解合页损失

**SVM之对偶问题**

- 了解拉格朗日乘子法的对偶性
- 了解KKT条件
- 理解SVM的对偶问题
- 理解SVM中支持向量的概念及支持向量的稀疏性

**SVM之核方法**

- 了解核技巧
- 了解核函数
- 掌握非线性核在SVM中的应用

**SVM之回归:SVR**

- 理解$\epsilon​$不敏感损失函数
- 掌握支持向量回归模型:SVR

**Scikit-Learn中的SVM实现**

- 掌握Scikit-Learn中SVM的调用接口第二周

## 第二周

### 第三章 集成机器学习

**Bagging和随机森林1**

- 理解误差的偏差-方差分解
- 理解Bagging集成学习思想
- 掌握随机森林模型的原理

**Scikit-Learn中的随机森林模型**

- 掌握Scikit-Learn中随机森林模型的调用接口

**Adaboost**

- 理解AdaBoost模型的原理

**GBM**

- 理解Gradient Boosting思想

**Scikit-Learn中的GBM**

- 了解Scikit-Learn中GBDT模型的调用接口

**XGBoost原理**

- 理解XGBoost的基本原理

**XGBoost工具包使用指南**

- 掌握XGBoost的调用接口

**XGBoost的Scikit-Learn接口**

- 掌握XGBoost的Scikit-Learn接口

**LightGBM原理**

- 理解LightGBM对GBM的快速实现原理

**LightGBM使用指南1**

- 掌握LightGBM的调用接口

## 第三周

### 第四章  非监督学习

**PCA降维原理**

- 理解PCA原理

**Scikit-Learn中的PCA**

- 掌握Scikit-Learn中的PCA接口

**t-SNE**

- 理解t-NSE的原理

**Scikit-Learn中的 t-SNE**

- 掌握Scikit-Learn中的t-NSE的接口

**聚类简介**

- 理解聚类的基本思想
- 理解聚类算法的评价指标

**KMean聚类算法**

- 理解K-Means聚类原理

**Scikit-Learn中的 KMean聚类**

- 掌握Scikit-Learn中的K-Means聚类接口

## 第四周
### 第五章  推荐系统

**推荐系统简介**

- 了解推荐系统应用场景
- 了解推荐算法的类别
- 了解推荐系统的评价指标

**基于内容的推荐**

- 理解基于内容的推荐的基本原理

**基于用户的协同过滤**

- 理解基于用户的协同过滤的原理

**基于物品的协同过滤**

- 理解基于物品协同过滤的原理

**基于矩阵分解的协同过滤**

- 理解基于矩阵分解的协同过滤的原理

## 第五周
### 第五章  推荐系统

**CTR预估简介**

- 了解CTR估计的应用场景
- 了解CTR预估任务的特点

**FTRL模型**

- 了解FTRL的优化原理

**FM与FFM**

- 理解FM和FFM的原理

**GBDT**

- 理解GBDT用于特征组合的原理

**Wide and Deep Learning模型**

- 理解Wide and Deep Learning模型的原理



# 视觉方向

## 第一周

### 第一章 位姿估计

#### 坐标系与相机模型

- 常用的图像变换模型
- 计算机视觉中常用的坐标系与坐标变换
- 线性及非线形摄像机模型

#### 相对位姿测量算法

- **基于空间多点的相对位姿测量算法-重点-难点**
- 基于平面多特征点点相对位姿测量算法

#### 相机标定

- 相机内参数矩阵标定的基本思想
- 相机参数标定的Zhang方法及标定步骤

## 第二周

### 第二章 极线几何与立体视觉

#### 极线几何

- 极线几何的基本概念
- **本质矩阵的基本概念及几何意义-重点-难点**
- 根据点对应求解本质矩阵及相对位姿

#### 立体视觉与三维重构

- 立体视觉的基本概念及空间点坐标计算方法
- 三维重构的基本步骤

#### 特征匹配

- 特征匹配基本问题及应用
- **基于k-d树的特征匹配方法-重点-难点**
- RANSAC基本思路及应用

# 讲师衔接 屈老师->孙老师

下周将会进入最近这些年比较火热的深度学习重要领域，卷积神经网络的学习。

下周内容重点：

- 卷积的计算方式，特点，这个部分是面试的时候经常会问到的。

- 卷积网络的代码实现案例，需要仔细看，tensorflow中卷积是如何实现的，同时，模型训练，保存的流程等等。



## 第三周

### 第一章 卷积神经网络

#### 介绍

- 了解卷积神经网络在人工智能领域的发展，优势；

- 掌握卷积神经网络前向传播及反向传播公式及计算方法。

#### 卷积和池化

- 掌握卷积的概念和特点
- **掌握卷积的计算-重点**
- 掌握池化的计算
- 掌握卷积和池化在模型中组合的效果

#### 卷积的反向传播

- **了解卷积的反向传播算法-难点**

#### tensorflow基础

- 了解tensorflow中卷积的四种写法

#### 卷积神经网络的tensorflow实现

- 了解tensorflow的使用
- 了解卷积神经网络的训练





## 第四周

### 第二章 卷积神经网络案例

#### 经典卷积神经网络案例

- 了解几种经典的卷积神经网络结构
- **了解各种常见结构的优缺点-重点-难点**
- **掌握论文网络结构表的解读-重点**
- **了解se-net，MobileNetV1/V2-重点**
- 掌握几种已经被证明有效的模块

#### VggInception网络代码讲解

- 了解tensorflow的使用
- 了解较复杂的神经网络的代码实现

#### 基于slim的神经网络模型训练

- 了解slim及其使用
- 掌握一个神经网络训练的流程
- 掌握预训练模型的使用
- 了解训练完的模型的使用

## 第五周

### 第三章 卷积神经网络应用

#### 分类定位

- 了解卷积神经网络的几种应用实例
- **掌握一些典型任务的业务网络设计-重点**

#### 检测

- 了解检测网络的发展历史
- **掌握几种典型的检测网络-重点**
- 了解各种检测的思路

#### 检测模型的训练与使用

- 了解slim中的目标检测模型
- **了解检测模型的训练和使用-重点-难点**

#### 分割

- 了解像素级图像分割
- **掌握FCN网络-重点-难点**
- 了解几种比较先进的分割网络

#### 人脸

- 了解人脸检测的任务内容
- **了解人脸检测与普通目标检测的相同点与区别-重点**
- 了解几种在人脸检测领域发展起来的损失函数

#### 其他

- 了解深度神经网络的一些应用

#### 特征使用

- 了解网络输出的特征

- **掌握特征的距离计算方式-重点**

#### 业务网络设计

- 了解业务网络设计的一些套路



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)