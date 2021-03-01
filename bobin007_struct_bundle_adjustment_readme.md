# Bundle adjustment with structure

## Introduction
为了利用场景中的结构信息约束BA的优化, 我们构造了line, plane节点以及line-point, plane-point边, 利用这些边和点约束完成ba以及位姿估计等.

在优化器中如果固定点, 可以进行PoseOnly的优化, 利用3D-2D线可以提高位姿的估计精度. 

例外利用plucker坐标以及plucker矩阵, 我们构造了plucker线的节点以及pluckerline-SE3边. 将图像上的线反投影至归一化平面, 利用plucker矩阵计算线的投影误差.参见 (Přibyl B, Zemčík P, Čadík M. Camera Pose Estimation from Lines using Pl\" ucker Coordinates[J]. arXiv preprint arXiv:1608.02824, 2016.)
 
# 安装
## Prerequisites
Prerequisites needed for compiling PnPL using c++:
- OpenCV (http://opencv.org)
- g2o (https://github.com/RainerKuemmerle/g2o)


## How to run
- Linux
```
mkdir build
cd build
cmake ..
make
```




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)