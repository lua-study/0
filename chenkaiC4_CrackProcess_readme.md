# CrackProcess

#### 项目介绍
水泥表面图片的裂缝检测和测量

#### 软件架构
1. CrackProcess.h 外部调用接口定义
2. CrackProcess.cpp 算法的实现部分
3. Utilities.h Utilities.cpp 辅助函数，包括骨架提取、连通域检测等

#### CrackProcess中函数功能说明
1. FindCracks 检测裂缝
2. Filter 滤波
3. MeasureCracks 测量
4. Stitcher 拼接图片

#### Utilities中函数功能说明
1. addContrast 增加对比度
2. findConnectedDomain 检测连通域，并删除不符合条件的连通域
3. thinImage 提取连通域的骨架
4. swapMat 交换两个Mat
5. save2PNG 将图像以PNG格式保存
6. binaryzation 二值化图像。0->0,非0->255
7. getWhitePoints 获取图像中白点的数量
8. calInfoPosition 计算宽高信息的放置位置

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)