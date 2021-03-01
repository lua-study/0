# Covid19-KG

#### 介绍
##### 项目目录
1. crawler 进行爬虫及数据的基本清洗
2. KGQA 部署以Apache Jena以及SPARQL为查询语言的问答系统
3. raw_data 经过清洗的一系列数据,包括RDF和JSON格式
4. static 一些静态的图片等相关文件
5. templates 基本的前端HTML页面
6. app.py 基本的flask框架部署
7. demo.mp4 一段录制的视频
8. utils.py 琐碎的综合功能

##### 运行方法
第一步首先需要部署服务器
![jena服务器](static/jena.png)

第二步讲raw_data中的数据上传到jena服务器
![save](static/save.png)

第三步
```python
python app.py
```


##### 实际效果详见demo

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)