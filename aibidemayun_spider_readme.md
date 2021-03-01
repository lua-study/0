### 在家出不去开始写博客了，复习一下python爬虫
目标网址：[美女图](https://www.mzitu.com/xinggan/page/1/)

环境：win10 + python3.7 + pycharm

用到的包 ：requests ,BeautifulSoup (如果包没有，就使用命令 pip install [包名])

开始打开[网址](https://www.mzitu.com/xinggan/page/1/)
#### 一 分析网址
	一般分析网址使用Chrome浏览器比较方便，没有也可以使用Firefox，功能基本相同。一下默认使用Chrome
	
鼠标右键点击图片，选择检查（Firefox时审查元素？），弹出控制台。
![在这里插入图片描述](https://images.gitee.com/uploads/images/2020/0305/001355_b042d708_2274535.png)
我们可以看到图片的URL和名称，就是我们需要，再往上看，我们现在要找到所有的图片在那个div里（这里需要一点HTML知识，没有也无妨，div就相当于箱子，装一堆图片用）。
![在这里插入图片描述](https://images.gitee.com/uploads/images/2020/0305/001355_256970b3_2274535.png)
可以看到a标签在li下，li又在ul下ul在div下，终于目标div找到了，再看一些整个div里有几个li就有几个图片，但是图片里有几个是动态图，点击发现是广告，再用右键点击发现这些广告的 li 与其他的广告不同，需要在代码里处理一下。那么开始敲代码了。

---
#### 二，检查是否有反爬虫，并解决
我们先试一下网站有没有反爬虫

```python
url = 'https://www.mzitu.com/xinggan/page/1/'
html = requests.get(url)
print(html)
```
    这个代码就是最简单的爬虫了，如果网站没有任何反爬虫措施就可以看到网页的状态码了

```python
 
```
很遗憾这个网站有反爬虫，这得需要我们回到浏览器在分析一下，看看我们需要如何伪装请求头。

现在需要换一下控制台的模式，在右上角点击Network，就可以看到Chrome的抓包工具了，这里可能需要刷新一下才能看到。
![在这里插入图片描述](https://images.gitee.com/uploads/images/2020/0305/001355_37761762_2274535.jpeg)
然后再下边出现的图片缩略图里点击一个不是广告的查看它的请求头。

![在这里插入图片描述](https://images.gitee.com/uploads/images/2020/0305/001355_af313dc7_2274535.png)

如上图，第一个箭头就是请求头，一一分析并没有发现特别重要的信息，我们先添加一下User-Agent看一下，就是箭头2所自己的一行。

```python
url = 'https://www.mzitu.com/xinggan/page/1/'
headers={
        'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3770.142 Safari/537.36'
    }
html = requests.get(url,headers=headers)
print(html)

```
请求头是一个集合，User-Agent 添加进去，然后再改一下requests的get（）请求，把headers添加进去。运行看一下。

```python
 
```
这次状态码是200，说明访问成功，绕过了反爬虫，到这里已经成功了一般。

---
#### 三 获取图片连接
刚刚一直在使用requests包，终于到BeautifulSoup包了。

 1. 第一步先把div找到
 

```python
soup = BS(html.text, "html.parser")
list=soup.find(class_="postlist")
print(list)
```
soup是经过BeautifulSoup处理过的结果，然后使用BeautifulSoup的find函数找到div。
![在这里插入图片描述](https://images.gitee.com/uploads/images/2020/0305/001355_c3c726b6_2274535.png)
这个就是此段代码得到的结果，有URL和图片标题（URL应为怕被和谐就打码了），里面还有一下其他的东西，进一步清洗。

只需要更改下面一行就可以了

```python
list=soup.find(class_="postlist").findAll("li")
```
然后再分析一下现在拿到的数据，比如有多少个，发现用上面的代码得到了24个数据，一看刚好是除去广告之后每一页的的图片数量，到此基本拿到了图片的URL，再稍微处理一下就可以了。

```python
for i in list:
    # 连接
    print(i.a.img["data-original"])
    # 名
    print(i.span.a.text)
```
这就分析出了图片的URL和名字，每个 i 就是一个图片的 li 标签 i.a.img就是图片的标签，这里很好理解，只要有一点HTML基础。
![在这里插入图片描述](https://images.gitee.com/uploads/images/2020/0305/001355_9c78ca48_2274535.png)
以上就拿到了URL和名字。接下来就是下载了，没有下载的爬虫是没有灵魂的。

---
#### 图片保存到本地
既然已经拿到了URL，保存到本地还是比较容易的。

```python
        try:
            comn = requests.get(url=i.a.img["data-original"],headers=headerssss).content
        except:
            continue
        with open(i.span.a.text+ ".jpg", "wb") as f:
            f.write(comn)
            print("写入成功")
```

下载保存其实就是在请求一下，然后写入到文件就可以了
![在这里插入图片描述](https://images.gitee.com/uploads/images/2020/0305/001355_65e4b199_2274535.png)
以上就是此段代码的成果。
 **想要下载多页只需要在最外面套一个循环就可以了。**
 
---

这次爬虫效率比较底，没有开多线程，也没有把图片成套的下载，下次再写吧。

源码放在码云：[下载源码](https://gitee.com/aibidemayun/spider.git)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)