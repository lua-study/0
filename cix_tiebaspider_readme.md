### 项目简介
这是一个爬取百度贴吧整吧图片的爬虫，运行项目后输入贴吧名即可启动爬虫，而后会在根目录下自动生成一个 Image 文件夹来存储图片


### 前期准备
1. 安装 scrapy 框架    

- Windows 安装方式
    - Python 2
    - 升级pip版本：pip install --upgrade pip
    - 通过pip 安装 Scrapy 框架pip install Scrapy

- Ubuntu 需要9.10或以上版本安装方式
    - Python 2
    - 安装非Python的依赖 sudo apt-get install python-dev python-pip libxml2-dev libxslt1-dev zlib1g-dev libffi-dev libssl-dev
    - 通过pip 安装 Scrapy 框架 sudo pip install scrapy

- 安装后，只要在命令终端输入 scrapy，提示类似以下结果，代表已经安装成功
![输入图片说明](https://gitee.com/uploads/images/2018/0215/161648_81674a17_1577043.png "7.1.png")


### 运行项目
1. 下载项目
   
git clone https://gitee.com/cix/tiebaspider.git

2. 进入项目文件夹

cd tiebaspider/

3. 执行项目

scrapy crawl tb

4. 输入贴吧名

![输入图片说明](https://gitee.com/uploads/images/2018/0217/194333_8f712a2e_1577043.png "Snip20180217_1.png")

### 运行结果
- Image 文件夹下保存的图片

![输入图片说明](https://gitee.com/uploads/images/2018/0217/194635_9ff6a829_1577043.png "Snip20180217_3.png")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)