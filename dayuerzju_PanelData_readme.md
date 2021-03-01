---
> ## 最新直播课程：  
---

&emsp;

## 《Stata直播丨直击面板数据模型》

- 在线观看链接：  
- 首次直播时间：2019.12.18，19:30-21:00 (已结束)
- 免费回放：点击  ，使用经管之家账号登陆后可以免费观看直播。

## 课程概览

面板数据模型简介，包括：固定效应模型 (FE)，随机效应模型 (RE)，二维固定效应模型 (Twoway FE)，聚类调整后的标准误，动态面板和面板门槛模型等。本课程是 [「2020寒假Stata现场班(1.8-17日，北京)」](http://www.peixun.net/view/1224.html) ， [「微信版-课程介绍」](https://mp.weixin.qq.com/s/-dFPrGQMhH3JzA4tEc35kQ) 的一个小节。以介绍模型设定思路为主，实操部分请下载 「**Lian_Panel.rar**」压缩包自行演练，我会在现场班做详细讲解。
  

> **获取课程电子包：** 

你可以点击主页右上方的【克隆/下载&rarr;下载zip】，以便下载本仓库的压缩包；也可以申请一个 [码云](https://gitee.com) 账号，然后点击本项目右上角的【Fork】按钮，这样就可以直接把这个仓库「叉」到你的账号下了，随后我这边更新后，你只需要同步一下就可以看到所有的文件了。


> **实操：Stata dofiles/Data/Papers:** 

下载地址：  (百度云盘，无解压码)。

> 文件清单如下：

```dos
D:\Lec\Lian_Panel
|
│  Lian_PanelData.do    // dofiles，附带本将所有实操命令
│  
├─Data
│      FE_BE_POLS.do
│      FE_mark.dta
│      FE_OLS_Negative.do
│      FE_OLS_Nodiff.do
│      FE_OLS_Positive.do
│      FE_OLS_Zero.do
│      FE_simudata.dta
│      FE_simudata_00.do
│      GTA_sample.dta
│      invest2.dta
│      nlswork.dta
│      xtcs.dta
│      xtlabor.dta
│      XT_FE_fig1.do
│      XT_FE_fig2.do
│      XT_FE_fig3.do
│      
├─Out
│      panel_Neg.png
│      panel_Nodiff.png
│      panel_Positive.png
│      panel_Pos_Scatter.png
│      panel_Zero.png
│      
└─refs
        Abadie_2017_adjust_SE.pdf
        Baltagi_2005.pdf
        Bruederl_Ludwig_FE_2015.pdf
        Cameron_2008_RES_bsClusterSE.pdf
        Cameron_2011_Clustered_se.pdf
        Cameron_2011_ClusterSE.pdf
        Cameron_2011_ClusterSE_PPT.pdf
        Cameron_2015_ClusterSE_JHR.pdf
        Flannery_2006.pdf
        Flannery_2006_FE.pdf
        Gormley_2014_RFS_FE.pdf
        Greene_2012.pdf
        Hisao_2003.pdf
        Horioka_2007_DPD.pdf
        Huang_2008_DPD.pdf
        Ibragimov_2010_clustse.pdf
        OLS_Partial_Corr.pdf
        panel_Neg.png
        Petersen-2009.pdf
        Rios_2015_SJ_15-3_FE.pdf
        SJ12-3-ReviewFE.pdf
        Sun_2004.pdf
        Thompson-2011.pdf
        Wooldridge_2010.pdf
        XT3_Hausman.pptx
        XT_FE_RE.pptx
        连玉君(2011)_Panel_Data.pdf
        连玉君_2012_消费文化.pdf
        连玉君_2014_Hausman检验.pdf
```

&emsp;


## 嘉宾简介

![连玉君](https://images.gitee.com/uploads/images/2019/0801/231203_00d532e3_1522177.jpeg)   

**[连玉君](http://lingnan.sysu.edu.cn/node/151)** ，经济学博士，副教授，博士生导师。2007年7月毕业于西安交通大学金禾经济研究中心，现任教于中山大学岭南学院金融系。主讲课程为“金融计量”、“实证金融”等。已在《China Economic Review》、《经济研究》、《管理世界》、《经济学(季刊)》、《金融研究》、《统计研究》等期刊发表论文 60 余篇；主持完成国家自然科学基金项目、教育部人文社科基金项目、广东自然科学基金项目等课题项目 10 余项。目前已完成 Panel VAR、Panel Threshold、Two-tier Stochastic Frontier 等计量模型的 Stata 实现程序，并编写过几十个小程序，如 `xtbalance`, `winsor2`, `bdiff`, `hausmanxt`, `ttable3`, `hhi5`, `ua`等。连玉君老师团队一直积极分享 Stata 应用经验，创办了公众号「Stata连享会 (StataChina)」，开设了 [[Stata连享会-简书]](https://www.jianshu.com/u/69a30474ef33)，[[Stata连享会-知乎]](https://www.zhihu.com/people/arlionn) 两个专栏，累计阅读量超过 200 万人次。


## 课程介绍

### 主题：直击面板数据模型

目前的实证分析中，基本上都是以「面板数据」为分析对象。好处很明显，一方面，随着样本量的增加，我们的统计推断会更加稳健；另一方面，面板数据同时提供了时序和截面的信息，使得我们既可以分析个体之间的截面差异，也可以分析他们时序动态变化。最为重要的是，使用面板数据还是缓解内生性问题的一个主要方法——我们可以控制那些不可观测的固定效应的影响。

本次直播主要包括如下几个主题：

- 简介：面板数据结构、优势和挑战
- 什么是「固定效应」？辛普森悖论
- 一维和二维固定效应模型
- 估计方法对比分析：POLS，DVLS，Within-FE
- 聚类标准误：一维聚类和多维聚类
- 实证分析中的主要陷阱
- 动态面板和面板门限模型简介

#### 课程特色
- 深入浅出：掌握最主流的面板数据分析方法
- 电子板书：全程电子板书演示，课后分享
- 电子讲义：分享全套 Stata 课件 (数据、程序和 dofiles)


&emsp;

----


&emsp;
 
> Stata 连享会： [知乎](https://zhuanlan.zhihu.com/arlion) | [简书](http://www.jianshu.com/u/69a30474ef33) | [码云](https://gitee.com/arlionn) | [CSDN](https://blog.csdn.net/arlionn)



---
> ### 连享会 现场班-精品课程
  
> #### A. [2020寒假Stata现场班](https://gitee.com/arlionn/Course/blob/master/StataFull.md) 
> **时间地点：** 2020年1月8-17日，北京         
> **主讲嘉宾：** 连玉君 (中山大学)；江艇 (中国人民大学)                   
> &emsp; 完整的知识架构是你长期成长的动力源泉……



> #### B. [连享会-文本分析与爬虫专题班](https://gitee.com/arlionn/Course/blob/master/Done/2020Text.md)   
> **时间地点：** 2020年3月26-29日，西安-西北工业大学     
> **主讲嘉宾：** 司继春(上海对外经贸大学)；游万海(福州大学)


&emsp;




---
### A. [2020寒假Stata现场班](https://mp.weixin.qq.com/s/-dFPrGQMhH3JzA4tEc35kQ)  
- **时间地点：** 2020年1月8-17日；北京-海淀区
- **主讲嘉宾**：连玉君 (中山大学，初级+高级)；江艇 (中国人民大学，论文班)
- **授课内容：** 全面介绍 Stata 数据处理、编程、主流计量方法，通过剖析经典论文掌握论文写作方法。主要涵盖如下方法和模型：模型设定、交乘项、静态和动态面板数据模型、面板门槛模型、内生性专题 (DID, PSM, RDD)，合成控制法，Probit模型等。
- **课程主页：** [2020寒假Stata现场班](http://www.peixun.net/view/1224.html) ， [「微信版-课程介绍」](https://mp.weixin.qq.com/s/-dFPrGQMhH3JzA4tEc35kQ)
&emsp;

[![2020寒假Stata现场班](https://images.gitee.com/uploads/images/2019/1114/084141_b50efd9f_1522177.jpeg "2020寒假Stata现场班-扫码了解详情")](https://mp.weixin.qq.com/s/-dFPrGQMhH3JzA4tEc35kQ)


&emsp;

---
### B. [连享会-文本分析与爬虫专题班](https://gitee.com/arlionn/Course/blob/master/Done/2020Text.md)   
- **时间：** 2020 年 3 月 26-29 日 (周四-周日)
- **时段：** 上午 9:00-12:00；下午 14:00-17:00，答疑：17:00-17:30
- **地点：** 西安，西北工业大学国际会议中心  ([百度地图](https://j.map.baidu.com/yXIiP) | [搜狗地图](http://map.sogou.com/u/MvmiOn))
- **主讲嘉宾：** 游万海 (第 1-4 讲)；司继春 (第 5-8 讲)
- **授课内容：** 文本分析与爬虫
  - **课程要点：** 本课程主要介绍正则表达式相关语法规则及非结构化数据处理；讲解 Python 的基础知识，并使用 Python 进行数据处理、数值计算、网络爬虫、文本分析等不同任务的处理；介绍机器学习常用算法，如决策树、随机森林、支持向量机以及神经网络等的基本原理，并使用 Python 实现各类算法。
  - **主要方法：** Python, Scipy, Numpy, Pandas, Matplotlib, Plotly, BeautifulSoup, Request, Selenium, Scikit-learn, TensorFlow, Jieba, NLTK, gensim等。
- **主要软件\语言：** Stata, Python
- **课程主页(含助教招聘)：** [连享会-文本分析与爬虫专题班](https://gitee.com/arlionn/Course/blob/master/Done/2020Text.md) || 「[微信版大纲](http://mp.weixin.qq.com/s?__biz=MzAwMzk4ODUzOQ==&mid=2247486963&idx=1&sn=ed6e2b77be6977bcb723f12bebaa3e26&chksm=9b3380a7ac4409b186fa06a2133d3799e8697893caef53fc0f07c204b2f0d850d671d340d9a5&scene=21#wechat_redirect)」

![连享会-文本分析与爬虫专题班，西北工业大学，2020.3.26-29](https://fig-lianxh.oss-cn-shenzhen.aliyuncs.com/连享会2020.3文本分析海报.png "连享会-文本分析现场班，西北工业大学，2020.3.26-29")



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)