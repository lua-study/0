# python_etc

some topic about python

## 方法论

### 思路总结

之前发现很多工程写的特别混乱，现在开始进行整理，思路如下：

我们遇到的困难都是可以分而治之的，假设我们划分两个集合，一个规范集，一个非规范集，两个集合的并集就是全集（问题集），规范集和非规范集互斥且相互独立；规范集描述的是已经规范的知识，用自己的语法描述并加以整理的知识，形成自己的“解决套路”，例如，学习爬虫的写法，我们不知道如何去请求js异步加载，那么我们就可以列举问题形成清单，只谈当前有必要解决和适当扩展的（而非像以前一样，贪图广，分散精力，注意力也被发散），什么叫异步加载？如何用python实现？规范的流程有哪些？然后依次解决，高频问题就划分到我的常用demo库里，以备后用，而非规范集就是描述这些未解决的问题，把所有问题总结成一个清单，包含未解决，或是不重要的，如果不重要，就放在项目中即可。

简单来讲，规范集有点类似活字印刷术里的印刷字，每一个都可以当做标准的或者高频demo来使用，而非规范集就可以依附于工程存放，偶尔review即可，这样就避免了很多高频的用法反复耗费精力去使用。


### 使用方法

#### 列举所有遇到的问题

列举问题形成清单，只谈当前有必要解决和适当扩展的（而非像以前一样，贪图广，分散精力，注意力也被发散）


#### 根据问题清理梳理规范集

尝试解决问题中的高频需求，再将其规范入规范集中，初始规范集为空

#### 根据问题梳理非规范集

尝试解决问题中的低频需求，将其规范入非规范集中，初始非规范集为空

#### 伪需求集

原则上规范集和非规范集是相互独立，互斥，完全穷尽，但可以出现异常集，即伪需求集，这时可以尝试伪需求集


## 仓库结构划分
如果粗略按照基本、进阶、高级主题这样进行结构划分，问题很大。
所以我采取先按主题领域分解，最后再进行进阶主题的分解。
> 参考python核心编程，python科学手册，利用python进行数据分析，廖雪峰
>
> 传智播客

## 生成方法

先使用jupyter撰写文档，然后生成同名markdown

## 工程

### base

Python的基本应用

### data_structure

数据结构相关内容，包括Python和c

### dataAna

数据分析相关内容，包括基本数据分析，数据挖掘，机器学习，深度学习等

### devops

运维和基本配置相关内容


### leetcode

leetcode刷题记录


## 参考
python核心编程
python学习手册
利用python进行数据分析
python官方文档

阅读计划

## 官方文档



### scrapy官方文档



https://doc.scrapy.org/en/latest/
https://legacy.gitbook.com/book/stevenzhao/scrapy-chinese/details
### django官方文档



https://docs.djangoproject.com/en/2.0/
https://docs.djangoproject.com/zh-hans/2.0/
http://www.runoob.com/django/django-tutorial.html
### python标准库



https://docs.python.org/3/library/
https://pymotw.com/3/index.html
https://docs.python.org/3.5/howto/index.html

### git官方文档



https://git-scm.com/book/en/v2

### bs4官方文档



http://beautifulsoup.readthedocs.io/zh_CN/v4.4.0/
### lxml文档



http://lxml.de/

### requests



http://docs.python-requests.org/zh_CN/latest/

http://cn.python-requests.org/zh_CN/latest/
### selenium



http://selenium-python-docs-zh.readthedocs.io/zh_CN/latest/

http://selenium-python-zh.readthedocs.io/en/latest/index.html

https://seleniumhq.github.io/selenium/docs/api/py/api.html

### python3官方文档



https://docs.python.org/3/

### tornado官方文档



http://www.tornadoweb.org/en/stable/
http://tornado-zh-cn.readthedocs.io/zh_CN/latest/
### mysql官方文档



https://dev.mysql.com/doc/refman/5.7/en/

https://dev.mysql.com/doc/

### nginx
http://nginx.org/en/docs/
http://www.nginx.cn/doc/

### flask

http://docs.jinkan.org/docs/flask/
http://flask.pocoo.org/docs/1.0/
http://www.pythondoc.com/flask/index.html



http://www.pythontip.com/

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)