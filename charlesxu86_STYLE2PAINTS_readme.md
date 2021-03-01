# Lastest News

**Our new UI is under construction now. You can try it directly!**

PaintsTransfer: [http://paintstransfer.com/](http://paintstransfer.com/)

![new_preview](https://raw.githubusercontent.com/lllyasviel/style2paints/master/new_preview/0.png)

![new_preview](https://raw.githubusercontent.com/lllyasviel/style2paints/master/new_preview/1.png)

![new_preview](https://raw.githubusercontent.com/lllyasviel/style2paints/master/new_preview/2.png)

![new_preview](https://raw.githubusercontent.com/lllyasviel/style2paints/master/new_preview/3.png)

# You have just found STYLE2PAINTS

:pushpin:[GithubPage](https://lllyasviel.github.io/) :pushpin:[GithubPageChinese](https://lllyasviel.github.io/chinese) :pushpin:[StyleTransfer](https://github.com/lllyasviel/style2paints/blob/master/AnimeStyleTransfer.md)

*The previous version is now at 52.80.94.56:8000*

The AI can paint on a sketch according to a given specific color style.

The AI can transfer illustrations' style.

![web_preview](https://raw.githubusercontent.com/lllyasviel/style2paints/master/page/screen_shot.png)

![web_preview2](https://raw.githubusercontent.com/lllyasviel/style2paints/master/page/screen_shot2.png)

![web_preview3](https://raw.githubusercontent.com/lllyasviel/style2paints/master/page/screen_shot3.png)

![web_preview4](https://raw.githubusercontent.com/lllyasviel/style2paints/master/page/screen_shot4.png)

# Tuitions

[tuition 001](https://www.bilibili.com/video/av15014229/)

# Example 1 (Google Search results test)

![google](https://raw.githubusercontent.com/lllyasviel/style2paints/master/page/google.png)

A content sketch (**the first google image search result of key word 'anime sketch'**) and some style images:

.
 
.
 
.

Results:

.
 
.
 
.
 
.

.
 
.
 
.
 
.

.
 
.
 
.
 
.

# Example 2 (western sketch)

A western content sketch and 2 style images:

.
 
.
 
.
 
.

 

 

# Example 3 (messy sketch)

A messy content sketch and 2 style images:

.
 
.
 
.
 
.

.
 
.
 
.

# Example 4 (detailed sketch)

A detailed content sketch and 2 style images:

.
 
.
 
.
 
.

.
 
.
 
.

# Example 5 (simple sketch)

A simple content sketch **without shadow rendering** and 2 style images:

.
 
.
 
.
 
.

.
 
.
 
.

# CPU Server for Beginner

*you need a python 3 environment.*

    pip install tensorflow
    pip install keras
    pip install chainer
    pip install bottle
    pip install gevent
    pip install h5py
    pip install opencv-python
    git clone https://github.com/lllyasviel/style2paints.git
    (then download all pretrained models from 'release' page and then put them in 'style2paints/server')
    cd style2paints/server
    python server.py cpu

# GPU Server for Reseachers

*you need a CUDA python 3.6 environment.*

    pip install tensorflow_gpu
    pip install keras
    pip install chainer
    pip install cupy
    pip install bottle
    pip install gevent
    pip install h5py
    pip install opencv-python
    git clone https://github.com/lllyasviel/style2paints.git
    (then download all pretrained models from 'release' page and then put them in 'style2paints/server')
    cd style2paints/server
    python server.py

# Model

Models are available in 'release' page.

1. base_generator.net -> all rights reserved 2017 style2paints
2. style2paints.net -> all rights reserved 2017 style2paints
3. google_net.net -> from [nico-opendata](https://nico-opendata.jp/en/demo/tag/index.html)

# Training Datasets

1. The recommended training dataset of illustrations is the 400k images from [nico-opendata](https://nico-opendata.jp/en/seigadata/index.html)

2. The recommended training sketches is from [sketchKeras](https://github.com/lllyasviel/sketchKeras)

# Community

QQ Group ID: 184467946

## Acknowledgements

Thanks a lot to TaiZan. This project could not be achieved without his great help.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)