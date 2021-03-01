# E-echarts  {#top}
>易语言模块（开源）
***
## 目录
* [特别说明](#shuoming)
* [模块简介](#jianjie)
* [更新日志](https://coding.net/u/lsy9202/p/E-echarts/git/blob/master/doc/manual3.md)
* [运行效果](#demo)
* [模块特点](#tedian)
* [最新版功能（v1.6）](#zuixin)
* [运行环境](#huanjing)
* [文件列表](#wenjian)
* [讨论群](#qun)

***
### 特别说明{#shuoming}

由于示例更新频繁并且示例的基础文件包稍大，所以不再上传源码，示例大全源码及基础文件包将保存在群文件中，需要的可以加群下载（群号：93902676），有问题也欢迎及时群内留言反馈。

​	![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/1_6_9.png)

​	![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/1_6_10.png)

### 模块简介: {#jianjie}

本模块封装百度echarts.js（开源），相对于chart.js好处具有更全面api文档支持，更多的图形样式及配置支持，例如：散点图、折线图、柱状图、饼图、地图、雷达图、K线图、箱线图、热力图、关系图、矩形树图、平行坐标、桑基图、漏斗图、仪表盘等等。  

官方图形样例展示：http://echarts.baidu.com/examples.html  
官方API文档：http://echarts.baidu.com/option.html  

官方示例
![官方示例](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/demo1.png)

网友示例
![网友示例](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/demo2.png)
#####[回到顶部](#top)
***
### 模块运行效果： {#demo}

![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/zhexianhesandiantu-tu.png)
![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/zhutu-tu.png)
![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/bingtu-tu1.png)
![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/bingtu-tu2.png)
![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/leidatu-tu.png)

![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/demo3.png)
![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/candlestick.png)

动态效果展示（gif动图稍慢）
动态数据图形
![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/demo5.gif)
K线图
![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/demo4.gif)

#####[回到顶部](#top)
***
### 模块特点：  {#tedian}

>下边除了第一行，后边的都是echarts.js的特点，本模块仅是最大限度还原保留了它的特点。

* 使用本模块前请花3分钟学习一下json文件格式基础
* 简单三行代码即可快速生成图表
* echarts.js源码已更新至最新版，且内置到模块中，所以支持离线使用
* 支持WKE浏览框控件或超文本浏览框控件（建议使用wke，可使用更好的性能和兼容性，并支持运行js代码）
* 支持使用js动态加载数据（实时动态加载显示，无需刷新整个页面，比如CPU使用率曲线功能）
* 支持单页面显示多个图表互不干扰，分别js动态加载数据
* 模块支持引入外部js或者css文件
* 模块已封装了大量常用图形和各个图形组件，无需了解官方json结构即可快速生成图形
* 本模块内部封装了一个简单好用的json操作类，但不强制使用，使用者可以使用任意自己熟悉的方式来生成或操作配置json

#####[回到顶部](#top)

***
### 1.6版最新功能：{#zuixin}

* 使用echarts类的形式重写模块架构，并将echarts图形分为框架类和图形类，以便分别控制。

* 新架构最大限度保留了旧版本模块的支持一框多图、多框多图、json参数自定、组件化控制图形等优点。

* 新架构最大限度的将图形配置json保留在echarts类之内，不熟悉json的新手从图形创建到图形绘制全程无需关心json内容（当然依旧保留了json可自定修改、可导出、可导入等等特点）

* 统一调整了命令名称和部分参数位置，以便使用更简便。

* 新架构封装了大量常用js命令，例如操作运行图形、异步刷新图形等等操作无需再自行手写js代码了。

* 折线、柱图、散点图、K线图封装了数据异步调用的方法（原理：数据写入js引擎，使用js变量名调用数据），大数据时可以大幅度减少json生成和图形绘制时间。

* 所有命令添加了英文名词注释，可以用来快速对照官方api文档。


####  新特性展示

1.图形对象类和框架类分离控制

* 页面框架生成html页面时会自动调用图形对象代码
  ​	![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/1_6_1.png)

* 一屏多图时创建多个图形主体即可，生成html页面时会自动调用

  ![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/1_6_2.png)

2.从图形创建到图形绘制无需担心json的内容

​	![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/1_6_3.png)

3.封装了数据异步调用的方法

	> 下图中K线的数据量比较大（250KB左右，一共18年4110条数据）
	> 如果这么大量的数据直接写入json中，会造成json读写非常缓慢，浪费大量时间
	> 1.6版模块允许将数据写入js引擎，然后使用js变量名调用数据，同时不影响json内容编辑
	> （普通的json类不允许使用js变量名或js代码，如果有嵌入js内容之后是无法再使用命令修改json内容，本模块突破了此壁障）
	> json中使用过js变量名或者嵌入过js代码后，最后运行图形配置需要使用“运行图形配置_带JS变量()”命令

![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/1_6_4.png)

4.新版1.6模块简化了异步更新图形数据的方法

> 旧版本模块刷新图形数据时需要修改json内容，json内容比较多并且对官网json数据结构不了解的朋友可能无从下手。
>
> 新版本封装了"取图形数据()"和"JS操作_更新图形数据 ()"命令，大幅度简化数据修改和更新到图形的过程。

 * 取图形数据（）

   > 本命令将取出当前图形对象中的所有图形数据（仅仅是图形数据，其他将忽略）

   ![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/1_6_5.png)

* 取到的数据：

  ![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/1_6_6.png)

* 修改数据

  取到的数据都是标准json格式，直接使用内置json类修改即可

  下图是删除数组中开头的第一个成员，然后在末尾添加一个新数据成员，最后修改后重新存到变量

  这样可以得到图形从右往左移动的效果（最右边是新数据）

  ![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/1_6_7.png)

* 写入数据更新到图形

  ![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/1_6_8.png)

5.新版模块所有命令都添加了英文名词注释，以便对照查阅官网api文档

官网api文档地址：http://echarts.baidu.com/option.html

![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/1_6_11.png)

![](https://coding.net/u/lsy9202/p/E-echarts/git/raw/master/doc/img/1_6_12.png)

#####[回到顶部](#top)

***
### 运行环境说明： {#huanjing}
Echarts是js图形库，运行需要浏览框支持，可使用易语言内置超文本浏览框（ie内核），也可使用wke模块（精简chrome浏览器内核），也可以使用更强大一些的CEF3（精易黑猫封装的完整Chromium内核浏览框模块或支持库）

性能比较：**超文本浏览框**       .版本 2
>     wke.绑定 (_启动窗口.取窗口句柄 ()) ' 这里默认使用整个窗口做图形显示
>     json.解析 (标准配置_折线图 (“折线图主标题”, “折线图副标题”, X轴内容组, Y轴内容组))
>     wke.载入(页面代码_生成 (#CSS_隐藏滚动条, 创建图形 (“640px”, “480px”, , “myChart”, json.取代码 ())))  

2.wke浏览框使用运行js命令关闭loading动画并载入数据
>     .版本 2
>     wke.运行js("myChart.hideLoading();")
>     wke.运行js("myChart.setOption(" ＋ json.取代码() ＋ ")")

#####[回到顶部](#top)
***
### 文件列表： {#wenjian}
> 演示文件中因为需要演示js异步加载功能，所以使用了exui的wke浏览框控件，实际使用如果不需要js也可以使用易语言内置的超文本浏览框。

- **目录code** ----   为模块文本源码（方便在线查看）  
- **目录js**  ----  为引用的echart.js文件（只为展示，使用时不需要，js文件已内置到模块中）  
- **Echart_DEMO.e**  ----  为演示程序（演示程序使用了EXUI支持库的wke浏览框控件，需要单独下载）  
- **Echarts模块v---.ec**  ----  为已编译的成品模块文件  
- **READMO.md**  ----  说明文件
- **LICENSE**  ----  开源协议
- **echart.e**  ----  模块易语言源码文件
- **wke.dll**  ----  demo演示文件使用了EXUI支持库的wke浏览框控件
- **ex_ui2016.9.15.zip**  ----  EXUI支持库（demo演示文件中使用）

#####[回到顶部](#top)
***
### 讨论群： {#qun}
Echarts讨论群：**93902676**（本模块最新版及所有演示文件都在群文件中）
WKE等webui讨论群：**124479181**

#####[回到顶部](#top)

***

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)