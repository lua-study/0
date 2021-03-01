# DeepNude-an-Image-to-Image-technology

![](paper_images/image2image_logo.png)

This repository contains the core algorithms of DeepNude, and more importantly, the general Image-to-Image theory and practice behind DeepNude.

这个仓库包含DeepNude的核心算法，更重要的是DeepNude背后的通用的Image-to-Image理论与实践研究。

## What is DeepNude? 什么是 DeepNude?
DeepNude uses a slightly modified version of the [pix2pixHD](https://github.com/NVIDIA/pix2pixHD) GAN architecture, quoted from [deepnude_official](https://github.com/deepinstruction/deepnude_official). The pix2pixHD(proposed by NVIDIA) can be used for turning semantic label maps into photo-realistic images or synthesizing portraits from face label maps. Obviously DeepNude is the wrong application of artificial intelligence technology, but it could be useful for researchers and developers working in other fields such as fashion, cinema and visual effects.

DeepNude使用了一个稍微修改过的 [pix2pixHD](https://github.com/NVIDIA/pix2pixHD) GAN 架构，引自 [deepnude_official](https://github.com/deepinstruction/deepnude_official)。 pix2pixHD（由NVIDIA提出）可用于将语义图（语义图是一幅不同色块代表不同物体的图片）转换为逼真的图像或合成肖像。显然，DeepNude是人工智能技术的错误应用，但它对于在时尚，电影和视觉效果等其他领域工作的研究人员和开发人员非常有用。

---

## Content of this resource 本资源内容

|English|中文|
|-|-|
|What is DeepNude?|什么是 DeepNude?|
|Image-to-Image Demo |		             试玩Demo|
|DeepNude Algorithm|               DeepNude算法|
|Image-to-Image Theoretical Research|  理论研究|
|Image-to-Image Practice Research|     实践研究|
|Future|					                     展望未来|

---

## Image-to-Image Demo
This section provides a demo of Image-to-Image Demo: Black and white stick figures to colorful cats, shoes, handbags. DeepNude software mainly uses Image-to-Image technology, which theoretically converts the images you enter into any image you want. You can experience Image-to-Image technology in your browser by clicking Image-to-Image Demo below.

这一部分提供一个试玩的 Image-to-Image Demo：黑白简笔画到色彩丰富的猫、鞋、手袋。DeepNude 软件主要使用了Image-to-Image技术，该技术理论上可以把你输入的图片转换成任何你想要的图片。你可以点击下方的Image-to-Image Demo在浏览器中体验Image-to-Image技术。

[Try Image-to-Image Demo](https://affinelayer.com/pixsrv/)

An example of using this demo is as follows：

![](paper_images/2017_Phillip_pix2pix_examples_edges2cats.png)

In the left side box, draw a cat as you imagine, and then click the process button, you can output a model generated cat.

在左侧框中按照自己想象画一个简笔画的猫，再点击process按钮，就能输出一个模型生成的猫。

---

## :underage: DeepNude Algorithm
> DeepNude is a pornographic software that is forbidden by minors. If you are not interested in DeepNude itself, you can skip this section and see the general Image-to-Image theory and practice in the following chapters. DeepNude 是一款含有色情的软件，未成年人禁止使用。如果你对DeepNude本身不感兴趣，可以直接跳过本节，查看后面章节中通用的Image-to-Image理论与实践研究。

|Title|Content|
|-|-|
|[DeepNude_software_itself](DeepNude_software_itself)|DeepNude software usage process and evaluation of advantages and disadvantages. DeepNude 软件的使用过程和优缺点评价。|
|[Official DeepNude Algorithm(Based on Pytorch)](https://github.com/deepinstruction/deepnude_official)|官方版本DeepNude算法（基于Pytorch）|
|DeepNude Algorithm(Based on TensorFlow 2)|Under development|

---

## Image-to-Image Theoretical Research

This section describes DeepNude-related AI/Deep Learning theory (especially computer vision) research. If you like to read the paper and use the latest papers, enjoy it.

这一部分阐述DeepNude相关的人工智能/深度学习理论（特别是计算机视觉）研究，如果你喜欢阅读论文使用最新论文成果，尽情享用吧。

### 1. Pix2Pix

+ 论文 Berkeley 2017 paper [Image-to-Image Translation with Conditional Adversarial Networks](https://arxiv.org/abs/1611.07004)
+ 主页 [Pix2Pix homepage](https://phillipi.github.io/pix2pix/)
+ 代码 code [pix2pix](https://github.com/phillipi/pix2pix)
+ Run in Google Colab [pix2pix.ipynb](https://github.com/tensorflow/docs/blob/master/site/en/r2/tutorials/generative/pix2pix.ipynb)

**效果**

![](paper_images/2017_Phillip_pix2pix_examples.jpg)

[Image-to-Image Translation with Conditional Adversarial Networks](https://arxiv.org/abs/1611.07004) is a general solution for the use of conditional confrontation networks as an image-to-image conversion problem proposed by the University of Berkeley.

[Image-to-Image Translation with Conditional Adversarial Networks](https://arxiv.org/abs/1611.07004) 是伯克利大学研究提出的使用条件对抗网络作为图像到图像转换问题的通用解决方案。

### 2. Pix2PixHD
> DeepNude mainly uses this Image-to-Image(Pix2PixHD) technology.

+ 论文 NVIDIA 2018 [High-Resolution Image Synthesis and Semantic Manipulation with Conditional GANs](https://arxiv.org/abs/1711.11585)
+ 主页 [Pix2PixHD homepage](https://tcwang0509.github.io/pix2pixHD/)
+ 代码 code [pix2pixHD](https://github.com/NVIDIA/pix2pixHD)

**效果**

![](paper_images/2018_NVIDIA_Pix2PixHD_example.png)
![](paper_images/2018_NVIDIA_Pix2PixHD_example_2.png)

Get high resolution images from the semantic map. The semantic graph is a color picture. The different color blocks on the map represent different kinds of objects, such as pedestrians, cars, traffic signs, buildings, and so on. Pix2PixHD takes a semantic map as input and produces a high-resolution, realistic image. Most of the previous techniques can only produce rough, low-resolution images that don't look real. This research has produced images with a resolution of 2k by 1k, which is very close to full HD photos.

从语义图上获得高分辨率图片。语义图是一幅彩色图片，图上的不同色块代表不同种类物体，如行人、汽车、交通标志、建筑物等。Pix2PixHD将一张语义图作为输入，并由此生成了一张高分辨率的逼真的图像。之前的技术多数只能生成粗糙的低分辨率的图片，看起来也不真实。而这个研究却生成了2k乘1k分辨率的图像，已经很接近全高清的照片。


### 3. CycleGAN

+ 论文 Berkeley 2017 paper [Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks](https://arxiv.org/abs/1703.10593)
+ 主页 [CycleGAN homepage](https://junyanz.github.io/CycleGAN/)
+ 代码 code [CycleGAN](https://github.com/junyanz/CycleGAN)
+ Run in Google Colab [cyclegan.ipynb](https://github.com/tensorflow/docs/blob/master/site/en/r2/tutorials/generative/cyclegan.ipynb)

**效果**

![](paper_images/2017_Zhu_CycleGAN_examples.jpg)

CycleGAN uses a cycle consistency loss to enable training without the need for paired data. In other words, it can translate from one domain to another without a one-to-one mapping between the source and target domain. This opens up the possibility to do a lot of interesting tasks like photo-enhancement, image colorization, style transfer, etc. All you need is the source and the target dataset.

CycleGAN使用循环一致性损失函数来实现训练，而无需配对数据。换句话说，它可以从一个域转换到另一个域，而无需在源域和目标域之间进行一对一映射。这开启了执行许多有趣任务的可能性，例如照片增强，图像着色，样式传输等。您只需要源和目标数据集。

### 4. Image Inpainting 图像修复

+ 论文 NVIDIA 2018 paper [Image Inpainting for Irregular Holes Using Partial Convolutions](https://arxiv.org/abs/1804.07723) and [Partial Convolution based Padding](https://arxiv.org/abs/1811.11718).
+ 代码 Paper code [partialconv](https://github.com/NVIDIA/partialconv)。

**效果**

![](paper_images/2018_NVIDIA_Image_Inpainting_examples.png)

In the image interface of [Image_Inpainting(NVIDIA_2018).mp4](https://github.com/yuanxiaosc/DeepNude-an-Image-to-Image-technology/raw/master/paper_images/Image_Inpainting(NVIDIA_2018).mp4) video, you only need to use tools to simply smear the unwanted content in the image. Even if the shape is very irregular, NVIDIA's model can “restore” the image with very realistic The picture fills the smeared blank. It can be described as a one-click P picture, and "no ps traces." The study was based on a team from Nvidia's Guilin Liu et al. who published a deep learning method that could edit images or reconstruct corrupted images, even if the images were worn or lost pixels. This is the current 2018 state-of-the-art approach.

在 [Image_Inpainting(NVIDIA_2018).mp4](https://github.com/yuanxiaosc/DeepNude-an-Image-to-Image-technology/raw/master/paper_images/Image_Inpainting(NVIDIA_2018).mp4) 视频中左侧的操作界面，只需用工具将图像中不需要的内容简单涂抹掉，哪怕形状很不规则，NVIDIA的模型能够将图像“复原”，用非常逼真的画面填补被涂抹的空白。可谓是一键P图，而且“毫无ps痕迹”。该研究来自Nvidia的Guilin Liu等人的团队，他们发布了一种可以编辑图像或重建已损坏图像的深度学习方法，即使图像穿了个洞或丢失了像素。这是目前2018 state-of-the-art的方法。

---

## Image-to-Image Practice Research
> More models and functions will be added in the future.

This section explains DeepNude-related AI/Deep Learning (especially computer vision) code practices, and if you like to experiment, enjoy them.

这一部分阐述DeepNude相关的人工智能/深度学习（特别是计算机视觉）代码实践，如果你喜欢动手做实验，尽情享用它们。

### 1. Pix2Pix

Use the Pix2Pix model (Conditional Adversarial Networks) to implement black and white stick figures to color graphics, flat houses to stereoscopic houses and aerial maps to maps.

使用Pix2Pix模型（Conditional Adversarial Networks）实现黑白简笔画到彩图、平面房屋到立体房屋和航拍图到地图等功能。

[Click Start Experience 1](Pix2Pix)

### 2. Pix2PixHD

Under development...

### 3. CycleGAN for Image-to-Image

The CycleGAN neural network model is used to realize the four functions of photo style conversion, photo effect enhancement, landscape season change, and object conversion.

使用CycleGAN神经网络模型实现照片风格转换、照片效果增强、照片中风景季节变换、物体转换四大功能。

[Click Start Experience 3](CycleGAN)

---

## Future

In fact, we don't need Image-to-Image. We can use [GANs](https://arxiv.org/abs/1406.2661) to generate images directly from random values or generate images from text.

### 1. [Obj-GAN](https://github.com/jamesli1618/Obj-GAN)

The new AI technology Obj-GAN developed by Microsoft Research AI understands natural language descriptions, sketches, composite images, and then refines the details based on individual words provided by sketch frames and text. In other words, the network can generate images of the same scene based on textual descriptions that describe everyday scenes.

微软人工智能研究院（Microsoft Research AI）开发的新 AI 技术Obj-GAN可以理解自然语言描述、绘制草图、合成图像，然后根据草图框架和文字提供的个别单词细化细节。换句话说，这个网络可以根据描述日常场景的文字描述生成同样场景的图像。

**效果**

![](https://raw.githubusercontent.com/jamesli1618/Obj-GAN/master/step_vis.png)

**模型**

![](https://raw.githubusercontent.com/jamesli1618/Obj-GAN/master/framework.png)


### 2. [StoryGAN](https://github.com/yitong91/StoryGAN)

[Advanced version of the pen: just one sentence, one story, you can generate a picture](https://www.microsoft.com/en-us/research/blog/a-picture-from-a-dozen-words-a-drawing-bot-for-realizing-everyday-scenes-and-even-stories/).
> Microsoft's new research proposes a new GAN, ObjGAN, which can generate complex scenes based on textual descriptions. They also proposed another GAN, StoryGAN, which can draw a story. Enter the text of a story and output the "picture book".

[进阶版神笔：只需一句话、一个故事，即可生成画面](https://www.jiqizhixin.com/articles/2019-06-29)
> 微软新研究提出新型 GAN——ObjGAN，可根据文字描述生成复杂场景。他们还提出另一个可以画故事的 GAN——StoryGAN，输入一个故事的文本，即可输出「连环画」。

当前最优的文本到图像生成模型可以基于单句描述生成逼真的鸟类图像。然而，文本到图像生成器远远不止仅对一个句子生成单个图像。给定一个多句段落，生成一系列图像，每个图像对应一个句子，完整地可视化整个故事。

**效果**

![](https://www.microsoft.com/en-us/research/uploads/prod/2019/06/drawing-bot-figure-3.png)

---

The most commonly used image-to-image technology should be Beauty App, so why don't we develop a smarter Beauty Camera?

现在用得最多的Image-to-Image技术应该就是美颜APP了，所以我们为什么不开发一个更加智能的美颜相机呢？


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)