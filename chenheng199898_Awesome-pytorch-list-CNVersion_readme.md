Awesome-Pytorch-list｜厉害的Pytorch项目
========================

![pytorch-logo-dark](https://raw.githubusercontent.com/pytorch/pytorch/master/docs/source/_static/img/pytorch-logo-dark.png)

## [English Version](https://github.com/bharathgs/Awesome-pytorch-list)

## Contents｜内容
- [Awesome-Pytorch-list｜厉害的Pytorch项目](#awesome-pytorch-list%EF%BD%9C%E5%8E%89%E5%AE%B3%E7%9A%84pytorch%E9%A1%B9%E7%9B%AE)
  - [English Version](#english-version)
  - [Contents｜内容](#contents%EF%BD%9C%E5%86%85%E5%AE%B9)
  - [Pytorch & related libraries｜Pytorch & 相关库](#pytorch-related-libraries%EF%BD%9Cpytorch-%E7%9B%B8%E5%85%B3%E5%BA%93)
    - [NLP & Speech Processing｜自然语言处理 & 语音处理:](#nlp-speech-processing%EF%BD%9C%E8%87%AA%E7%84%B6%E8%AF%AD%E8%A8%80%E5%A4%84%E7%90%86-%E8%AF%AD%E9%9F%B3%E5%A4%84%E7%90%86)
    - [CV｜计算机视觉:](#cv%EF%BD%9C%E8%AE%A1%E7%AE%97%E6%9C%BA%E8%A7%86%E8%A7%89)
    - [Probabilistic/Generative Libraries｜概率库和生成库:](#probabilisticgenerative-libraries%EF%BD%9C%E6%A6%82%E7%8E%87%E5%BA%93%E5%92%8C%E7%94%9F%E6%88%90%E5%BA%93)
    - [Other libraries｜其他库:](#other-libraries%EF%BD%9C%E5%85%B6%E4%BB%96%E5%BA%93)
  - [Tutorials & examples｜教程 & 示例](#tutorials-examples%EF%BD%9C%E6%95%99%E7%A8%8B-%E7%A4%BA%E4%BE%8B)
  - [Paper implementations｜论文实现](#paper-implementations%EF%BD%9C%E8%AE%BA%E6%96%87%E5%AE%9E%E7%8E%B0)
  - [Talks & conferences｜报告 & 会议](#talks-conferences%EF%BD%9C%E6%8A%A5%E5%91%8A-%E4%BC%9A%E8%AE%AE)
  - [Pytorch elsewhere ｜ Pytorch相关](#pytorch-elsewhere-%EF%BD%9C-pytorch%E7%9B%B8%E5%85%B3)
        
## Pytorch & related libraries｜Pytorch & 相关库

1. [pytorch](http://pytorch.org): Tensors and Dynamic neural networks in Python with strong GPU acceleration | 使用强GPU加速的Python张量计算和动态神经网络.

### NLP & Speech Processing｜自然语言处理 & 语音处理:

1.  2100+  [text](https://github.com/pytorch/text): 针对文本数据和NLP数据集的数据加载和抽象。
2.  1100+  [pytorch-seq2seq](https://github.com/IBM/pytorch-seq2seq): Pytorch中处理seq2seq的开源框架。
3.  1000-  [anuvada](https://github.com/Sandeep42/anuvada): NLP可解释模型。
4.  1000-  [audio](https://github.com/pytorch/audio): 简单的音频I/O。
5.  1000-  [loop](https://github.com/facebookresearch/loop):  一种跨多说话者的语音生成方法。
6.  7000+  [fairseq](https://github.com/facebookresearch/fairseq-py): Facebook开发的Sequence-to-Sequence python工具包。
7.  1000-  [speech](https://github.com/awni/speech): 语音转文字的端到端模型实现。
8.  3800+  [OpenNMT-py](https://github.com/OpenNMT/OpenNMT-py): 开源神经机器翻译 http://opennmt.net.
9.  1800+  [neuralcoref](https://github.com/huggingface/neuralcoref): 在spaCy中使用神经网络实现快速共指消解。
10.  1000-  [sentiment-discovery](https://github.com/NVIDIA/sentiment-discovery): 基于规模的无监督语言模型在稳健情绪分类中的应用。
11.  2300+  [MUSE](https://github.com/facebookresearch/MUSE): 一个多语言无监督或有监督词语嵌入库。
12.  1000-  [nmtpytorch](https://github.com/lium-lst/nmtpytorch): PyTorch中的Sequence-to-Sequence框架。
13.  1000-  [pytorch-wavenet](https://github.com/vincentherrmann/pytorch-wavenet): 快速生成WaveNet的实现。
14.  1000-  [Tacotron-pytorch](https://github.com/soobinseo/Tacotron-pytorch): Tacotron: 端到端语音合成。
15.  8000+  [AllenNLP](https://github.com/allenai/allennlp): 开源NLP研究库，基于PyTorch。[http://www.allennlp.org/](https://allennlp.org)
16.  1600+  [PyTorch-NLP](https://github.com/PetrochukM/PyTorch-NLP): 为加速NLP研究设立的一个库，包含神经网络层、文本处理模块和众多数据集。 pytorchnlp.readthedocs.io
17.  1000-  [quick-nlp](https://github.com/outcastofmusic/quick-nlp): 基于FastAI的Pytorch NLP库。
18.  1800+  [TTS](https://github.com/mozilla/TTS): 文本转语音的深度学习框架。
19.  2300+  [LASER](https://github.com/facebookresearch/LASER): LASER是一个用来计算和使用多语言语句嵌入的库。
20.  1000-  [pyannote-audio](https://github.com/pyannote/pyannote-audio): 用于说话人分类的神经构建块：语音活动检测, 说话人变化检测, 说话人嵌入。
21.  1000-  [gensen](https://github.com/Maluuba/gensen): 基于大规模多任务学习的通用句子表示。
22.  1000-  [translate](https://github.com/pytorch/translate): 翻译——一个PyTorch语言库。
23.  1800+  [espnet](https://github.com/espnet/espnet): 端到端语音处理工具集。 espnet.github.io/espnet
24.  3000+  [pythia](https://github.com/facebookresearch/pythia): 源于FAIR(Facebook AI Research)的视觉与语言多模态研究的模块化框架。
25.  1300+  [UnsupervisedMT](https://github.com/facebookresearch/UnsupervisedMT): 基于短语的神经无监督机器翻译。
26.  1000-  [jiant](https://github.com/jsalt18-sentence-repl/jiant): 通用文本理解模型的jiant工具包。https://jiant.info
27.  3200+  [BERT-PyTorch](https://github.com/codertimo/BERT-pytorch): Google AI 2018 BERT 的 Pytorch 实现，伴有简单注释。
28.  1800+  [InferSent](https://github.com/facebookresearch/InferSent): NLI的句子嵌入(InferSent)和训练代码。
29.  1000+  [uis-rnn](https://github.com/google/uis-rnn):无限交错状态递归神经网络(UIS-RNN)算法，能够从嘈杂的环境中分辨声音，对应论文 Fully Supervised Speaker Diarization. arxiv.org/abs/1810.04719
30.  8100+  [flair](https://github.com/zalandoresearch/flair): 一个针对最先进的NLP的简单框架。
31.  5700+  [pytext](https://github.com/facebookresearch/pytext): 基于PyTorch的自然语言建模框架。 fb.me/pytextdocs
32.  1000-  [voicefilter](https://github.com/mindslab-ai/voicefilter): 谷歌AI的VoiceFilter的非官方实现。 http://swpark.me/voicefilter
33.  1000-  [BERT-NER](https://github.com/kamalkraj/BERT-NER): 基于BERT的命名体识别(Named-Entity-Recognition)。
34.  1000-  [transfer-nlp](https://github.com/feedly/transfer-nlp): 为可复制实验管理而设计的NLP库。
35.  1000-  [texar-pytorch](https://github.com/asyml/texar-pytorch): 机器学习和文本生成工具包。 texar.io
36.  1400+  [pytorch-kaldi](https://github.com/mravanelli/pytorch-kaldi): pytorch-kaldi 是一个开发中的最先进的dnn/rnn混合语音识别系统。其DNN部分由PyTorch实现，而特征提取、标签计算和解码由kaldi工具包完成。
37.  1000+  [NeMo](https://github.com/NVIDIA/NeMo): 神经模块：对话式AI（conversational AI）工具集 nvidia.github.io/NeMo
38.  1000-  [pytorch-struct](https://github.com/harvardnlp/pytorch-struct): 经过测试的GPU实现库，实现了深度学习中的一些核心的结构化算法，如HMM, Dep Trees, CKY, ...
39.  1000-  [espresso](https://github.com/freewym/espresso): Espresso: 快速的端到端神经语音识别工具集。
40.  22500+  [transformers](https://github.com/huggingface/transformers): huggingface Transformers: TensorFlow 2.0  和 PyTorch 上最先进的NLP工具。huggingface.co/transformers
41.  1000-  [reformer-pytorch](https://github.com/lucidrains/reformer-pytorch): [Reformer](https://openreview.net/pdf?id=rkgNKkHtvB) 的 PyTorch 版。

### CV｜计算机视觉:

1.  5600+  [pytorch vision](https://github.com/pytorch/vision): TorchVision包含流行的数据集、模型架构、计算机视觉中常用的图像变换。
2.  1000-  [pt-styletransfer](https://github.com/tymokvo/pt-styletransfer): 作为PyTorch中一个类的神经风格转移。
3.  1000-  [OpenFacePytorch](https://github.com/thnkim/OpenFacePytorch): 使用OpenFace的nn4.small2.v1.t7模型的PyTorch模块。
4.  1000-  [img_classification_pk_pytorch](https://github.com/felixgwu/img_classification_pk_pytorch): 将你的图像分类模型和最先进的模型进行快速比较 (比如DenseNet, ResNet, ...)
5.  1000+  [SparseConvNet](https://github.com/facebookresearch/SparseConvNet): 子流形稀疏卷积神经网络。
6.  1000-  [Convolution_LSTM_pytorch](https://github.com/automan000/Convolution_LSTM_pytorch): 多层卷积LSTM(长短期记忆网络)模块。
7.  3500+  [face-alignment](https://github.com/1adrianb/face-alignment): :fire: 基于 PyTorch 的 2D 和 3D 面部对齐库。 adrianbulat.com
8.  1200+  [pytorch-semantic-segmentation](https://github.com/ZijunDeng/pytorch-semantic-segmentation): 语义分割。
9.  1000-  [RoIAlign.pytorch](https://github.com/longcw/RoIAlign.pytorch): PyTorch版本的RoIAlign。其实现基于crop_and_resize，支持CPU和GPU上的前向和后向。
10.  1000-  [pytorch-cnn-finetune](https://github.com/creafz/pytorch-cnn-finetune): 用PyTorch微调预训练卷积神经网络。
11.  1000-  [detectorch](https://github.com/ignacio-rocco/detectorch): Detectorch - PyTorch版detectron框架，目前仅有detectron的推断(inference)和评估(evalutaion)功能，无训练(training)功能。
12.  3800+  [Augmentor](https://github.com/mdbloice/Augmentor): 用于机器学习的图像增强库。 http://augmentor.readthedocs.io
13.  1000-  [s2cnn](https://github.com/jonas-koehler/s2cnn): Spherical CNNs：球面卷积网络的PyTorch实现。 (e.g. 全方位图像、全球信号)
14.  1600+  [TorchCV](https://github.com/donnyyou/torchcv): 基于PyTorch的计算机视觉深度学习框架。
15.  7200+  [maskrcnn-benchmark](https://github.com/facebookresearch/maskrcnn-benchmark): 实例分割与对象检测的快速模块化参考实现。
16.  1100+  [image-classification-mobile](https://github.com/osmr/imgclsmob): 计算机视觉卷积网络训练沙盒，包含ImageNet-1K上的与训练分类模型集合。
17.  1000-  [medicaltorch](https://github.com/perone/medicaltorch): 一个医学成像框架。http://medicaltorch.readthedocs.io
18.  4500+  [albumentations](https://github.com/albu/albumentations): 快速图像增强库和其他库的易用包装器。
19.  1900+  [kornia](https://github.com/arraiyopensource/kornia): 开源可微计算机视觉库。https://kornia.org
20.  1000-  [text-detector](https://github.com/s3nh/text-detector): 检测和翻译文本。
21.  1000-  [facenet-pytorch](https://github.com/timesler/facenet-pytorch): 预训练Pytorch人脸检测与识别模型，从 [davidsandberg/facenet](https://github.com/davidsandberg/facenet) 移植而来。
22.  8000+  [detectron2](https://github.com/facebookresearch/detectron2): Detectron2是FAIR的下一代目标检测和分割研究平台。
23.  1000-  [vedaseg](https://github.com/Media-Smart/vedaseg): 基于PyTorch的语义分割工具箱。
24.  1000-  [ClassyVision](https://github.com/facebookresearch/ClassyVision): A用于图像和视频分类的端到端PyTorch框架。https://classyvision.ai
25.  1000-  [detecto](https://github.com/alankbi/detecto): 用 5 行代码构建功能完备的计算机视觉模型。https://detecto.readthedocs.io/
26.  2300+  [pytorch3d](https://github.com/facebookresearch/pytorch3d): PyTorch3d 是一个面向深度学习的高效、可复用的 3D 计算机视觉库。 https://pytorch3d.org/
27.  8800+  [MMDetection](https://github.com/open-mmlab/mmdetection): MMDetection 是一个开源的目标检测工具箱，属于 open-mmlab 项目，由 [Multimedia Laboratory, CUHK](http://mmlab.ie.cuhk.edu.hk/) 开发。
28.  1000-  [neural-dream](https://github.com/ProGamerGov/neural-dream): DeepDream 算法的 PyTorch 实现，可以创造梦一样的幻觉视觉效果。

### Probabilistic/Generative Libraries｜概率库和生成库:

1.  1000-  [ptstat](https://github.com/stepelu/ptstat): 概率编程和统计推断。
2.  6000+  [pyro](https://github.com/uber/pyro): 基于 Python 和 PyTorch 的深度通用概率编程库。 http://pyro.ai
3.  1000-  [probtorch](https://github.com/probtorch/probtorch): Probabilistic Torch是一个扩展了PyTorch的深度生成模型的库。
4.  1000-  [paysage](https://github.com/drckf/paysage): 基于Python/PyTorch的非监督学习和生成模型库。
5.  1000-  [pyvarinf](https://github.com/ctallec/pyvarinf): Python包，促进了带有变分推断的贝叶斯深度学习方法在pytorch中的应用。
6.  1000-  [pyprob](https://github.com/probprog/pyprob): 一个基于PyTorch的概率编程与推断编译的库。
7.  1000-  [mia](https://github.com/spring-epfl/mia): 一个运行针对机器学习模型的成员推理攻击的库。
8.  1000-  [pro_gan_pytorch](https://github.com/akanimax/pro_gan_pytorch): 作为PyTorch nn.Module的扩展的ProGAN包。
9.  1400+  [botorch](https://github.com/pytorch/botorch): PyTorch中的贝叶斯优化。


### Other libraries｜其他库:

1.  1000-  [pytorch extras](https://github.com/mrdrozdov/pytorch-extras): PyTorch的额外特性。
2.  1000-  [functional zoo](https://github.com/szagoruyko/functional-zoo): PyTorch和Tensorflow的模型定义和预训练权重。
3.  1400+  [torch-sampling](https://github.com/ncullen93/torchsample): Pytorch的采样、高级训练、数据增强和实用程序。
4.  1000-  [torchcraft-py](https://github.com/deepcraft/torchcraft-py): TorchCraft的Python包装器，TorchCraft是连接Torch和StarCraft的桥梁。
5.  1000-  [aorun](https://github.com/ramon-oliveira/aorun): Aorun试图以PyTorch为后端实现类似于Keras的API。
6.  1000-  [logger](https://github.com/oval-group/logger): 机器学习记录器（logger）。
7.  1000-  [PyTorch-docset](https://github.com/iamaziz/PyTorch-docset): PyTorch离线文档，结合Dash，Zeal，Velocity或者LovelyDocs使用。
8.  1000-  [convert_torch_to_pytorch](https://github.com/clcarwin/convert_torch_to_pytorch): 将Torch t7模型转换为PyTorch模型。
9.  6100+  [pretrained-models.pytorch](https://github.com/Cadene/pretrained-models.pytorch): PyTorch 预训练卷积神经网络：NASNet, ResNeXt, ResNet, InceptionV4, InceptionResnetV2, Xception, DPN 等等。该项目的目标是帮助复制研究论文结果。
10.  1000-  [pytorch_fft](https://github.com/locuslab/pytorch_fft): CUDA FFTs的PyTorch包装器。
11.  1000-  [caffe_to_torch_to_pytorch](https://github.com/fanq15/caffe_to_torch_to_pytorch): Caffe模型转PyTorch/Torch模型，Torch模型转PyTorch模型。
12.  1000-  [pytorch-extension](https://github.com/sniklaus/pytorch-extension): PyTorch的CUDA扩展示例，计算了两个张量的[哈达玛积(Hadamard product)](https://baike.baidu.com/item/哈达玛积/18894493?fr=aladdin)。
13.  6000+  [tensorboard-pytorch](https://github.com/lanpa/tensorboard-pytorch): 该模块以tensorboard格式保存PyTorch张量以供检查。目前支持tensorboard中的标量、图像、音频、直方图等特性。
14.  1800+  [gpytorch](https://github.com/jrg365/gpytorch): GPyTorch是一个用PyTorch实现的高斯过程库。它可以轻松地创建可伸缩、灵活和模块化的高斯过程模型。
15.  2000+  [spotlight](https://github.com/maciejkula/spotlight): 深度推荐模型。
16.  1000-  [pytorch-cns](https://github.com/awentzonline/pytorch-cns): 基于PyTorch的广义压缩网络搜索（Generalized [Compressed Network Search](http://people.idsia.ch/~juergen/compressednetworksearch.html)）。
17.  1000-  [pyinn](https://github.com/szagoruyko/pyinn): CuPy实现融合PyTorch操作。
18.  1000-  [inferno](https://github.com/nasimrahaman/inferno): 关于PyTorch的实用程序库。
19.  1000-  [pytorch-fitmodule](https://github.com/henryre/pytorch-fitmodule): 一种用于PyTorch模块的超简单拟合方法。
20.  2900+  [inferno-sklearn](https://github.com/dnouri/inferno): 一个基于PyTorch封装且兼容scikit-learn的神经网络库。
21.  1000-  [pytorch-caffe-darknet-convert](https://github.com/marvis/pytorch-caffe-darknet-convert): 在 pytorch, caffe prototxt/weights 和 darknet cfg/weights 之间转换。
22.  1000-  [pytorch2caffe](https://github.com/longcw/pytorch2caffe): 将PyTorch模型转换成Caffe模型。
23.  1000-  [pytorch-tools](https://github.com/nearai/pytorch-tools): PyTorch工具。
24.  1700+  [sru](https://github.com/taolei87/sru): 训练RNNs和训练CNNs一样快。 (arxiv.org/abs/1709.02755)
25.  1000-  [torch2coreml](https://github.com/prisma-ai/torch2coreml): Torch7 -> CoreML，该工具可将Torch7模型转换为[Apple CoreML](https://developer.apple.com/documentation/coreml)格式以便在Apple设备上运行。
26.  1200+  [PyTorch-Encoding](https://github.com/zhanghang1989/PyTorch-Encoding): PyTorch 深度纹理编码网络 (Deep Texture Encoding Network) http://hangzh.com/PyTorch-Encoding
27.  1000-  [pytorch-ctc](https://github.com/ryanleary/pytorch-ctc): PyTorch-CTC 实现了CTC(联结主义时间分类，Connectionist Temporal Classification)集束搜索（Beam Search）解码。C++代码借鉴了TensorFlow，并通过一些改进增加了灵活性。
28.  1000-  [candlegp](https://github.com/t-vi/candlegp): Pytorch中的高斯过程。
29.  1000-  [dpwa](https://github.com/loudinthecloud/dpwa): 基于成对平均（Pair-Wise Averaging）的分布式学习。
30.  1000-  [dni-pytorch](https://github.com/koz4k/dni-pytorch): 基于合成梯度的PyTorch解耦神经接口。
31.  2900+  [skorch](https://github.com/dnouri/skorch): 一个基于PyTorch封装且兼容scikit-learn的神经网络库。
32.  2500+  [ignite](https://github.com/pytorch/ignite): Ignite是一个高级库，帮助你在PyTorch中训练神经网络。
33.  1000-  [Arnold](https://github.com/glample/Arnold): Arnold - DOOM 游戏代理。
34.  1000-  [pytorch-mcn](https://github.com/albanie/pytorch-mcn): 将MatConvNet模型转换为PyTorch模型。
35.  2100+  [simple-faster-rcnn-pytorch](https://github.com/chenyuntc/simple-faster-rcnn-pytorch): Faster R-CNN 的简化实现，性能与原始论文相当。
36.  1000-  [generative_zoo](https://github.com/DL-IT/generative_zoo): generative_zoo提供了PyTorch中一些生成模型的工作实现。
37.  1100+  [pytorchviz](https://github.com/szagoruyko/pytorchviz): 可视化PyTorch的运行图。
38.  1000-  [cogitare](https://github.com/cogitare-ai/cogitare): Cogitare - 一个现代、快速、模块化的深度学习和机器学习框架。
39.  1000-  [pydlt](https://github.com/dmarnerides/pydlt): 基于PyTorch的深度学习工具箱。
40.  1000-  [semi-supervised-pytorch](https://github.com/wohlert/semi-supervised-pytorch): 各种基于VAE的半监督模型和生成模型的实现。
41.  1000-  [pytorch_cluster](https://github.com/rusty1s/pytorch_cluster): 优化图簇算法的PyTorch扩展库。
42.  1000-  [neural-assembly-compiler](https://github.com/aditya-khant/neural-assembly-compiler): 基于自适应神经编译的PyTorch神经汇编编译器。
43.  1000-  [caffemodel2pytorch](https://github.com/vadimkantorov/caffemodel2pytorch): 将Caffe模型转换为PyTorch模型。
44.  1000-  [extension-cpp](https://github.com/pytorch/extension-cpp): PyTorch中的C++扩展。
45.  1000-  [pytoune](https://github.com/GRAAL-Research/pytoune): 类Keras框架和实用程序。
46.  1000-  [jetson-reinforcement](https://github.com/dusty-nv/jetson-reinforcement): 使用PyTorch，OpenAI Gym和Gazebo机器人模拟的NVIDIA Jetson深度强化学习GPU库。
47.  1000-  [matchbox](https://github.com/salesforce/matchbox): 编写单个示例的PyTorch代码，然后小批量地高效运行。
48.  1000-  [torch-two-sample](https://github.com/josipd/torch-two-sample): PyTorch双样本测试库。
49.  2000+  [pytorch-summary](https://github.com/sksq96/pytorch-summary): PyTorch模型总结，类似于Keras中的`model.summary()`。
50.  1000-  [mpl.pytorch](https://github.com/BelBES/mpl.pytorch): MaxPoolingLoss的PyTorch实现。
51.  null  [scVI-dev](https://github.com/YosefLab/scVI-dev): 链接失效。
52.  3400+  [apex](https://github.com/NVIDIA/apex): 一个PyTorch扩展：面向精简混合精度和分布式训练。
53.  3000+  [ELF](https://github.com/pytorch/ELF): ELF: 游戏研究平台，复现了AlphaGoZero/AlphaZero。
54.  1000-  [Torchlite](https://github.com/EKami/Torchlite): Pytorch建立在sklearn、Pytorch和Tensorflow等流行机器学习框架上的高水平库。
55.  1000-  [joint-vae](https://github.com/Schlumberger/joint-vae): JointVAE的PyTorch实现，一个面向分离连续和离散变异因素的框架 :star2:。
56.  1000-  [SLM-Lab](https://github.com/kengz/SLM-Lab): PyTorch模块化深度强化学习框架。
57.  1000-  [bindsnet](https://github.com/Hananel-Hazan/bindsnet): 一个Python包，可借助PyTorch `Tensor` 功能在CPUs或GPUs上模拟脉冲神经网络(SNNs, Spiking Neural Networks)。
58.  1000-  [pro_gan_pytorch](https://github.com/akanimax/pro_gan_pytorch): 作为 PyTorch nn.Module 扩展的 ProGAN 包。
59.  6600+  [pytorch_geometric](https://github.com/rusty1s/pytorch_geometric): PyTorch几何深度学习扩展库。
60.  1000-  [torchplus](https://github.com/knighton/torchplus): 在 PyTorch modules 上实现 + 运算符，返回序列。
61.  1000-  [lagom](https://github.com/zuoxingdong/lagom): lagom: 用于强化学习算法快速原型构建的轻量级PyTorch架构。
62.  1000-  [torchbearer](https://github.com/ecs-vlc/torchbearer): torchbearer: PyTorch模型拟合库。
63.  1000-  [pytorch-maml-rl](https://github.com/tristandeleu/pytorch-maml-rl): 强化学习中的模型不可知元学习(MAML, Model-Agnostic Meta-Learning)。
64.  1000-  [NALU](https://github.com/bharathgs/NALU): 神经算术逻辑单元(Neural Arithmetic Logic Units)的PyTorch基本实现，论文：arxiv.org/pdf/1808.00508.pdf 。
65.  1000-  [QuCumber](https://github.com/PIQuIL/QuCumber): 神经网络多体波函数重构。
66.  1000-  [magnet](https://github.com/MagNet-DL/magnet): 自我建立的深度学习项目。http://magnet-dl.readthedocs.io/
67.  1000-  [opencv_transforms](https://github.com/jbohnslav/opencv_transforms): OpenCV实现Torchvision的图像分割。
68.  17100+  [fastai](https://github.com/fastai/fastai): fast.ai 深度学习库、课程和教程。
69.  1000-  [pytorch-dense-correspondence](https://github.com/RobotLocomotion/pytorch-dense-correspondence): [《Dense Object Nets: Learning Dense Visual Object Descriptors By and For Robotic Manipulation》](arxiv.org/pdf/1806.08756.pdf) 一文的代码。
70.  1000-  [colorization-pytorch](https://github.com/richzhang/colorization-pytorch): PyTorch实现交互式深度着色(Interactive Deep Colorization)。 richzhang.github.io/ideepcolor
71.  1000-  [beauty-net](https://github.com/cms-flash/beauty-net): PyTorch一个简单、灵活、可扩展的PyTorch模板。
72.  1000-  [OpenChem](https://github.com/Mariewelt/OpenChem): OpenChem: 面向计算化学和药物设计研究的深度学习工具包 mariewelt.github.io/OpenChem 。
73.  1000-  [torchani](https://github.com/aiqm/torchani): PyTorch精确神经网络电位。 aiqm.github.io/torchani
74.  1000-  [PyTorch-LBFGS](https://github.com/hjmshi/PyTorch-LBFGS): PyTorch实现L-BFGS。
75.  1800+  [gpytorch](https://github.com/cornellius-gp/gpytorch): PyTorch中对高斯过程的高效且模块化的实现。
76.  1000-  [hessian](https://github.com/mariogeiger/hessian): PyTorch版hessian。
77.  1000-  [vel](https://github.com/MillionIntegrals/vel): 深度学习研究中的速度。
78.  1000-  [nonechucks](https://github.com/msamogh/nonechucks): 动态地处理数据集中的坏样本，使用转换作为过滤器。
79.  1000-  [torchstat](https://github.com/Swall0w/torchstat): PyTorch中的模型分析器。
80.  1200+  [QNNPACK](https://github.com/pytorch/QNNPACK): 量化神经网络包—量化神经网络算子的移动优化实现。
81.  2700+  [torchdiffeq](https://github.com/rtqichen/torchdiffeq): PyTorch解常微分方程（ODE），使用的是全GPU支持、O(1)内存复杂度的反向传播算法。
82.  1000-  [redner](https://github.com/BachiLi/redner): 可微的 Monte Carlo 路径跟踪器。
83.  1000-  [pixyz](https://github.com/masa-su/pixyz): 一个库，用来以更简洁、直观和可扩展的方式开发深层生成模型。
84.  1000-  [euclidesdb](https://github.com/perone/euclidesdb): 一种多模型机器学习特征嵌入数据库。 http://euclidesdb.readthedocs.io
85.  1000-  [pytorch2keras](https://github.com/nerox8664/pytorch2keras): 将PyTorch模型转换为Keras模型。
86.  1000-  [salad](https://github.com/domainadaptation/salad): 域适应和半监督学习工具箱。
87.  1000-  [netharn](https://github.com/Erotemic/netharn): PyTorch的参数化拟合和预测线束（Prediction Harnesses）。
88.  4000+  [dgl](https://github.com/dmlc/dgl): Python包，基于现有的DL框架，用于简化对图形的深度学习。http://dgl.ai.
89.  1400+  [gandissect](https://github.com/CSAILVision/gandissect): 基于PyTorch的工具，用于可视化和理解GAN的神经元。gandissect.csail.mit.edu
90.  1000-  [delira](https://github.com/justusschock/delira): 基于PyTorch和Tensorlow的快速原型和训练深层神经网络的轻量级框架，用于医疗成像。 delira.rtfd.io
91.  1000-  [mushroom](https://github.com/AIRLab-POLIMI/mushroom): 强化学习实验的Python库。
92.  1000-  [Xlearn](https://github.com/thuml/Xlearn): 迁移学习库。
93.  1000-  [geoopt](https://github.com/ferrine/geoopt): 基于PyTorch优化的黎曼自适应优化方法。
94.  1000-  [vegans](https://github.com/unit8co/vegans): 包含多种现有的GANs。
95.  1900+  [kornia](https://github.com/arraiyopensource/kornia): PyTorch开源可微计算机视觉库。 https://kornia.org
96.  1000-  [AdverTorch](https://github.com/BorealisAI/advertorch): 研究对抗鲁棒性的工具箱。
97.  2700+  [AdaBound](https://github.com/Luolc/AdaBound): 一个优化器，训练速度和Adam一样快，和SGD一样好。
98.  1000-  [fenchel-young-losses](https://github.com/mblondel/fenchel-young-losses): 在PyTorch/TensorFlow/scikit-learn中使用Fenchel-Young损失作为概率分类的损失函数。
99.  1400+  [pytorch-OpCounter](https://github.com/Lyken17/pytorch-OpCounter): 统计PyTorch模型的MACs/FLOPs。
100.  1000-  [Tor10](https://github.com/kaihsin/Tor10): 基于PyTorch，为量子模拟设计的通用张量网络库。
101.  1600+  [Catalyst](https://github.com/catalyst-team/catalyst): PyTorch DL&RL 研究的高级实用程序。它的开发重点是可重复性、快速实验和代码/思想重用。能够研究/开发新的东西，而不是编写另一个常规的训练循环。
102.  1000+  [Ax](https://github.com/facebook/Ax): 自适应实验平台。
103.  1000-  [pywick](https://github.com/achaiah/pywick): 高水平的PyTorch神经网络训练库。
104.  1000-  [torchgpipe](https://github.com/kakaobrain/torchgpipe): PyTorch实现GPipe。 torchgpipe.readthedocs.io
105.  1000-  [hub](https://github.com/pytorch/hub): Pytorch Hub 是一个预训练模型库，用来提升研究的可重复性。
106.  3800+  [pytorch-lightning](https://github.com/williamFalcon/pytorch-lightning): 面向ML研究人员的轻量级PyTorch包装器。缩放模型，少写样板。
107.  1000-  [Tor10](https://github.com/kaihsin/Tor10): 基于pytorch为量子模拟设计的通用张量网络库。
108.  2700+  [tensorwatch](https://github.com/microsoft/tensorwatch): 针对Python机器学习与数据科学的调试、监控与可视化。
109.  1000-  [wavetorch](https://github.com/fancompute/wavetorch): 波动方程的数值求解与反传播。 arxiv.org/abs/1904.12831
110.  1000-  [diffdist](https://github.com/ag14774/diffdist): diffdist是一个面向PyTorch的Python库。它扩展了`torch.autograd`的默认功能，并增加了对进程间可微通信的支持。
111.  1000-  [torchprof](https://github.com/awwong1/torchprof): 用于Pytorch模型逐层分析的最小依赖库。
112.  1000-  [osqpth](https://github.com/oxfordcontrol/osqpth): PyTorch可微OSQP求解器。
113.  1000-  [mctorch](https://github.com/mctorch/mctorch): 面向深度学习的流形优化库。
114.  1000-  [pytorch-hessian-eigenthings](https://github.com/noahgolmant/pytorch-hessian-eigenthings): 使用Hessian向量积和随机幂迭代的高效PyTorch Hessian特征分解。
115.  1000-  [MinkowskiEngine](https://github.com/StanfordVL/MinkowskiEngine): 闵可夫斯基引擎是一个用于广义稀疏卷积和高维稀疏张量的自动微分方法库。
116.  1000-  [pytorch-cpp-rl](https://github.com/Omegastick/pytorch-cpp-rl): CppRl是一个强化学习框架，用 PyTorch C++ 前端编写。
117.  1000-  [pytorch-toolbelt](https://github.com/BloodAxe/pytorch-toolbelt): PyTorch扩展，用来进行快速R&D原型开发和Kaggle代码收集。
118.  1000-  [argus-tensor-stream](https://github.com/Fonbet/argus-tensor-stream): 一个库，用来将实时视频流解码至CUDA内存。tensorstream.argus-ai.com
119.  1000-  [macarico](https://github.com/hal3/macarico): 在 PyTorch 中学习搜索。
120.  1200+  [rlpyt](https://github.com/astooke/rlpyt): PyTorch 中的强化学习。
121.  1000-  [pywarm](https://github.com/blue-season/pywarm): 为 PyTorch 建立神经网络的一种更清洁的方法。https://blue-season.github.io/pywarm/
122.  1000-  [learn2learn](https://github.com/learnables/learn2learn): PyTorch元学习框架。http://learn2learn.net
123.  1000-  [torchbeast](https://github.com/facebookresearch/torchbeast): 分布式强化学习的PyTorch平台。
124.  1000-  [higher](https://github.com/facebookresearch/higher): higher 是一个PyTorch库，允许用户获得跨越训练循环而不是单个训练步骤的损失的高阶梯度。
125.  null  [Torchelie](https://github.com/Vermeille/Torchelie/): Torchélie 是面向PyTorch的一系列工具函数、层、损失、模型、训练器等的合集。 https://torchelie.readthedocs.org/
126.  1000-  [CrypTen](https://github.com/facebookresearch/CrypTen): CrypTen 是一个隐私保护机器学习框架，它使用PyTorch编写，允许研究人员和开发人员使用加密数据训练模型。CrypTen目前支持将安全的多方计算（[Secure Multiparty Computation](https://en.wikipedia.org/wiki/Secure_multi-party_computation)）作为其加密机制。
127.  1000-  [cvxpylayers](https://github.com/cvxgrp/cvxpylayers): cvxpylayers 是一个 Python 库，用于在PyTorch中构造可微凸优化层。
128.  1000-  [RepDistiller](https://github.com/HobbitLong/RepDistiller): 对比表示蒸馏（CRD）和最新知识蒸馏方法的基准。
129.  1700+  [kaolin](https://github.com/NVIDIAGameWorks/kaolin): 一个旨在加速3D深度学习研究的PyTorch库。
130.  1000-  [PySNN](https://github.com/BasBuller/PySNN): 高效的尖峰神经网络框架，建立在PyTorch之上，用于GPU加速。
131.  1000-  [sparktorch](https://github.com/dmmiller612/sparktorch): 在 Apache Spark 上训练和运行 PyTorch 模型。
132.  1000-  [pytorch-metric-learning](https://github.com/KevinMusgrave/pytorch-metric-learning): 在应用程序中使用度量学习的最简单方法。模块化，灵活，可扩展。用 PyTorch 构建。
133.  1000-  [autonomous-learning-library](https://github.com/cpnota/autonomous-learning-library): 用于建立深度强化学习代理的 PyTorch 库。
134.  1000-  [flambe](https://github.com/asappresearch/flambe): 一个用于加速研究及其生产路径的ML框架。https://flambe.ai
135.  1000-  [pytorch-optimizer](https://github.com/jettify/pytorch-optimizer): Collections of modern optimization algorithms for PyTorch, includes: AccSGD, AdaBound, AdaMod, DiffGrad, Lamb, RAdam, RAdam, Yogi.
136. [PyTorch-VAE](https://github.com/AntixK/PyTorch-VAE): A Collection of Variational Autoencoders (VAE) in PyTorch.

## Tutorials & examples｜教程 & 示例

1.  3800+  [Practical Pytorch](https://github.com/spro/practical-pytorch)**: 该教程对不同的RNN模型进行了解释。
2. [DeepLearningForNLPInPytorch](https://pytorch.org/tutorials/beginner/deep_learning_nlp_tutorial.html): IPython Notebook 深度学习教程，包含对自然语言处理的强调。
3.  15500+  [pytorch-tutorial](https://github.com/yunjey/pytorch-tutorial): 面向研究人员的深度学习教程，其中大部分模型的实现代码都少于30行。
4.  1000-  [pytorch-exercises](https://github.com/keon/pytorch-exercises): PyTorch练习集合。
5.  3300+  [pytorch tutorials](https://github.com/pytorch/tutorials): 各种PyTorch教程。
6.  11900+  [pytorch examples](https://github.com/pytorch/examples):  PyTorch使用示例，应用场景包括视觉、文本、强化学习等。
7.  1000-  [pytorch practice](https://github.com/napsternxg/pytorch-practice): PyTorch示例。  
8.  1000-  [pytorch mini tutorials](https://github.com/vinhkhuc/PyTorch-Mini-Tutorials): PyTorch极简教程，改编自Alec Radford的[Theano教程](https://github.com/Newmu/Theano-Tutorials)。
9.  1000-  [pytorch text classification](https://github.com/xiayandi/Pytorch_text_classification): PyTorch实现基于CNN的文本分类。
10.  1000-  [cats vs dogs](https://github.com/desimone/pytorch-cat-vs-dogs): Kaggle 竞赛 Dogs vs. Cats Redux: Kernels Edition 的网络微调示例。
11.  1000-  [convnet](https://github.com/eladhoffer/convNet.pytorch): 深度卷积网络在不同数据集(ImageNet, Cifar10, Cifar100, MNIST)上的完整训练示例。
12.  1000-  [pytorch-generative-adversarial-networks](https://github.com/mailmahee/pytorch-generative-adversarial-networks): 一个简单的对抗生成网络(GAN) 。
13.  1000-  [pytorch containers](https://github.com/amdegroot/pytorch-containers): PyTorch中简化的Torch容器。
14.  1000-  [T-SNE in pytorch](https://github.com/cemoody/topicsne): t-SNE实验。
15.  1000-  [AAE_pytorch](https://github.com/fducau/AAE_pytorch): PyTorch版对抗自编码器。
16.  1000-  [Kind_PyTorch_Tutorial](https://github.com/GunhoChoi/Kind_PyTorch_Tutorial): PyTorch新手教程。  
17.  1000-  [pytorch-poetry-gen](https://github.com/justdark/pytorch-poetry-gen): 基于PyTorch的char-RNN（字符级循环神经网络）。  
18.  1000-  [pytorch-REINFORCE](https://github.com/JamesChuanggg/pytorch-REINFORCE): PyTorch 实现了 OpenAI gym 下离散和连续控制的 REINFORCE。
19.  4300+  [PyTorch-Tutorial](https://github.com/MorvanZhou/PyTorch-Tutorial)**: 简单而快速地搭建你自己的神经网络。 https://morvanzhou.github.io/tutorials/
20.  1000-  [pytorch-intro](https://github.com/joansj/pytorch-intro): 演示如何在PyTorch中实现CNNs和RNNs。
21.  1000-  [pytorch-classification](https://github.com/bearpaw/pytorch-classification): 一个CIFAR-10/100和ImageNet数据集上的分类框架。
22.  1000-  [pytorch_notebooks - hardmaru](https://github.com/hardmaru/pytorch_notebooks): 用NumPy和PyTorch编写的随机教程。
23.  1000-  [pytorch_tutoria-quick](https://github.com/soravux/pytorch_tutorial): PyTorch介绍和教程。面向计算机视觉、图形和机器学习领域的研究人员，要求对神经网络理论知识和常用神经网络框架由基本的了解。
24.  1000-  [Pytorch_fine_tuning_Tutorial](https://github.com/Spandan-Madan/Pytorch_fine_tuning_Tutorial): 在PyTorch中进行微调或转移学习的简短教程。
25.  1000-  [pytorch_exercises](https://github.com/Kyubyong/pytorch_exercises): PyTorch练习。
26.  1000-  [traffic-sign-detection](https://github.com/soumith/traffic-sign-detection-homework): 纽约大学2018年计算机视觉秋季课程示例。
27.  1000-  [mss_pytorch](https://github.com/Js-Mim/mss_pytorch): 无需进行滤波后处理，利用循环推断算法实现歌唱语音分离 - PyTorch 实现。 演示: js-mim.github.io/mss_pytorch
28.  2200+  [DeepNLP-models-Pytorch](https://github.com/DSKSD/DeepNLP-models-Pytorch) cs-224n课程中的各种深度NLP模型的PyTorch实现。(Stanford Univ: NLP with Deep Learning)
29.  1000-  [Mila introductory tutorials](https://github.com/mila-udem/welcome_tutorials): 面向MILA新生的各种教程。（[MILA：加拿大蒙特利尔人工智能研究中心](https://mila.quebec/en/mila/)）
30.  1000-  [pytorch.rl.learning](https://github.com/moskomule/pytorch.rl.learning): 使用PyTorch学习强化学习。
31.  1000-  [minimal-seq2seq](https://github.com/keon/seq2seq): 关注神经机器翻译的最小Seq2Seq模型。
32.  1000-  [tensorly-notebooks](https://github.com/JeanKossaifi/tensorly-notebooks): 利用Python和TensorLy实现张量方法。 tensorly.github.io/dev
33.  1000-  [pytorch_bits](https://github.com/jpeg729/pytorch_bits): 时序预测的相关示例。
34.  1000-  [skip-thoughts](https://github.com/sanyam5/skip-thoughts): PyTorch实现Skip-Thought词向量模型。
35.  1000-  [video-caption-pytorch](https://github.com/xiadingZ/video-caption-pytorch): 利用PyTorch为视频添加字幕。
36.  1000-  [Capsule-Network-Tutorial](https://github.com/higgsfield/Capsule-Network-Tutorial): 简单易学的胶囊网络（Capsule Network）教程。
37.  1700+  [code-of-learn-deep-learning-with-pytorch](https://github.com/SherlockLiao/code-of-learn-deep-learning-with-pytorch): 《深度学习入门之PyTorch》书中代码。 item.jd.com/17915495606.html
38.  1800+  [RL-Adventure](https://github.com/higgsfield/RL-Adventure): Pytorch 版 Deep Q Learning 教程，简单、易学、代码可读性强，包含 DQN / DDQN / Prioritized replay/ noisy networks/ distributional values/ Rainbow/ hierarchical RL 的 PyTorch 实现。
39.  1000-  [accelerated_dl_pytorch](https://github.com/hpcgarage/accelerated_dl_pytorch): Jupyter Day Atlanta II 会议上的加速深度学习算法，包含 PyTorch 教程和会议演讲文稿。
40.  2000+  [RL-Adventure-2](https://github.com/higgsfield/RL-Adventure-2): 以下内容的 PyTorch0.4 版本教程: actor critic / proximal policy optimization / acer / ddpg / twin dueling ddpg / soft actor critic / generative adversarial imitation learning / hindsight experience replay。
41. [Generative Adversarial Networks (GANs) in 50 lines of code (PyTorch)](https://medium.com/@devnag/generative-adversarial-networks-gans-in-50-lines-of-code-pytorch-e81b79659e3f): 50行生成对抗网络。
42. [adversarial-autoencoders-with-pytorch](https://blog.paperspace.com/adversarial-autoencoders-with-pytorch/): PyTorch对抗自编码器。
43. [transfer learning using pytorch](https://medium.com/@vishnuvig/transfer-learning-using-pytorch-4c3475f4495): PyTorch迁移学习。
44. [how-to-implement-a-yolo-object-detector-in-pytorch](https://blog.paperspace.com/how-to-implement-a-yolo-object-detector-in-pytorch/): 如何使用PyTorch实现一个YOLO (v3)物体检测器。
45. [pytorch-for-recommenders-101](http://blog.fastforwardlabs.com/2018/04/10/pytorch-for-recommenders-101.html): 使用PyTorch构建推荐系统。
46.  1000-  [pytorch-for-numpy-users](https://github.com/wkentaro/pytorch-for-numpy-users): 面向Numpy用户的PyTorch。
47. [PyTorch Tutorial](http://www.pytorchtutorial.com/): PyTorch中文教程（PyTorch中文网）。
48.  1000-  [grokking-pytorch](https://github.com/Kaixhin/grokking-pytorch): 手把手教你学会PyTorch。
49.  1600+  [PyTorch-Deep-Learning-Minicourse](https://github.com/Atcold/PyTorch-Deep-Learning-Minicourse): PyTorch深度学习微型课程。
50.  1000-  [pytorch-custom-dataset-examples](https://github.com/utkuozbulak/pytorch-custom-dataset-examples): PyTorch的一些自定义数据集示例。
51. [Multiplicative LSTM for sequence-based Recommenders](https://florianwilhelm.info/2018/08/multiplicative_LSTM_for_sequence_based_recos/): 面向基于序列的推荐器的乘法LSTM。/基于LSTM的序列推荐实现。
52.  1000-  [deeplearning.ai-pytorch](https://github.com/furkanu/deeplearning.ai-pytorch): Coursera深度学习课程(deeplearning.ai)任务的PyTorch实现。
53.  1000-  [MNIST_Pytorch_python_and_capi](https://github.com/tobiascz/MNIST_Pytorch_python_and_capi): 示例：如何在Python中训练一个MNIST网络并在C++中用PyTorch1.0运行。
54.  1000-  [torch_light](https://github.com/ne7ermore/torch_light): 教程和示例，包括强化学习、NLP、CV。Logistic、CNN、RNN、LSTM等神经网络模型由数行代码实现，一些高级示例由复杂模型实现。
55.  1000-  [portrain-gan](https://github.com/dribnet/portrain-gan): 编码（解码尚未实现）art-DCGAN 生成的肖像油画。
56.  1000-  [mri-analysis-pytorch](https://github.com/omarsar/mri-analysis-pytorch): 使用PyTorch和MedicalTorch进行核磁共振（MRI）分析。
57.  1000-  [cifar10-fast](https://github.com/davidcpage/cifar10-fast): 在79秒内完成CIFAR10数据集上的ResNet模型的训练并达到94%的测试准确率，相关内容参见 [blog series](https://www.myrtle.ai/2018/09/24/how_to_train_your_resnet/)。
58. [Intro to Deep Learning with PyTorch](https://in.udacity.com/course/deep-learning-pytorch--ud188): Udacity和Facebook联合推出的免费课程，包括对PyTorch的介绍和对PyTorch作者之一的Soumith Chintala的采访。
59.  1500+  [pytorch-sentiment-analysis](https://github.com/bentrevett/pytorch-sentiment-analysis): PyTorch和TorchText语义分析教程。
60.  2600+  [pytorch-image-models](https://github.com/rwightman/pytorch-image-models): PyTorch图像模型、脚本、与训练权重—— (SE)ResNet/ResNeXT, DPN, EfficientNet, MobileNet-V3/V2/V1, MNASNet, Single-Path NAS, FBNet等等。
61.  1000-  [CIFAR-ZOO](https://github.com/BIGBALLON/CIFAR-ZOO): 以CIFAR为基准的多种CNN架构的PyTorch实现。
62.  2700+  [d2l-pytorch](https://github.com/dsgiitr/d2l-pytorch): 本项目尝试复制《动手深度学习（Dive into Deep Learning）》(www.d2l.ai) 一书，将MXnet代码改编为PyTorch版。
63.  1000-  [thinking-in-tensors-writing-in-pytorch](https://github.com/stared/thinking-in-tensors-writing-in-pytorch):  张量思维，PyTorch实践 (深度学习入门)。
64.  1000-  [NER-BERT-pytorch](https://github.com/lemonhu/NER-BERT-pytorch): 命名试题识别的PyTorch解决方案，使用了Google AI的预训练BERT模型。
65.  1000-  [pytorch-sync-batchnorm-example](https://github.com/dougsouza/pytorch-sync-batchnorm-example): 如何在 PyTorch 中使用交叉复制（Cross Replica）/同步批标准化（Synchronized Batchnorm）。
66.  1000-  [SentimentAnalysis](https://github.com/barissayil/SentimentAnalysis): 情绪分析神经网络，在斯坦福情绪树库上用微调BERT训练得到。
67. [pytorch-cpp](https://github.com/prabhuomkar/pytorch-cpp): C++ implementations of PyTorch tutorials for deep learning researchers (based on the Python tutorials from [pytorch-tutorial](https://github.com/yunjey/pytorch-tutorial)).

## Paper implementations｜论文实现

1.  1000-  [google_evolution](https://github.com/neuralix/google_evolution): 实现了 [Large-scale evolution of image classifiers](https://arxiv.org/abs/1703.01041) 一文的结果网络之一。
2.  1000-  [pyscatwave](https://github.com/edouardoyallon/pyscatwave): 基于CuPy/PyTorch的快速散射变换，[Scaling the Scattering Transform: Deep Hybrid Networks](https://arxiv.org/abs/1703.08961)
3.  1000-  [scalingscattering](https://github.com/edouardoyallon/scalingscattering): 该仓库包含 [Scaling The Scattering Transform : Deep Hybrid Networks](https://arxiv.org/abs/1703.08961) 一文中的实验。  
4.  1000-  [deep-auto-punctuation](https://github.com/episodeyang/deep-auto-punctuation): 通过逐字符学习实现自动添加标点。
5.  1000-  [Realtime_Multi-Person_Pose_Estimation](https://github.com/tensorboy/pytorch_Realtime_Multi-Person_Pose_Estimation): 基于PyTorch的多人人体姿态估计，[原始代码](https://github.com/ZheC/Realtime_Multi-Person_Pose_Estimation)。
6.  1000-  [PyTorch-value-iteration-networks](https://github.com/onlytailei/PyTorch-value-iteration-networks): PyTorch实现价值迭代网络（[Value Iteration Networks](https://arxiv.org/abs/1602.02867)）（NIPS2016最佳论文奖）。
7.  1000-  [pytorch_Highway](https://github.com/analvikingur/pytorch_Highway): PyTorch实现高速公路网络（[Highway Networks](https://arxiv.org/abs/1505.00387)）。
8.  1000-  [pytorch_NEG_loss](https://github.com/analvikingur/pytorch_NEG_loss): PyTorch实现负采样损失（[Negative Sampling Loss](https://arxiv.org/abs/1310.4546)）。  
9.  1000-  [pytorch_RVAE](https://github.com/analvikingur/pytorch_RVAE): 用PyTorch实现的产生序列数据的递归变分自动编码器，相关论文：[Generating Sentences from a Continuous Space](https://arxiv.org/abs/1511.06349#)，[Character-Aware Neural Language Models](https://arxiv.org/abs/1508.06615)。
10.  1000-  [pytorch_TDNN](https://github.com/analvikingur/pytorch_TDNN): 用PyTorch实现时间延迟神经网络（Time Delayed NN）。
11.  1000-  [eve.pytorch](https://github.com/moskomule/eve.pytorch): 一个Eve优化器的实现，相关论文：[Imploving Stochastic Gradient Descent with Feedback](https://arxiv.org/abs/1611.01505)。  
12.  1000-  [e2e-model-learning](https://github.com/locuslab/e2e-model-learning): 随机优化中的基于任务的端到端模型，https://arxiv.org/abs/1703.04529 。
13.  1000-  [pix2pix-pytorch](https://github.com/mrzhu-cool/pix2pix-pytorch): PyTorch实现“基于条件对抗网络的图像到图像翻译”。 论文：[Image-to-Image Translation Using Conditional Adversarial Networks](https://arxiv.org/pdf/1611.07004v1.pdf)。
14.  3300+  [Single Shot MultiBox Detector](https://github.com/amdegroot/ssd.pytorch): 单发多盒探测器，论文：[Single Shot MultiBox Detector](http://arxiv.org/abs/1512.02325)。
15.  1000-  [DiscoGAN](https://github.com/carpedm20/DiscoGAN-pytorch): 学习利用生成性对抗网络发现跨域关系。论文：[Learning to Discover Cross-Domain Relations with Generative Adversarial Networks](https://arxiv.org/abs/1703.05192)。  
16.  1000-  [official DiscoGAN implementation](https://github.com/SKTBrain/DiscoGAN): 官方实现“学习利用生成性对抗网络发现跨域关系”。 论文：[Learning to Discover Cross-Domain Relations with Generative Adversarial Networks](https://arxiv.org/abs/1703.05192)。  
17.  1000-  [pytorch-es](https://github.com/atgambardella/pytorch-es): 进化策略。论文：[Evolution Strategies as a Scalable Alternative to Reinforcement Learning](https://arxiv.org/abs/1703.03864) .  
18.  1000-  [piwise](https://github.com/bodokaiser/piwise): 使用PyTorch对VOC2012数据集进行像素切割。
19.  1000-  [pytorch-dqn](https://github.com/transedward/pytorch-dqn): 深度Q学习网络。  
20.  1000-  [neuraltalk2-pytorch](https://github.com/ruotianluo/neuraltalk2.pytorch): PyTorch图像字幕代码库(在分支“with_finetune”中有可微调CNN)。
21.  1000-  [vnet.pytorch](https://github.com/mattmacy/vnet.pytorch): PyTorch实现V-Net：全卷积神经网络在体医学图像分割中的应用。 http://mattmacy.io/vnet.pytorch/
22.  1000+  [pytorch-fcn](https://github.com/wkentaro/pytorch-fcn): PyTorch 实现完全卷积网络。 
23.  1000-  [WideResNets](https://github.com/xternalz/WideResNet-pytorch): PyTorch实现WideResNets。该实现比官方Torch实现花费更少的GPU内存。实现: https://github.com/szagoruyko/wide-residual-networks .
24.  1000-  [pytorch_highway_networks](https://github.com/c0nn3r/pytorch_highway_networks): PyTorch实现高速公路网络。  
25.  1000-  [pytorch-NeuCom](https://github.com/ypxie/pytorch-NeuCom): Pytorch实现DeepMind的可微神经计算机[论文](http://www.nature.com/articles/nature20101.epdf?author_access_token=ImTXBI8aWbYxYQ51Plys8NRgN0jAjWel9jnR3ZoTv0MggmpDmwljGswxVdeocYSurJ3hxupzWuRNeGvvXnoO8o4jTJcnAyhGuZzXJ1GEaD-Z7E6X_a9R-xqJ9TfJWBqz)。
26.  1000-  [captionGen](https://github.com/eladhoffer/captionGen): 使用PyTorch为图像生成标注。
27.  1000-  [AnimeGAN](https://github.com/jayleicn/animeGAN): 生成对抗网络的PyTorch简单实现，关注于动漫脸谱绘画。
28.  1000-  [Cnn-text classification](https://github.com/Shawn1993/cnn-text-classification-pytorch): PyTorch 实现 [Kim的基于卷积神经网络的句子分类](https://arxiv.org/abs/1408.5882) 论文。
29.  1200+  [deepspeech2](https://github.com/SeanNaren/deepspeech.pytorch): 使用 Baidu Warp-CTC 实现DeepSpeech2。创造一个基于 DeepSpeech2 架构的网络，用 CTC 激活函数训练。
30.  1000-  [seq2seq](https://github.com/MaximumEntropy/Seq2Seq-PyTorch): 包含PyTorch中的Seq2Seq模型。  
31.  1000-  [Asynchronous Advantage Actor-Critic in PyTorch](https://github.com/rarilurelo/pytorch_a3c): PyTorch实现A3C(Asynchronous Advantage Actor-Critic)，论文：[Asynchronous Methods for Deep Reinforcement Learning](https://arxiv.org/pdf/1602.01783v1.pdf)。由于 PyTorch 可以轻松地在多进程内控制共享内存，我们可以轻易实现A3C这样的异步算法。  
32.  1000-  [densenet](https://github.com/bamos/densenet.pytorch): This is a PyTorch 实现 DenseNet-BC 架构，相关论文 [Densely Connected Convolutional Networks](https://arxiv.org/abs/1608.06993)。该实现的 CIFAR-10+ 100层错误率为 4.77 增长率为 12。官方实现和许多第三方库的链接参见 [liuzhuang13/DenseNet](https://github.com/liuzhuang13/DenseNet)。
33.  1000-  [nninit](https://github.com/alykhantejani/nninit): PyTorch神经网络模块的权值初始化方案，这是 [nninit](https://github.com/Kaixhin/nninit) 的流行端口。
34.  1300+  [faster rcnn](https://github.com/longcw/faster_rcnn_pytorch): PyTorch 实现 Faster RCNN。该项目主要基于 py-faster-rcnn 和 TFFRCNN。更多关于 R-CNN 的细节请参考论文 Faster R-CNN：[Towards Real-Time Object Detection with Region Proposal Network](https://arxiv.org/abs/1506.01497)。
35.  1000-  [doomnet](https://github.com/akolishchak/doom-net-pytorch): PyTorch版Doom-net，实现了ViZDoom环境下的RL模型。  
36.  1000-  [flownet](https://github.com/ClementPinard/FlowNetPytorch): 通过Dosovitskiy等完成FlowNet的Pytorch实现。
37.  1000-  [sqeezenet](https://github.com/gsp-27/pytorch_Squeezenet): 在CIFAR10数据集上用PyTorch实现Squeezenet模型，[论文](https://arxiv.org/abs/1602.07360)。
38.  2500+  [WassersteinGAN](https://github.com/martinarjovsky/WassersteinGAN): PyTorch实现[WassersteinGAN](https://arxiv.org/abs/1701.07875)。
39.  1000-  [optnet](https://github.com/locuslab/optnet): 该仓库包含PyTorch源码，重现了论文[OptNet: Differentiable Optimization as a Layer in Neural Networks](https://arxiv.org/abs/1703.00443)中的实验。  
40.  1000-  [qp solver](https://github.com/locuslab/qpth): PyTorch的一个快速和可微分的QP求解器。https://locuslab.github.io/qpth/
41.  1000-  [Continuous Deep Q-Learning with Model-based Acceleration ](https://github.com/ikostrikov/pytorch-naf): [基于模型加速的连续深度Q学习](https://arxiv.org/pdf/1603.00748v1.pdf)的再实现。
42.  1000-  [Learning to learn by gradient descent by gradient descent](https://github.com/ikostrikov/pytorch-meta-optimizer): PyTorch实现[Learning to learn by gradient descent by gradient descent](https://arxiv.org/abs/1606.04474)。
43.  1000-  [fast-neural-style](https://github.com/darkstar112358/fast-neural-style): PyTorch实现fast-neural-style，论文：[Perceptual Losses for Real-Time Style Transfer and Super-Resolution](https://arxiv.org/abs/1603.08155)。
44.  1000-  [PytorchNeuralStyleTransfer](https://github.com/leongatys/PytorchNeuralStyleTransfer): Pytorch中的神经风格转换。
45.  1000-  [Fast Neural Style for Image Style Transform by Pytorch](https://github.com/bengxy/FastNeuralStyle): 使用快速神经风格进行图像风格转换。
46.  1000-  [neural style transfer](https://github.com/alexis-jacq/Pytorch-Tutorials): 通过神经风格算法介绍PyTorch，[Neural-Style algorithm](https://arxiv.org/abs/1508.06576)。
47.  1000-  [VIN_PyTorch_Visdom](https://github.com/zuoxingdong/VIN_PyTorch_Visdom): PyTorch实现价值迭代网络(VIN):干净、简单、模块化。利用Visdom进行可视化。
48.  1200+  [YOLO2](https://github.com/longcw/yolo2-pytorch): PyTorch中的YOLOv2。
49.  1000+  [attention-transfer](https://github.com/szagoruyko/attention-transfer): 通过注意转移改善卷积网络，[ICLR2017会议论文](https://arxiv.org/abs/1612.03928)。
50.  1000-  [SVHNClassifier](https://github.com/potterhsu/SVHNClassifier-PyTorch): PyTorch实现[基于深度卷积神经网络的街景图像多位数识别](https://arxiv.org/pdf/1312.6082.pdf)。
51.  1000-  [pytorch-deform-conv](https://github.com/oeway/pytorch-deform-conv): PyTorch实现可变形卷积(Deformable Convolution)。  
52.  1000-  [BEGAN-pytorch](https://github.com/carpedm20/BEGAN-pytorch): PyTorch实现[边界均衡生成对抗网络（BEGAN）](https://arxiv.org/abs/1703.10717): Boundary Equilibrium Generative Adversarial Networks.  
53.  1000-  [treelstm.pytorch](https://github.com/dasguptar/treelstm.pytorch): PyTorch实现树形结构LSTM。
54.  1000-  [AGE](https://github.com/DmitryUlyanov/AGE): 论文代码，原文：对抗生成编码器网络（[Adversarial Generator-Encoder Networks](http://sites.skoltech.ru/app/data/uploads/sites/25/2017/04/AGE.pdf)）。
55.  1000-  [ResNeXt.pytorch](https://github.com/prlz77/ResNeXt.pytorch): 再现 ResNet-V3 (深度神经网络的聚集残差变换)。
56.  1000-  [pytorch-rl](https://github.com/jingweiz/pytorch-rl): 基于PyTorch和Visdom的深度强化学习。
57.  1000-  [Deep-Leafsnap](https://github.com/sujithv28/Deep-Leafsnap): 对比传统的计算机视觉方法，使用深度神经网络的[LeafSnap](https://neerajkumar.org/base/papers/nk_eccv2012_leafsnap.pdf)能有效提高测试准确率。
58.  11000+  [pytorch-CycleGAN-and-pix2pix](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix): PyTorch 实现图像风格迁移。
59.  1000-  [A3C-PyTorch](https://github.com/onlytailei/A3C-PyTorch):PyTorch 实现 A3C(Advantage async actor-critic)算法。
60.  1000-  [pytorch-value-iteration-networks](https://github.com/kentsommer/pytorch-value-iteration-networks): PyTorch实现价值迭代网络Value Iteration Networks (NIPS 2016 最佳论文)。  
61.  1000-  [PyTorch-Style-Transfer](https://github.com/zhanghang1989/PyTorch-Style-Transfer): PyTorch实现实时转换多风格生成网络。
62.  1000-  [pytorch-deeplab-resnet](https://github.com/isht7/pytorch-deeplab-resnet): PyTorch实现 [DeepLab resnet v2](https://arxiv.org/abs/1606.00915)。
63.  1000-  [pointnet.pytorch](https://github.com/fxia22/pointnet.pytorch): PyTorch实现 "PointNet: 基于深度学习的3D点分类和分割模型" https://arxiv.org/abs/1612.00593  
64.  1700+  [pytorch-playground](https://github.com/aaron-xichen/pytorch-playground): 包含常见的预训练模型和数据集(MNIST, SVHN, CIFAR10, CIFAR100, STL10, AlexNet, VGG16, VGG19, ResNet, Inception, SqueezeNet)**.
65.  1000-  [pytorch-dnc](https://github.com/jingweiz/pytorch-dnc): PyTorch/Visdom实现的神经机器翻译(NTM)&可微神经计算机(DNC)。
66.  1000-  [pytorch_image_classifier](https://github.com/jinfagang/pytorch_image_classifier): 使用PyTorch的最小但实用的图像分类器管道，在ResNet18上进行细化，在自己的小型数据集上获得99%的准确率。
67.  1000-  [mnist-svhn-transfer](https://github.com/yunjey/mnist-svhn-transfer): PyTorch实现CycleGAN和SGAN。
68.  1000-  [pytorch-yolo2](https://github.com/marvis/pytorch-yolo2): pytorch-yolo2
69.  1000-  [dni](https://github.com/andrewliao11/dni.pytorch): PyTorch实现使用合成梯度的解耦神经接口，论文：[Decoupled Neural Interfaces using Synthetic Gradients](https://arxiv.org/abs/1608.05343)。
70.  1000-  [wgan-gp](https://github.com/caogang/wgan-gp): PyTorch实现论文"[Improved Training of Wasserstein GANs](https://arxiv.org/abs/1704.00028v3)".
71.  1000-  [pytorch-seq2seq-intent-parsing](https://github.com/spro/pytorch-seq2seq-intent-parsing):  PyTorch使用seq2seq和注意力模型进行意图分析和空位填充。
72.  1000-  [pyTorch_NCE](https://github.com/demelin/pyTorch_NCE): 复现噪音对比估计算法，论文：[Noise-contrastive estimation: A new estimation principle for unnormalized statistical models](http://proceedings.mlr.press/v9/gutmann10a/gutmann10a.pdf)。
73.  1000-  [molencoder](https://github.com/cxhernandez/molencoder): 分子自动编码器。
74.  1000-  [GAN-weight-norm](https://github.com/stormraiser/GAN-weight-norm): 论文代码，"[生成对抗网络中批量和权重归一化的影响](https://arxiv.org/abs/1704.03971)"
75.  1000-  [lgamma](https://github.com/rachtsingh/lgamma): 实现polygamma、lgamma和beta函数。
76.  1000-  [bigBatch](https://github.com/eladhoffer/bigBatch): 论文代码，论文：“[训练越久，泛化越好：关闭神经网络大批量训练的泛化间隙](https://arxiv.org/abs/1705.08741)”。
77.  1000-  [rl_a3c_pytorch](https://github.com/dgriff777/rl_a3c_pytorch): 针对 Atari 2600 的强化学习，实现了 A3C LSTM 。
78.  1000-  [pytorch-retraining](https://github.com/ahirner/pytorch-retraining): PyTorch动物园模型转移学习(torchvision)。
79.  1000-  [nmp_qc](https://github.com/priba/nmp_qc): 用于计算机视觉的神经消息传递。
80.  1000+  [grad-cam](https://github.com/jacobgil/pytorch-grad-cam): PyTorch 实现[Grad-CAM](https://arxiv.org/pdf/1610.02391v1.pdf)。
81.  1000-  [pytorch-trpo](https://github.com/mjacar/pytorch-trpo): PyTorch s实现置信域策略优化（[Trust Region Policy Optimization (TRPO)](https://arxiv.org/abs/1502.05477)）。
82.  1000-  [pytorch-explain-black-box](https://github.com/jacobgil/pytorch-explain-black-box): PyTorch通过有意义扰动实现黑箱的可解释性解释，[论文](https://arxiv.org/abs/1704.03296)。
83.  1000-  [vae_vpflows](https://github.com/jmtomczak/vae_vpflows): 凸组合线性IAF与Householder流 https://jmtomczak.github.io/deebmed.html 。
84.  1000-  [relational-networks](https://github.com/kimhc6028/relational-networks): Pytorch实现"[用一个简单的神经网络模块来做关系推理](https://arxiv.org/pdf/1706.01427.pdf)"(关系网络)。
85.  1000-  [vqa.pytorch](https://github.com/Cadene/vqa.pytorch): 视觉问答。
86.  1200+  [end-to-end-negotiator](https://github.com/facebookresearch/end-to-end-negotiator): 成交还是不成交？谈判对话的端到端学习。
87.  1000-  [odin-pytorch](https://github.com/ShiyuLiang/odin-pytorch): 神经网络失配实例的原则性检测。
88.  1000-  [FreezeOut](https://github.com/ajbrock/FreezeOut): 一种通过逐步冻结层加速神经网络训练的简单技术。
89.  1000-  [ARAE](https://github.com/jakezhaojb/ARAE): 论文代码，"[对抗性正则化的自动编码器, ARAE](https://arxiv.org/abs/1706.04223)"。
90.  1000-  [forward-thinking-pytorch](https://github.com/kimhc6028/forward-thinking-pytorch): PyTorch实现"[前向思考：一次一层地建立和训练神经网络](https://arxiv.org/pdf/1706.02480.pdf)"。  
91.  1000-  [context_encoder_pytorch](https://github.com/BoyuanJiang/context_encoder_pytorch): PyTorch实现上下文编码器(Context Encoders)，可用于图像修复。
92.  3600+  [attention-is-all-you-need-pytorch](https://github.com/jadore801120/attention-is-all-you-need-pytorch): PyTorch在"Attention is All You Need"中实现转换模型，https://github.com/thnkim/OpenFacePytorch。
93.  1000-  [OpenFacePytorch](https://github.com/thnkim/OpenFacePytorch): 使用 OpenFace's nn4.small2.v1.t7 模型的PyTorch模块。
94.  1000-  [neural-combinatorial-rl-pytorch](https://github.com/pemami4911/neural-combinatorial-rl-pytorch):  PyTorch 实现"[通过强化学习实现神经组合优化](https://arxiv.org/abs/1611.09940)"。
95.  1000-  [pytorch-nec](https://github.com/mjacar/pytorch-nec): PyTorch实现神经情景控制([NEC，Neural Episodic Control](https://arxiv.org/abs/1703.01988))。
96.  1000-  [seq2seq.pytorch](https://github.com/eladhoffer/seq2seq.pytorch): 使用PyTorch进行Sequence-to-Sequence学习。
97.  1000-  [Pytorch-Sketch-RNN](https://github.com/alexis-jacq/Pytorch-Sketch-RNN): PyTorch实现 “[A Neural Representation of Sketch Drawings](arxiv.org/abs/1704.03477)”。
98.  1000-  [pytorch-pruning](https://github.com/jacobgil/pytorch-pruning): PyTorch实现 [1611.06440] [用于资源有效推理的剪枝卷积神经网络](https://arxiv.org/abs/1611.06440)
99.  1000-  [DrQA](https://github.com/hitvoice/DrQA): PyTorch实现自动阅读维基百科并回答开放领域问题。
100.  1000-  [YellowFin_Pytorch](https://github.com/JianGoForIt/YellowFin_Pytorch): 基于动量梯度下降（momentum SGD）的自动调优优化器，无需手动指定学习速率和动量。
101.  1000-  [samplernn-pytorch](https://github.com/deepsound-project/samplernn-pytorch): PyTorch实现SampleRNN: 一种无条件端到端神经音频生成模型。
102.  1000-  [AEGeAN](https://github.com/tymokvo/AEGeAN): 基于AE稳定的更深的深度卷积生成对抗网络(DCGAN, Deep Convolution Generative Adversarial Networks)。
103.  1000-  [/pytorch-SRResNet](https://github.com/twtygqyy/pytorch-SRResNet): PyTorch实现“[基于生成对抗网络的实感单幅图像超分辨率](https://arxiv.org/abs/1609.04802)”。
104.  1000-  [vsepp](https://github.com/fartashf/vsepp): 论文代码，"[VSE++:使用难分样本(Hard Negative)改善视觉语义联合嵌入](https://arxiv.org/abs/1707.05612)"。
105.  1000-  [Pytorch-DPPO](https://github.com/alexis-jacq/Pytorch-DPPO): Pytorch实现分布式近端策略优化([Distributed Proximal Policy Optimization](https://arxiv.org/abs/1707.02286))。
106.  1500+  [UNIT](https://github.com/mingyuliutw/UNIT): 无监督的图像到图像转换网络，[论文](https://arxiv.org/abs/1703.00848)。
107.  1100+  [efficient_densenet_pytorch](https://github.com/gpleiss/efficient_densenet_pytorch): DenseNets的内存高效实现。
108.  1000-  [tsn-pytorch](https://github.com/yjxiong/tsn-pytorch): PyTorch实现时间分割网络(TSN, Temporal Segment Networks)。
109.  1000-  [SMASH](https://github.com/ajbrock/SMASH): [SMASH](https://arxiv.org/abs/1708.05344)，一种高效地探索神经体系结构的实验技术。
110.  1000-  [pytorch-retinanet](https://github.com/kuangliu/pytorch-retinanet): RetinaNet。
111.  1000-  [biogans](https://github.com/aosokin/biogans): 实现 ICCV 2017 论文 "[利用GANs进行生物图像合成](https://arxiv.org/abs/1708.04692)"。
112.  null  [Semantic Image Synthesis via Adversarial Learning]( https://github.com/woozzu/dong_iccv_2017): PyTorch 实现 ICCV 2017 论文 "[基于对抗学习的语义图像合成](https://arxiv.org/abs/1707.06873)"。
113.  1000-  [fmpytorch](https://github.com/jmhessel/fmpytorch): PyTorch在Cython中实现分析机（Factorization Machine）模块。
114.  1000-  [ORN](https://github.com/ZhouYanzhao/ORN): PyTorch 实现 CVPR 2017 论文 "[Oriented Response Networks](https://arxiv.org/pdf/1701.01833.pdf)"。
115.  1000-  [pytorch-maml](https://github.com/katerakelly/pytorch-maml): PyTorch实现 [MAML](https://arxiv.org/abs/1703.03400)（Model-Agnostic Meta-Learning，与模型无关的元学习）。
116.  1900+  [pytorch-generative-model-collections](https://github.com/znxlwm/pytorch-generative-model-collections): PyTorch中的各种生成模型集合。
117.  1000-  [vqa-winner-cvprw-2017](https://github.com/markdtw/vqa-winner-cvprw-2017): Pytorch 实现 CVPR'17 VQA( Visual Question Answer，视觉问答) 挑战冠军。
118.  1000-  [tacotron_pytorch](https://github.com/r9y9/tacotron_pytorch):  PyTorch 实现 Tacotron 语音合成模型。
119.  1000-  [pspnet-pytorch](https://github.com/Lextal/pspnet-pytorch): PyTorch 实现 PSPNet 语义分割网络。
120.  1000-  [LM-LSTM-CRF](https://github.com/LiyuanLucasLiu/LM-LSTM-CRF): 《Empower Sequence Labeling with Task-Aware Language Model》 http://arxiv.org/abs/1709.04109
121.  3500+  [face-alignment](https://github.com/1adrianb/face-alignment): 使用PyTorch构建2D和3D人脸对齐库。
122.  1000-  [DepthNet](https://github.com/ClementPinard/DepthNet): PyTorch 在Still Box数据集上训练DepthNet。
123.  1100+  [EDSR-PyTorch](https://github.com/thstkdgus35/EDSR-PyTorch): 论文《Enhanced Deep Residual Networks for Single Image Super-Resolution》的PyTorch实现版本。 (CVPRW 2017)
124.  1000-  [e2c-pytorch](https://github.com/ethanluoyc/e2c-pytorch): E2C，Embed to Control 实现。
125.  1900+  [3D-ResNets-PyTorch](https://github.com/kenshohara/3D-ResNets-PyTorch): 基于3D残差网络的动作识别。
126.  1000-  [bandit-nmt](https://github.com/khanhptnk/bandit-nmt): EMNLP 2017 论文《Reinforcement Learning for Bandit Neural Machine Translation with Simulated Human Feedback》的代码,，改论文在神经编解码模型的基础上实现了A2C算法，并在模拟噪声激励下对组合进行了基准测试。
127.  1700+  [pytorch-a2c-ppo-acktr](https://github.com/ikostrikov/pytorch-a2c-ppo-acktr): PyTorch 实现 Advantage Actor Critic (A2C), Proximal Policy Optimization (PPO，近端策略优化) 和可扩展信赖域（Trust Region）方法，这些算法使用 Kronecker因子近似（ACKTR）和生成对抗模仿学习（GAIL）实现，可用于深度强化学习。
128.  1000-  [zalando-pytorch](https://github.com/baldassarreFe/zalando-pytorch): [Fashion-MNIST](https://github.com/zalandoresearch/fashion-mnist)数据集上的各种实验。
129.  1000-  [sphereface_pytorch](https://github.com/clcarwin/sphereface_pytorch): PyTorch实现SphereFace，人脸识别相关，https://arxiv.org/abs/1704.08063 。
130.  1000-  [Categorical DQN](https://github.com/floringogianu/categorical-dqn): PyTorch 版 Categorical DQN，该模型来自论文《[A Distributional Perspective on Reinforcement Learning](https://arxiv.org/abs/1707.06887)》。
131.  1000-  [pytorch-ntm](https://github.com/loudinthecloud/pytorch-ntm): 神经网络图灵机。
132.  null  [mask_rcnn_pytorch](https://github.com/felixgwu/mask_rcnn_pytorch): Mask RCNN in PyTorch.
133.  1000-  [graph_convnets_pytorch](https://github.com/xbresson/graph_convnets_pytorch): PyTorch 实现图卷积神经网络，NIPS’16。
134.  1400+  [pytorch-faster-rcnn](https://github.com/ruotianluo/pytorch-faster-rcnn): PyTorch实现 faster RCNN 检测框架，基于 Xinlei Chen 的[tf-faster-rcnn](https://github.com/endernewton/tf-faster-rcnn)，已不再维护。
135.  1000-  [torchMoji](https://github.com/huggingface/torchMoji): A pyTorch implementation of the DeepMoji model: state-of-the-art deep learning model for analyzing sentiment, emotion, sarcasm etc.
136.  3000+  [semantic-segmentation-pytorch](https://github.com/hangzhaomit/semantic-segmentation-pytorch): 在[MIT ADE20K dataset](http://sceneparsing.csail.mit.edu)数据集上实现语义分割/场景解析。
137.  1100+  [pytorch-qrnn](https://github.com/salesforce/pytorch-qrnn): PyTorch implementation of the Quasi-Recurrent Neural Network - up to 16 times faster than NVIDIA's cuDNN LSTM
138.  1000-  [pytorch-sgns](https://github.com/theeluwin/pytorch-sgns): Skipgram Negative Sampling in PyTorch.
139.  1000-  [SfmLearner-Pytorch ](https://github.com/ClementPinard/SfmLearner-Pytorch): Pytorch version of SfmLearner from Tinghui Zhou et al.
140.  1000-  [deformable-convolution-pytorch](https://github.com/1zb/deformable-convolution-pytorch): PyTorch实现可变形卷积。
141.  1000-  [skip-gram-pytorch](https://github.com/fanglanting/skip-gram-pytorch): A complete pytorch implementation of skipgram model (with subsampling and negative sampling). The embedding result is tested with Spearman's rank correlation.
142.  1000-  [stackGAN-v2](https://github.com/hanzhanggit/StackGAN-v2): Pytorch implementation for reproducing StackGAN_v2 results in the paper StackGAN++: Realistic Image Synthesis with Stacked Generative Adversarial Networks by Han Zhang*, Tao Xu*, Hongsheng Li, Shaoting Zhang, Xiaogang Wang, Xiaolei Huang, Dimitris Metaxas.
143.  1000-  [self-critical.pytorch](https://github.com/ruotianluo/self-critical.pytorch): 非官方，PyTorch实现基于 self-critical 序列训练的图像标注。
144.  2200+  [pygcn](https://github.com/tkipf/pygcn): 图卷积网络。
145.  1000-  [dnc](https://github.com/ixaxaar/pytorch-dnc): 可微神经计算机、稀疏存取存储器与稀疏可微神经计算机。
146.  1000-  [prog_gans_pytorch_inference](https://github.com/ptrblck/prog_gans_pytorch_inference): PyTorch inference for "Progressive Growing of GANs" with CelebA snapshot.
147.  1000-  [pytorch-capsule](https://github.com/timomernick/pytorch-capsule): Pytorch implementation of Hinton's Dynamic Routing Between Capsules.
148.  1000-  [PyramidNet-PyTorch](https://github.com/dyhan0920/PyramidNet-PyTorch): A PyTorch implementation for PyramidNets (Deep Pyramidal Residual Networks, arxiv.org/abs/1610.02915)
149.  1000-  [radio-transformer-networks](https://github.com/gram-ai/radio-transformer-networks): A PyTorch implementation of Radio Transformer Networks from the paper "An Introduction to Deep Learning for the Physical Layer". arxiv.org/abs/1702.00832
150.  1000-  [honk](https://github.com/castorini/honk): PyTorch reimplementation of Google's TensorFlow CNNs for keyword spotting.
151.  1000-  [DeepCORAL](https://github.com/SSARCandy/DeepCORAL): A PyTorch implementation of 'Deep CORAL: Correlation Alignment for Deep Domain Adaptation.', ECCV 2016
152.  1000-  [pytorch-pose](https://github.com/bearpaw/pytorch-pose): PyTorch工具包，用于2D人体姿态估计。
153.  1000-  [lang-emerge-parlai](https://github.com/karandesai-96/lang-emerge-parlai): Implementation of EMNLP 2017 Paper "Natural Language Does Not Emerge 'Naturally' in Multi-Agent Dialog" using PyTorch and ParlAI
154.  1000-  [Rainbow](https://github.com/Kaixhin/Rainbow): Rainbow: Combining Improvements in Deep Reinforcement Learning 
155.  1000-  [pytorch_compact_bilinear_pooling v1](https://github.com/gdlg/pytorch_compact_bilinear_pooling): This repository has a pure Python implementation of Compact Bilinear Pooling and Count Sketch for PyTorch.
156.  1000-  [CompactBilinearPooling-Pytorch v2](https://github.com/DeepInsight-PCALab/CompactBilinearPooling-Pytorch): (Yang Gao, et al.) A Pytorch Implementation for Compact Bilinear Pooling.
157.  1000-  [FewShotLearning](https://github.com/gitabcworld/FewShotLearning): Pytorch implementation of the paper "Optimization as a Model for Few-Shot Learning"
158.  1000-  [meProp](https://github.com/jklj077/meProp): Codes for "meProp: Sparsified Back Propagation for Accelerated Deep Learning with Reduced Overfitting".
159.  1000-  [SFD_pytorch](https://github.com/clcarwin/SFD_pytorch): 单镜头尺度不变人脸检测器。
160.  1000-  [GradientEpisodicMemory](https://github.com/facebookresearch/GradientEpisodicMemory): Continuum Learning with GEM: Gradient Episodic Memory. https://arxiv.org/abs/1706.08840
161.  1500+  [DeblurGAN](https://github.com/KupynOrest/DeblurGAN): Pytorch implementation of the paper DeblurGAN: Blind Motion Deblurring Using Conditional Adversarial Networks.
162.  4400+  [StarGAN](https://github.com/yunjey/StarGAN): StarGAN: 多领域图像转换 GAN 网络，https://arxiv.org/abs/1711.09020 。
163.  1000-  [CapsNet-pytorch](https://github.com/adambielski/CapsNet-pytorch): PyTorch 实现 NIPS 2017 论文 “[胶囊间的动态路由](https://arxiv.org/abs/1710.09829)”。
164.  1000-  [CondenseNet](https://github.com/ShichenLiu/CondenseNet): CondenseNet: 面向移动设备的轻量级 CNN。
165.  5600+  [deep-image-prior](https://github.com/DmitryUlyanov/deep-image-prior): 基于神经网络的图像修复，无学习过程。
166.  1000-  [deep-head-pose](https://github.com/natanielruiz/deep-head-pose): 使用PyTorch进行深度学习头部姿势估计。
167.  1000-  [Random-Erasing](https://github.com/zhunzhong07/Random-Erasing): 论文代码，论文："[随机擦除数据增强](https://arxiv.org/abs/1708.04896)"。
168.  1000-  [FaderNetworks](https://github.com/facebookresearch/FaderNetworks): Fader Networks: 通过滑动属性重构图像 - NIPS 2017，https://arxiv.org/pdf/1706.00409.pdf 。
169.  1700+  [FlowNet 2.0](https://github.com/NVIDIA/flownet2-pytorch): FlowNet 2.0: 深度网络中光流估计的演化。
170.  4300+  [pix2pixHD](https://github.com/NVIDIA/pix2pixHD): 利用条件 GANs 合成和处理 HD 高清图像的 PyTorch 实现，https://arxiv.org/pdf/1711.11585.pdf。
171.  1000-  [pytorch-smoothgrad](https://github.com/pkdn/pytorch-smoothgrad): SmoothGrad通过增加噪声来去除噪声。
172.  1000-  [RetinaNet](https://github.com/c0nn3r/RetinaNet): RetinaNe实现。
173.  4800+  [faster-rcnn.pytorch](https://github.com/jwyang/faster-rcnn.pytorch): This project is a faster faster R-CNN implementation, aimed to accelerating the training of faster R-CNN object detection models. 
174.  1000-  [mixup_pytorch](https://github.com/leehomyc/mixup_pytorch): A PyTorch implementation of the paper Mixup: Beyond Empirical Risk Minimization in PyTorch.
175.  1000-  [inplace_abn](https://github.com/mapillary/inplace_abn): In-Place Activated BatchNorm for Memory-Optimized Training of DNNs
176.  1000-  [pytorch-pose-hg-3d](https://github.com/xingyizhou/pytorch-pose-hg-3d): PyTorch implementation for 3D human pose estimation
177.  1000-  [nmn-pytorch](https://github.com/HarshTrivedi/nmn-pytorch): Neural Module Network for VQA in Pytorch.
178.  1000-  [bytenet](https://github.com/kefirski/bytenet): Pytorch implementation of bytenet from "Neural Machine Translation in Linear Time" paper
179.  1000-  [bottom-up-attention-vqa](https://github.com/hengyuan-hu/bottom-up-attention-vqa): vqa, bottom-up-attention, pytorch
180.  1000-  [yolo2-pytorch](https://github.com/ruiminshen/yolo2-pytorch): The YOLOv2 is one of the most popular one-stage object detector. This project adopts PyTorch as the developing framework to increase productivity, and utilize ONNX to convert models into Caffe 2 to benifit engineering deployment.
181.  1000-  [reseg-pytorch](https://github.com/Wizaron/reseg-pytorch): PyTorch 实现ReSeg。 (https://arxiv.org/pdf/1511.07053.pdf)
182.  1000-  [binary-stochastic-neurons](https://github.com/Wizaron/binary-stochastic-neurons): Binary Stochastic Neurons in PyTorch.
183.  1000-  [pytorch-pose-estimation](https://github.com/DavexPro/pytorch-pose-estimation): PyTorch Implementation of Realtime Multi-Person Pose Estimation project.
184.  1000-  [interaction_network_pytorch](https://github.com/higgsfield/interaction_network_pytorch): Pytorch Implementation of Interaction Networks for Learning about Objects, Relations and Physics.
185.  1000-  [NoisyNaturalGradient](https://github.com/wlwkgus/NoisyNaturalGradient): Pytorch Implementation of paper "Noisy Natural Gradient as Variational Inference". 
186.  1000-  [ewc.pytorch](https://github.com/moskomule/ewc.pytorch): An implementation of Elastic Weight Consolidation (EWC), proposed in James Kirkpatrick et al. Overcoming catastrophic forgetting in neural networks 2016(10.1073/pnas.1611835114).
187.  1000-  [pytorch-zssr](https://github.com/jacobgil/pytorch-zssr): PyTorch implementation of 1712.06087 "Zero-Shot" Super-Resolution using Deep Internal Learning
188.  1000-  [deep_image_prior](https://github.com/atiyo/deep_image_prior): 基于未训练神经网络的图像重建算法实现。算法：[Deep Image Prior](https://arxiv.org/abs/1711.10925)。
189.  1000-  [pytorch-transformer](https://github.com/leviswind/pytorch-transformer): PyTorch实现论文[Attention Is All You Need](https://arxiv.org/abs/1706.03762)。
190.  1000-  [DeepRL-Grounding](https://github.com/devendrachaplot/DeepRL-Grounding): PyTorch实现AAAI-18论文[Gated-Attention Architectures for Task-Oriented Language Grounding](https://arxiv.org/abs/1706.07230)。
191.  1000-  [deep-forecast-pytorch](https://github.com/Wizaron/deep-forecast-pytorch): 使用LSTMs进行风速预测，论文：[Deep Forecast: Deep Learning-based Spatio-Temporal Forecasting](arxiv.org/pdf/1707.08110.pdf)。
192.  1000-  [cat-net](https://github.com/utiasSTARS/cat-net):  正则外观变换（[Canonical Appearance Transformations](https://arxiv.org/abs/1709.03009)）
193.  1000-  [minimal_glo](https://github.com/tneumann/minimal_glo): Minimal PyTorch implementation of Generative Latent Optimization from the paper "Optimizing the Latent Space of Generative Networks"
194.  1000-  [LearningToCompare-Pytorch](https://github.com/dragen1860/LearningToCompare-Pytorch): Pytorch Implementation for Paper: Learning to Compare: Relation Network for Few-Shot Learning. 
195.  1200+  [poincare-embeddings](https://github.com/facebookresearch/poincare-embeddings): PyTorch implementation of the NIPS-17 paper "Poincaré Embeddings for Learning Hierarchical Representations". 
196.  null  [pytorch-trpo(Hessian-vector product version)](https://github.com/ikostrikov/pytorch-trpo): This is a PyTorch implementation of "Trust Region Policy Optimization (TRPO)" with exact Hessian-vector product instead of finite differences approximation.
197.  1000-  [ggnn.pytorch](https://github.com/JamesChuanggg/ggnn.pytorch): A PyTorch Implementation of Gated Graph Sequence Neural Networks (GGNN). 
198.  1000-  [visual-interaction-networks-pytorch](https://github.com/Mrgemy95/visual-interaction-networks-pytorch): This's an implementation of deepmind Visual Interaction Networks paper using pytorch
199.  1000-  [adversarial-patch](https://github.com/jhayes14/adversarial-patch): PyTorch实现对抗补丁。
200.  1000-  [Prototypical-Networks-for-Few-shot-Learning-PyTorch](https://github.com/orobix/Prototypical-Networks-for-Few-shot-Learning-PyTorch): Implementation of Prototypical Networks for Few Shot Learning (arxiv.org/abs/1703.05175) in Pytorch
201.  1000-  [Visual-Feature-Attribution-Using-Wasserstein-GANs-Pytorch](https://github.com/orobix/Visual-Feature-Attribution-Using-Wasserstein-GANs-Pytorch): Implementation of Visual Feature Attribution using Wasserstein GANs (arxiv.org/abs/1711.08998) in PyTorch.
202.  1000-  [PhotographicImageSynthesiswithCascadedRefinementNetworks-Pytorch](https://github.com/Blade6570/PhotographicImageSynthesiswithCascadedRefinementNetworks-Pytorch): 用级联优化网络生成照片级图像，https://arxiv.org/abs/1707.09405 。
203.  2100+  [ENAS-pytorch](https://github.com/carpedm20/ENAS-pytorch): PyTorch实现"[基于参数共享的高效神经网络结构搜索](https://arxiv.org/abs/1802.03268)"。
204.  1000-  [Neural-IMage-Assessment](https://github.com/kentsyx/Neural-IMage-Assessment): 神经图片评估，https://arxiv.org/abs/1709.05424 。
205.  1000-  [proxprop](https://github.com/tfrerix/proxprop): 近端回传(Proximal Backpropagation) - 隐式梯度代替显式梯度的神经网络训练算法。
206.  10100+  [FastPhotoStyle](https://github.com/NVIDIA/FastPhotoStyle): 照片级逼真的图像风格化的一个封闭解。
207.  1000-  [Deep-Image-Analogy-PyTorch](https://github.com/Ben-Louis/Deep-Image-Analogy-PyTorch): 基于PyTorch的深度图像模拟的Python实现。
208.  1800+  [Person-reID_pytorch](https://github.com/layumi/Person_reID_baseline_pytorch): 行人再识别Person-reID的PyTorch实现。
209.  1000-  [pt-dilate-rnn](https://github.com/zalandoresearch/pt-dilate-rnn): 空洞递归神经网络（Dilated RNNs）。
210.  1000-  [pytorch-i-revnet](https://github.com/jhjacobsen/pytorch-i-revnet): Pytorch实现i-RevNets。
211.  1000-  [OrthNet](https://github.com/Orcuslc/OrthNet): TensorFlow、PyTorch和Numpy层生成正交多项式。
212.  1000-  [DRRN-pytorch](https://github.com/jt827859032/DRRN-pytorch): "[超分辨率的深递归残差网络(DRRN)](http://cvlab.cse.msu.edu/pdfs/Tai_Yang_Liu_CVPR2017.pdf)", CVPR 2017
213.  1000-  [shampoo.pytorch](https://github.com/moskomule/shampoo.pytorch): Shampoo算法实现。
214.  1000-  [Neural-IMage-Assessment 2](https://github.com/truskovskiyk/nima.pytorch): 神经图片评估，https://arxiv.org/abs/1709.05424 。
215.  2100+  [TCN](https://github.com/locuslab/TCN): Sequence modeling benchmarks and temporal convolutional networks locuslab/TCN
216.  1000-  [DCC](https://github.com/shahsohil/DCC): This repository contains the source code and data for reproducing results of Deep Continuous Clustering paper.
217.  1000-  [packnet](https://github.com/arunmallya/packnet): Code for PackNet: Adding Multiple Tasks to a Single Network by Iterative Pruning arxiv.org/abs/1711.05769
218.  1000-  [PyTorch-progressive_growing_of_gans](https://github.com/github-pengge/PyTorch-progressive_growing_of_gans): PyTorch implementation of Progressive Growing of GANs for Improved Quality, Stability, and Variation.
219.  1000-  [nonauto-nmt](https://github.com/salesforce/nonauto-nmt): PyTorch Implementation of "Non-Autoregressive Neural Machine Translation"
220.  5500+  [PyTorch-GAN](https://github.com/eriklindernoren/PyTorch-GAN): PyTorch implementations of Generative Adversarial Networks.
221.  1000-  [PyTorchWavelets](https://github.com/tomrunia/PyTorchWavelets): PyTorch implementation of the wavelet analysis found in Torrence and Compo (1998)
222.  1000-  [pytorch-made](https://github.com/karpathy/pytorch-made): MADE (Masked Autoencoder Density Estimation) implementation in PyTorch
223.  1000-  [VRNN](https://github.com/emited/VariationalRecurrentNeuralNetwork): Pytorch implementation of the Variational RNN (VRNN), from A Recurrent Latent Variable Model for Sequential Data.
224.  1000-  [flow](https://github.com/emited/flow): Pytorch implementation of ICLR 2018 paper Deep Learning for Physical Processes: Integrating Prior Scientific Knowledge.
225.  1200+  [deepvoice3_pytorch](https://github.com/r9y9/deepvoice3_pytorch): PyTorch实现基于卷积神经网络的语音合成模型。
226.  1000-  [psmm](https://github.com/elanmart/psmm): imlementation of the the Pointer Sentinel Mixture Model, as described in the paper by Stephen Merity et al.
227.  1400+  [tacotron2](https://github.com/NVIDIA/tacotron2): Tacotron 2 - PyTorch implementation with faster-than-realtime inference.
228.  1000-  [AccSGD](https://github.com/rahulkidambi/AccSGD): Implements pytorch code for the Accelerated SGD algorithm.
229.  1000-  [QANet-pytorch](https://github.com/hengruo/QANet-pytorch): an implementation of QANet with PyTorch (EM/F1 = 70.5/77.2 after 20 epoches for about 20 hours on one 1080Ti card.)
230.  1000-  [ConvE](https://github.com/TimDettmers/ConvE): Convolutional 2D Knowledge Graph Embeddings
231.  1000-  [Structured-Self-Attention](https://github.com/kaushalshetty/Structured-Self-Attention): Implementation for the paper A Structured Self-Attentive Sentence Embedding, which is published in ICLR 2017: arxiv.org/abs/1703.03130 .
232.  1000-  [graphsage-simple](https://github.com/williamleif/graphsage-simple): Simple reference implementation of GraphSAGE.
233.  2600+  [Detectron.pytorch](https://github.com/roytseng-tw/Detectron.pytorch): A pytorch implementation of Detectron. Both training from scratch and inferring directly from pretrained Detectron weights are available.
234.  1000-  [R2Plus1D-PyTorch](https://github.com/irhumshafkat/R2Plus1D-PyTorch): PyTorch implementation of the R2Plus1D convolution based ResNet architecture described in the paper "A Closer Look at Spatiotemporal Convolutions for Action Recognition"
235.  1000-  [StackNN](https://github.com/viking-sudo-rm/StackNN): A PyTorch implementation of differentiable stacks for use in neural networks.
236.  1000-  [translagent](https://github.com/facebookresearch/translagent): Code for Emergent Translation in Multi-Agent Communication.
237.  1000-  [ban-vqa](https://github.com/jnhwkim/ban-vqa): Bilinear attention networks for visual question answering. 
238.  1100+  [pytorch-openai-transformer-lm](https://github.com/huggingface/pytorch-openai-transformer-lm): This is a PyTorch implementation of the TensorFlow code provided with OpenAI's paper "Improving Language Understanding by Generative Pre-Training" by Alec Radford, Karthik Narasimhan, Tim Salimans and Ilya Sutskever.
239.  1000-  [T2F](https://github.com/akanimax/T2F): 使用深度学习进行Text-to-Face生成。该项目结合了[StackGAN](https://arxiv.org/abs/1710.10916)和[ProGAN](https://arxiv.org/abs/1710.10196)，这两个模型可以基于文字描述合成人脸。
240.  1000-  [pytorch - fid](https://github.com/mseitzer/pytorch-fid): A Port of Fréchet Inception Distance (FID score) to PyTorch
241.  1000-  [vae_vpflows](https://github.com/jmtomczak/vae_vpflows):Code in PyTorch for the convex combination linear IAF and the Householder Flow, J.M. Tomczak & M. Welling jmtomczak.github.io/deebmed.html
242.  1000-  [CoordConv-pytorch](https://github.com/mkocabas/CoordConv-pytorch): Pytorch implementation of CoordConv introduced in 'An intriguing failing of convolutional neural networks and the CoordConv solution' paper. (arxiv.org/pdf/1807.03247.pdf)
243.  1000-  [SDPoint](https://github.com/xternalz/SDPoint): Implementation of "Stochastic Downsampling for Cost-Adjustable Inference and Improved Regularization in Convolutional Networks", published in CVPR 2018. 
244.  1000-  [SRDenseNet-pytorch](https://github.com/wxywhu/SRDenseNet-pytorch): 极深网络，SRDenseNet-pytorch，论文：[基于密集跳跃连接的图像超分辨率（ICCV_2017）](http://openaccess.thecvf.com/content_ICCV_2017/papers/Tong_Image_Super-Resolution_Using_ICCV_2017_paper.pdf)。
245.  1000-  [GAN_stability](https://github.com/LMescheder/GAN_stability): Code for paper "Which Training Methods for GANs do actually Converge? (ICML 2018)"
246.  1000-  [Mask-RCNN](https://github.com/wannabeOG/Mask-RCNN): A PyTorch implementation of the architecture of Mask RCNN, serves as an introduction to working with PyTorch
247.  1000-  [pytorch-coviar](https://github.com/chaoyuaw/pytorch-coviar): Compressed Video Action Recognition
248.  1000-  [PNASNet.pytorch](https://github.com/chenxi116/PNASNet.pytorch): PyTorch implementation of PNASNet-5 on ImageNet. 
249.  1000-  [NALU-pytorch](https://github.com/kevinzakka/NALU-pytorch): Basic pytorch implementation of NAC/NALU from Neural Arithmetic Logic Units arxiv.org/pdf/1808.00508.pdf
250.  1000-  [LOLA_DiCE](https://github.com/alexis-jacq/LOLA_DiCE): Pytorch 使用[DiCE](arxiv.org/abs/1802.05098)实现[LOLA](arxiv.org/abs/1709.04326)。
251.  1000-  [generative-query-network-pytorch](https://github.com/wohlert/generative-query-network-pytorch): Generative Query Network (GQN) in PyTorch as described in "Neural Scene Representation and Rendering"
252.  1000-  [pytorch_hmax](https://github.com/wmvanvliet/pytorch_hmax): 在PyTorch中实现[HMAX(Hierarchical Model and X)](https://maxlab.neuro.georgetown.edu/hmax.html#inside)视觉模型。
253.  1000-  [FCN-pytorch-easiest](https://github.com/yunlongdong/FCN-pytorch-easiest): trying to be the most easiest and just get-to-use pytorch implementation of FCN (Fully Convolotional Networks)
254.  1000-  [transducer](https://github.com/awni/transducer): A Fast Sequence Transducer Implementation with PyTorch Bindings.
255.  1000-  [AVO-pytorch](https://github.com/artix41/AVO-pytorch): Implementation of Adversarial Variational Optimization in PyTorch.
256.  1000-  [HCN-pytorch](https://github.com/huguyuehuhu/HCN-pytorch): A pytorch reimplementation of { Co-occurrence Feature Learning from Skeleton Data for Action Recognition and Detection with Hierarchical Aggregation }.
257.  1000-  [binary-wide-resnet](https://github.com/szagoruyko/binary-wide-resnet): PyTorch implementation of Wide Residual Networks with 1-bit weights by McDonnel (ICLR 2018)
258.  1000-  [piggyback](https://github.com/arunmallya/piggyback): Code for Piggyback: Adapting a Single Network to Multiple Tasks by Learning to Mask Weights arxiv.org/abs/1801.06519
259.  7100+  [vid2vid](https://github.com/NVIDIA/vid2vid): Pytorch implementation of our method for high-resolution (e.g. 2048x1024) photorealistic video-to-video translation.
260.  1000-  [poisson-convolution-sum](https://github.com/cranmer/poisson-convolution-sum): Implements an infinite sum of poisson-weighted convolutions
261.  1000-  [tbd-nets](https://github.com/davidmascharka/tbd-nets): PyTorch implementation of "Transparency by Design: Closing the Gap Between Performance and Interpretability in Visual Reasoning" arxiv.org/abs/1803.05268 
262.  1000-  [attn2d](https://github.com/elbayadm/attn2d): Pervasive Attention: 2D Convolutional Networks for Sequence-to-Sequence Prediction
263.  3500+  [yolov3](https://github.com/ultralytics/yolov3): YOLOv3: 训练和推断，https://www.ultralytics.com 。
264.  1000-  [deep-dream-in-pytorch](https://github.com/duc0/deep-dream-in-pytorch): Pytorch implementation of the DeepDream computer vision algorithm. 
265.  1000-  [pytorch-flows](https://github.com/ikostrikov/pytorch-flows): PyTorch implementations of algorithms for density estimation
266.  1000-  [quantile-regression-dqn-pytorch](https://github.com/ars-ashuha/quantile-regression-dqn-pytorch): Quantile Regression DQN a Minimal Working Example
267.  1000-  [relational-rnn-pytorch](https://github.com/L0SG/relational-rnn-pytorch): An implementation of DeepMind's Relational Recurrent Neural Networks in PyTorch.
268.  1000-  [DEXTR-PyTorch](https://github.com/scaelles/DEXTR-PyTorch): 深度极端切割，http://www.vision.ee.ethz.ch/~cvlsegmentation/dextr 。
269.  1000-  [PyTorch_GBW_LM](https://github.com/rdspring1/PyTorch_GBW_LM): PyTorch Language Model for Google Billion Word Dataset.
270.  1000-  [Pytorch-NCE](https://github.com/Stonesjtu/Pytorch-NCE): The Noise Contrastive Estimation for softmax output written in Pytorch
271.  1000-  [generative-models](https://github.com/shayneobrien/generative-models): Annotated, understandable, and visually interpretable PyTorch implementations of: VAE, BIRVAE, NSGAN, MMGAN, WGAN, WGANGP, LSGAN, DRAGAN, BEGAN, RaGAN, InfoGAN, fGAN, FisherGAN. 
272.  1000-  [convnet-aig](https://github.com/andreasveit/convnet-aig): PyTorch implementation for Convolutional Networks with Adaptive Inference Graphs.
273.  1000-  [integrated-gradient-pytorch](https://github.com/TianhongDai/integrated-gradient-pytorch): This is the pytorch implementation of the paper - Axiomatic Attribution for Deep Networks.
274.  1000-  [MalConv-Pytorch](https://github.com/Alexander-H-Liu/MalConv-Pytorch): Pytorch implementation of MalConv. 
275.  1000-  [trellisnet](https://github.com/locuslab/trellisnet): Trellis Networks for Sequence Modeling
276.  1000-  [Learning to Communicate with Deep Multi-Agent Reinforcement Learning](https://github.com/minqi/learning-to-communicate-pytorch): pytorch implementation of  Learning to Communicate with Deep Multi-Agent Reinforcement Learning paper.
277.  1000-  [pnn.pytorch](https://github.com/michaelklachko/pnn.pytorch): PyTorch implementation of CVPR'18 - Perturbative Neural Networks http://xujuefei.com/pnn.html.
278.  1000-  [Face_Attention_Network](https://github.com/rainofmine/Face_Attention_Network): Pytorch implementation of face attention network as described in Face Attention Network: An Effective Face Detector for the Occluded Faces.
279.  1300+  [waveglow](https://github.com/NVIDIA/waveglow): 基于流的语音合成生成网络。
280.  1000-  [deepfloat](https://github.com/facebookresearch/deepfloat): This repository contains the SystemVerilog RTL, C++, HLS (Intel FPGA OpenCL to wrap RTL code) and Python needed to reproduce the numerical results in "Rethinking floating point for deep learning" 
281.  1000-  [EPSR](https://github.com/subeeshvasu/2018_subeesh_epsr_eccvw): Pytorch implementation of [Analyzing Perception-Distortion Tradeoff using Enhanced Perceptual Super-resolution Network](https://arxiv.org/pdf/1811.00344.pdf). This work has won the first place in PIRM2018-SR competition (region 1) held as part of the ECCV 2018.
282.  1000-  [ClariNet](https://github.com/ksw0306/ClariNet): Pytorch实现[ClariNet](https://arxiv.org/abs/1807.07281)。
283.  22500+  [pytorch-pretrained-BERT](https://github.com/huggingface/pytorch-pretrained-BERT): PyTorch version of Google AI's BERT model with script to load Google's pre-trained models
284.  1000-  [torch_waveglow](https://github.com/npuichigo/waveglow): PyTorch实现WaveGlow: 基于流的语音合成生成网络。
285.  2300+  [3DDFA](https://github.com/cleardusk/3DDFA): The pytorch improved re-implementation of TPAMI 2017 paper: Face Alignment in Full Pose Range: A 3D Total Solution.
286.  1100+  [loss-landscape](https://github.com/tomgoldstein/loss-landscape): loss-landscape Code for visualizing the loss landscape of neural nets.
287.  1000-  [famos](https://github.com/zalandoresearch/famos):（非）参数图像风格化马赛克的对抗性框架。论文：http://arxiv.org/abs/1811.09236 。
288.  1000-  [back2future.pytorch](https://github.com/anuragranj/back2future.pytorch): This is a Pytorch implementation of
Janai, J., Güney, F., Ranjan, A., Black, M. and Geiger, A., Unsupervised Learning of Multi-Frame Optical Flow with Occlusions. ECCV 2018.
289.  1000-  [FFTNet](https://github.com/mozilla/FFTNet): Unofficial Implementation of FFTNet vocode paper.
290.  1000-  [FaceBoxes.PyTorch](https://github.com/zisianw/FaceBoxes.PyTorch): PyTorch实现[FaceBoxes](https://arxiv.org/abs/1708.05234)。
291.  2300+  [Transformer-XL](https://github.com/kimiyoung/transformer-xl): Transformer-XL: Attentive Language Models Beyond a Fixed-Length Contexthttps://github.com/kimiyoung/transformer-xl
292.  1000-  [associative_compression_networks](https://github.com/jalexvig/associative_compression_networks): Associative Compression Networks for Representation Learning. 
293.  1000-  [fluidnet_cxx](https://github.com/jolibrain/fluidnet_cxx): FluidNet re-written with ATen tensor lib. 
294.  2100+  [Deep-Reinforcement-Learning-Algorithms-with-PyTorch](https://github.com/p-christ/Deep-Reinforcement-Learning-Algorithms-with-PyTorch): This repository contains PyTorch implementations of deep reinforcement learning algorithms.
295.  1000-  [Shufflenet-v2-Pytorch](https://github.com/ericsun99/Shufflenet-v2-Pytorch): This is a Pytorch implementation of faceplusplus's ShuffleNet-v2. 
296.  1000-  [GraphWaveletNeuralNetwork](https://github.com/benedekrozemberczki/GraphWaveletNeuralNetwork): This is a Pytorch implementation of Graph Wavelet Neural Network. ICLR 2019. 
297.  1000-  [AttentionWalk](https://github.com/benedekrozemberczki/AttentionWalk): This is a Pytorch implementation of Watch Your Step: Learning Node Embeddings via Graph Attention. NIPS 2018.
298.  1000-  [SGCN](https://github.com/benedekrozemberczki/SGCN): This is a Pytorch implementation of Signed Graph Convolutional Network. ICDM 2018.
299.  1000-  [SINE](https://github.com/benedekrozemberczki/SINE): This is a Pytorch implementation of SINE: Scalable Incomplete Network Embedding. ICDM 2018.
300.  1000-  [GAM](https://github.com/benedekrozemberczki/GAM): This is a Pytorch implementation of Graph Classification using Structural Attention. KDD 2018.
301.  1000-  [neural-style-pt](https://github.com/ProGamerGov/neural-style-pt): PyTorch 实现 Justin Johnson 的神经风格算法。论文：[A Neural Algorithm of Artistic Style](https://arxiv.org/abs/1508.06576)。
302.  1000-  [TuckER](https://github.com/ibalazevic/TuckER): TuckER: Tensor Factorization for Knowledge Graph Completion.
303.  1000-  [pytorch-prunes](https://github.com/BayesWatch/pytorch-prunes): Pruning neural networks: is it time to nip it in the bud?
304.  1000-  [SimGNN](https://github.com/benedekrozemberczki/SimGNN): SimGNN: 一个快速图形相似度计算的神经网络方法。论文：A Neural Network Approach to Fast Graph Similarity Computation.
305.  1000-  [Character CNN](https://github.com/ahmedbesbes/character-based-cnn): PyTorch implementation of the Character-level Convolutional Networks for Text Classification paper. 
306.  1900+  [XLM](https://github.com/facebookresearch/XLM): PyTorch original implementation of Cross-lingual Language Model Pretraining.
307.  1000-  [DiffAI](https://github.com/eth-sri/diffai): A provable defense against adversarial examples and library for building compatible PyTorch models.
308.  1000-  [APPNP](https://github.com/benedekrozemberczki/APPNP): Combining Neural Networks with Personalized PageRank for Classification on Graphs. ICLR 2019.
309.  1000-  [NGCN](https://github.com/benedekrozemberczki/MixHop-and-N-GCN): A Higher-Order Graph Convolutional Layer. NeurIPS 2018.
310.  1000-  [gpt-2-Pytorch](https://github.com/graykode/gpt-2-Pytorch): Simple Text-Generator with OpenAI gpt-2 Pytorch Implementation
311.  1000-  [Splitter](https://github.com/benedekrozemberczki/Splitter): Splitter: Learning Node Representations that Capture Multiple Social Contexts. (WWW 2019).
312.  1000-  [CapsGNN](https://github.com/benedekrozemberczki/CapsGNN): 胶囊图神经网络，[Capsule Graph Neural Network](https://openreview.net/forum?id=Byl8BnRcYm)。
313.  1700+  [BigGAN-PyTorch](https://github.com/ajbrock/BigGAN-PyTorch): PyTorch实现BigGAN（非官方）。
314.  1000-  [ppo_pytorch_cpp](https://github.com/mhubii/ppo_pytorch_cpp): 近端策略优化算法的C++ API。
315.  1000-  [RandWireNN](https://github.com/seungwonpark/RandWireNN): 基于随机连接神经网络性能的图像识别。
316.  1000-  [Zero-shot Intent CapsNet](https://github.com/joel-huang/zeroshot-capsnet-pytorch): GPU-accelerated PyTorch implementation of "Zero-shot User Intent Detection via Capsule Neural Networks".
317.  1000-  [SEAL-CI](https://github.com/benedekrozemberczki/SEAL-CI) 半监督图分类：层次图视角，Semi-Supervised Graph Classification: A Hierarchical Graph Perspective. (WWW 2019)。
318.  1000-  [MixHop](https://github.com/benedekrozemberczki/MixHop-and-N-GCN): MixHop: Higher-Order Graph Convolutional Architectures via Sparsified Neighborhood Mixing. ICML 2019.
319.  1000-  [densebody_pytorch](https://github.com/Lotayou/densebody_pytorch): PyTorch implementation of CloudWalk's recent paper DenseBody.
320.  1000-  [voicefilter](https://github.com/mindslab-ai/voicefilter): Unofficial PyTorch implementation of Google AI's VoiceFilter system http://swpark.me/voicefilter. 
321.  1000-  [NVIDIA/semantic-segmentation](https://github.com/NVIDIA/semantic-segmentation): PyTorch实现“利用视频传播和标签松弛改进语义分割”。论文：[Improving Semantic Segmentation via Video Propagation and Label Relaxation](https://arxiv.org/abs/1812.01593), In CVPR2019.
322.  1000-  [ClusterGCN](https://github.com/benedekrozemberczki/ClusterGCN): A PyTorch implementation of "Cluster-GCN: An Efficient Algorithm for Training Deep and Large Graph Convolutional Networks" (KDD 2019).
323.  1000-  [NVlabs/DG-Net](https://github.com/NVlabs/DG-Net): A PyTorch implementation of "Joint Discriminative and Generative Learning for Person Re-identification" (CVPR19 Oral). 
324.  1000-  [NCRF](https://github.com/baidu-research/NCRF): 基于神经网络条件随机场(NCRF)的肿瘤转移检测，相关论文：https://openreview.net/forum?id=S1aY66iiM。
325.  1000-  [pytorch-sift](https://github.com/ducha-aiki/pytorch-sift): PyTorch实现SIFT（尺度不变特征变换匹配算法，Scale Invariant Feature Transform）描述子。
326.  1000-  [brain-segmentation-pytorch](https://github.com/mateuszbuda/brain-segmentation-pytorch): 深度学习分割网络U-Net的PyTorch模型实现，用于脑核磁共振中FLAIR异常的分割。
327.  1000-  [glow-pytorch](https://github.com/rosinality/glow-pytorch): PyTorch 实现 "[Glow, Generative Flow with Invertible 1x1 Convolutions](https://arxiv.org/abs/1807.03039)"。
328.  1000-  [EfficientNets-PyTorch](https://github.com/zsef123/EfficientNets-PyTorch): PyTorch实现EfficientNet: 卷积神经网络模型尺度的再思考。
329.  1000-  [STEAL](https://github.com/nv-tlabs/STEAL): STEAL - 从噪声标注中学习语义边界，https://nv-tlabs.github.io/STEAL/ 。
330.  1000-  [EigenDamage-Pytorch](https://github.com/alecwangcq/EigenDamage-Pytorch): 官方实现 ICML'19 论文 "[特征损伤：克罗内克分解特征基中的结构剪枝](https://arxiv.org/abs/1905.05934)"。
331.  1000-  [Aspect-level-sentiment](https://github.com/ruidan/Aspect-level-sentiment): 论文代码和数据集，ACL2018论文："[利用文档知识进行体层情感分类](https://arxiv.org/abs/1806.04346)"。
332.  1000-  [breast_cancer_classifier](https://github.com/nyukat/breast_cancer_classifier): 深层神经网络提高放射科医生乳腺癌筛查的效果，https://arxiv.org/abs/1903.08297 。
333.  1000-  [DGC-Net](https://github.com/AaltoVision/DGC-Net): PyTorch实现"[DGC-Net: 密集几何对应网络](https://arxiv.org/abs/1810.08393)".
334.  1000-  [universal-triggers](https://github.com/Eric-Wallace/universal-triggers): Universal Adversarial Triggers for Attacking and Analyzing NLP (EMNLP 2019)
335.  2100+  [Deep-Reinforcement-Learning-Algorithms-with-PyTorch](https://github.com/p-christ/Deep-Reinforcement-Learning-Algorithms-with-PyTorch): PyTorch implementations of deep reinforcement learning algorithms and environments.
336.  1000-  [simple-effective-text-matching-pytorch](https://github.com/alibaba-edu/simple-effective-text-matching-pytorch): A pytorch implementation of the ACL2019 paper "Simple and Effective Text Matching with Richer Alignment Features".
337.  null  [Adaptive-segmentation-mask-attack (ASMA)](https://github.com/utkuozbulak/adaptive-segmentation-mask-attack): A pytorch implementation of the MICCAI2019 paper "Impact of Adversarial Examples on Deep Learning Models for Biomedical Image Segmentation".
338.  1000-  [NVIDIA/unsupervised-video-interpolation](https://github.com/NVIDIA/unsupervised-video-interpolation): A PyTorch Implementation of [Unsupervised Video Interpolation Using Cycle Consistency](https://arxiv.org/abs/1906.05928), In ICCV 2019.

## Talks & conferences｜报告 & 会议

1. [PyTorch Conference 2018](https://developers.facebook.com/videos/2018/pytorch-developer-conference/): 2018年首届PyTorch开发者大会。

## Pytorch elsewhere ｜ Pytorch相关

1.  4500+  [the-incredible-pytorch](https://github.com/ritchieng/the-incredible-pytorch)**: 不可思议的Pythorch：一份PyTorch相关的教程、论文、项目、社区等的清单。
2.  5800+  [generative models](https://github.com/wiseodd/generative-models): 各种生成模型，例如基于Pytorch和Tensorflow的GAN、VAE。 http://wiseodd.github.io  
3. [pytorch vs tensorflow](https://www.reddit.com/r/MachineLearning/comments/5w3q74/d_so_pytorch_vs_tensorflow_whats_the_verdict_on/): Reddit上的PyTorch和TensorFlow的比较文章。
4. [Pytorch discussion forum](https://discuss.pytorch.org/): PyTorch论坛。
5.  null  [pytorch notebook: docker-stack](https://hub.docker.com/r/escong/pytorch-notebook/): 类似于 [Jupyter Notebook Scientific Python Stack](https://github.com/jupyter/docker-stacks/tree/master/scipy-notebook)
6.  1000-  [drawlikebobross](https://github.com/kendricktan/drawlikebobross): 使用神经网络作画！
7.  1000-  [pytorch-tvmisc](https://github.com/t-vi/pytorch-tvmisc): 该仓库收集了作者用PyTorch实现的各种玩意儿。
8.  1000-  [pytorch-a3c-mujoco](https://github.com/andrewliao11/pytorch-a3c-mujoco): 该项目旨在解决Mujoco中的控制问题，高度基于pytorch-a3c。
9. [PyTorch in 5 Minutes](https://www.youtube.com/watch?v=nbJ-2G2GXL0&list=WL&index=9).
10.  1000-  [pytorch_chatbot](https://github.com/jinfagang/pytorch_chatbot): 用PyTorch实现的聊天机器人。
11.  1000-  [malmo-challenge](https://github.com/Kaixhin/malmo-challenge): Malmo协作人工智能挑战-Pig Catcher团队。
12.  1000-  [sketchnet](https://github.com/jtoy/sketchnet): 指导计算机作画。http://www.jtoy.net/projects/sketchnet/
13.  1200+  [Deep-Learning-Boot-Camp](https://github.com/QuantScientist/Deep-Learning-Boot-Camp): 非盈利社区运营的5天深度学习训练营。 http://deep-ml.com.
14.  1000-  [Amazon_Forest_Computer_Vision](https://github.com/mratsim/Amazon_Forest_Computer_Vision): 亚马逊森林计算机视觉：使用PyTorch标记卫星图像标记/Keras中的PyTorch技巧。
15.  1900+  [AlphaZero_Gomoku](https://github.com/junxiaosong/AlphaZero_Gomoku): 用AlphaZero算法玩五子棋。
16.  null  [pytorch-cv](https://github.com/youansheng/pytorch-cv): null.
17.  1900+  [deep-person-reid](https://github.com/KaiyangZhou/deep-person-reid): Pytorch实现深度学习行人重新识别方法。
18.  1500+  [pytorch-template](https://github.com/victoresque/pytorch-template): PyTorch深度学习模版。
19.  1000-  [Deep Learning With Pytorch](https://github.com/svishnu88/DLwithPyTorch): 随书代码《[Deep Learning With Pytorch TextBook](https://www.packtpub.com/big-data-and-business-intelligence/deep-learning-pytorch)》 PyTorch实用指南：使用PyTorch建立文本和视觉神经网络模型。[亚马逊中国电子版](https://www.amazon.cn/dp/B078THDX3J/ref=sr_1_1?__mk_zh_CN=亚马逊网站&keywords=Deep+Learning+with+PyTorch&qid=1568007543&s=gateway&sr=8-1)
20.  1000-  [compare-tensorflow-pytorch](https://github.com/jalola/compare-tensorflow-pytorch): 比较用Tensorflow编写的层和用Pytorch编写的层之间的输出。
21.  1000-  [hasktorch](https://github.com/hasktorch/hasktorch): Haskell中的张量与神经网络。
22. [Deep Learning With Pytorch](https://www.manning.com/books/deep-learning-with-pytorch) Deep Learning with PyTorch 教你如何用Python和PyTorch实现深度学习算法。
23.  1000-  [nimtorch](https://github.com/fragcolor-xyz/nimtorch): PyTorch - Python + Nim，PyTorch的Nim前端。
24.  1000-  [derplearning](https://github.com/John-Ellis/derplearning): 自动驾驶遥控车代码。
25.  1000-  [pytorch-saltnet](https://github.com/tugstugi/pytorch-saltnet): Kaggle | TGS Salt Identification Challenge 第9名解决方案。
26.  1000-  [pytorch-scripts](https://github.com/peterjc123/pytorch-scripts): 一些脚本，使在Windows上使用PyTorch更加容易。
27.  1000-  [pytorch_misc](https://github.com/ptrblck/pytorch_misc): 为PyTorch讨论板创建的代码片段。
28.  1000-  [awesome-pytorch-scholarship](https://github.com/arnas/awesome-pytorch-scholarship): 收集了一系列优秀的PyTorch学术文章、指南、博客、课程和其他资源。
29.  1000-  [MentisOculi](https://github.com/mmirman/MentisOculi): PyTorch版raytracer。(raynet?)
30.  2400+  [DoodleMaster](https://github.com/karanchahal/DoodleMaster): “画出UI！”("Don't code your UI, Draw it !")
31.  1000-  [ocaml-torch](https://github.com/LaurentMazare/ocaml-torch): ocaml-torch为PyTorch张量库提供一些ocaml绑定。
32.  1000-  [extension-script](https://github.com/pytorch/extension-script): TorchScript自定义C++/CUDA运算符的示例。
33.  1000-  [pytorch-inference](https://github.com/zccyman/pytorch-inference):  Windows10 平台上 Pytorch 1.0在 C++ 中的推断。
34.  1000-  [pytorch-cpp-inference](https://github.com/Wizaron/pytorch-cpp-inference): 包含使用PyTorch C++ API执行推断的各种示例。
35.  1000-  [tch-rs](https://github.com/LaurentMazare/tch-rs): PyTorch的Rust绑定。
36.  1000-  [TorchSharp](https://github.com/interesaaat/TorchSharp): Pytorch引擎的.NET绑定。
37.  1000-  [ML Workspace](https://github.com/ml-tooling/ml-workspace): 面向机器学习和数据科学的一体化Web IDE。包含Jupyter, VS Code, PyTorch 和许多其他工具或库，这些都集合在一个Docker映像中。
38.  1000-  [PyTorch Style Guide](https://github.com/IgorSusmelj/pytorch-styleguide) Style guide for PyTorch code. Consistent and good code style helps collaboration and prevents errors!

**Feedback: If you have any ideas or you want any other content to be added to this list, feel free to contribute.**


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)