# 四位验证码CNN识别

## 1.参考
[1] [街道多位数字CNN识别，神经网络架构参考](https://github.com/potterhsu/SVHNClassifier)

[2] [关于CNN的详细解释，深度学习入门必备](https://morvanzhou.github.io/tutorials/machine-learning/tensorflow/5-03-CNN1/)


[3] [验证码生成参考类](http://git.oschina.net/thinkgem/jeesite/blob/master/src/main/java/com/thinkgem/jeesite/common/servlet/ValidateCodeServlet.java)

## 2.支持
[1] Python3.6.1 or >=3.5

[2] TensorFlow 1.2

[3] numpy

[4] cv2

## 3.简介
通过训练CNN（卷积神经网络）对4位验证码识别，其中字符有0-9a-zA-Z共计62种，但是预测结果不区分大小写，所以最终预测结果为36种。验证码由多个字体、颜色、干扰线随机生成。

## 4.项目结构
[1] 整体结构
>model.py 整个神经网络结构

>code_utils.py 将字符转换为一维数组以及一维数组转换为字符的工具类

>image_utils.py 读取图片，处理图片数据的工具类

>app.py 主程序类，其中包括参数设置以及整个神经网络训练流程控制

>test.py 提取大量的测试label测试神经网络的最终效果

>model 存放神经网络参数写入的文件夹

[2] 以下为缺少文件夹：

>test-images 所有测试验证码图片在这个文件夹

>train-images 所有训练验证码图片在这个文件夹

>`如果你需要这些数据请告诉我`

## 5.结果

以下是对100万张训练验证码进行训练，20万张不参与训练的测试验证码测试出的结果

一般的验证码系统都会去掉类似的字符（例如：i, l, o, 1, 0...），为了更全面的测试，所以我选择将这些难以识别的字符也添加进去测试，可以看出有这些难以辨别的字符时，连人类也很难去完全预测正确（下图，第一行为预测值，第二行为真实值）

![](http://git.oschina.net/kdldbq/verification-decoder/raw/master/result/train_1w.jpg)

### 训练60万次时的结果：

![](http://git.oschina.net/kdldbq/verification-decoder/raw/master/result/60w_loss.png)

![](http://git.oschina.net/kdldbq/verification-decoder/raw/master/result/60w_output.png)

```
最终结果： 四个字符同时正确率: 90.02%		单个字符正确率: 97.42%
```

*说明：本项目仅用于学习，勿用于网络攻击及验证码暴力破解

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)