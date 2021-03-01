# DouBanSpider

#### 项目介绍
使用 scrapy 编写的豆瓣图书爬虫，可以爬取豆瓣全站的图书信息然后保存到 MongoDB 数据库中。

#### 软件架构
爬虫：scrapy 框架
数据存储：MongoDB 数据库


#### 安装教程

1. 安装 scrapy 模块 https://scrapy.org
2. 安装 MongoDB 数据库 https://www.mongodb.com

#### 使用说明

1. 下载项目

git clone https://gitee.com/cix/DouBanSpider

2. 项目配置

   在 settings.py 文件下设置豆瓣的用户名和密码

    ![输入图片说明](https://images.gitee.com/uploads/images/2018/0915/085626_fea98a7b_1577043.png "Snip20180915_47.png")

   在 MongoDB 数据库中创建对应的库

     ![输入图片说明](https://images.gitee.com/uploads/images/2018/0915/085921_6ca1fe63_1577043.png "Snip20180915_49.png")

3. 进入项目文件夹

cd DouBanSpider/

4. 执行项目

scrapy crawl douban

5. 验证码  

模拟登陆次数增多后便需要输入验证码，在项目的根目录下有个名为 captcha_image.jpg 的图片文件

![输入图片说明](https://images.gitee.com/uploads/images/2018/0915/090711_851b5597_1577043.png "Snip20180915_51.png")

6. 最终效果


![输入图片说明](https://images.gitee.com/uploads/images/2018/0915/090033_c75d6934_1577043.png "Snip20180915_44.png")
 



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)