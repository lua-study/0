# 学习fastai而进行的项目学习
+ [数字图像识别](https://www.lintcode.com/ai/digit-recognition/data)

---

+ 手写数字生成任务  
**原始数据**
![](./digital_gan/original_examples.png)  

**自带wgan生成的数据**
![](./digital_gan/bad_examples.png)  

**预训练对抗生成结果**
![](./digital_gan/maybe_good.png)  

表现很差的原因在于，我们预训练的生成器，是直接使用的上一步wgan的生成器，此生成器效果并没有那么好。  
现在改进一下，直接对生成器做一个预训练，然后模型效果如下图所示：

![](./digital_gan/good.png)  

可以看到生成的效果已经非常不错了 此项目到底结束

---

+ 结合pyg用于分类任务  
目的：将fastai与pyg相结合

数据长这个样子
![](./pyg/pyg_show_batch.png)

数据预测长这个样子

![](./pyg/预测结果.png)


---
# kaggle 文本二分类问题
使用很简单的fastai + 调参后的结果。  
学习到了很有趣的经验：  **wd是很重要的参数**

![](./real_or_not_NLP_with_Disater_Tweets/rank.png)

---
# 图片序列预测问题
+ 使用ConvLSTM 来进行图片序列预测

![](./digital_movment/9_pred_9.png)

+ 使用ConvLSTM 来进行气象预测

![](./qixiangyuce/气象预测.png)
> 从中获得一个经验，对回归问题而言，对标签进行归一化能够使损失更为平滑，下降更快。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)