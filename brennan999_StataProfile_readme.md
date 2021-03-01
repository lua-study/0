>> Profile.do 下载方法： [[左键点我]](https://www.jianguoyun.com/p/DZAaPSwQtKiFCBiIndsC)，在弹出页面下载即可。

---
> &#x1F34E; **最新专题：**  
---




### 项目介绍：连玉君的 **profile.do** 文件

#### 使用方法
- 下载 **profile.do** 文件： [[左键点我]](https://www.jianguoyun.com/p/DZAaPSwQtKiFCBiIndsC)，在弹出页面下载即可。
- 如果在你的 Stata 安装目录下没有 **profile.do** 文档，可以直接将我的 **profile.do** 文件放到你的 Stata 安装目录下 (我的 Stata 安装目录是：**D:\stata15**)，但需要酌情修改你里面的内容，尤其是有关文件路径方面的设定。
- 如果在你的 Stata 安装目录下已经建立了 **profile.do** 文档，但需要更新一些设定，可以打开我的 **profile.do** 文档，截取所需放入你自己的 **profile.do** 文档中。Note: 有关文件路径方面的信息，可能需要酌情修改。

#### FAQ
- **Q1：如何打开 profile.do 文档？** 
  - **A1：** profile.do 就是一个普通的 **dofile**，因此，你平时怎么打开 dofile 就怎么打开 profile.do。问题的关键是，很多人不知道自己的 **profile.do** 存放在何处。答案是：它存放在 Stata 安装目录下。因此，你可以使用 Stata 的 dofile 编辑器打开 profile.do 文档，命令为： `doedit D:\stata15\profile.do` 或 **doedit `c(sysdir_stata)'/profile.do**。
- **Q2：我的 Stata 安装路径如何查看？**
  - **A2：** 在 Stata 命令窗口中输入 `sysdir` 命令，第一行显示的就是你的 Stata 安装路径。
  ```stata
  . sysdir
     STATA:  D:\stata15\
      BASE:  D:\stata15\ado\base\
      SITE:  D:\stata15\ado\site\
      PLUS:  D:\stata15/ado\plus\
  PERSONAL:  D:\stata15/ado\personal\
  OLDPLACE:  c:\ado\
  ```

#### 何谓 profile.do ？
每次启动 Stata 时，Stata 会自行到安装目录下找到 **profile.do** 文档，并执行里面的所有命令。显然，这些命令通常都是一些使用 Stata 时的基本设定，如文件路径、自动开启日志文件 (log file)、显示格式等。

如下是 `help profilew` 提供的说明：

#### Description

Stata first looks for the file sysprofile.do when it is invoked.  After that, Stata looks for the file profile.do.  If either of these files are found, Stata executes the commands they contain.  

Stata looks **(1)** in the directory where Stata was installed, **(2)** in the current directory, **(3)** along your PATH, **(4)** in your home directory as
defined by Windows's USERPROFILE environment variable, and finally **(5)** along the
 adopath (see adopath).

&emsp;

----




&emsp; 

---
> ### 最新-直播课

> &#x1F34E;  [我的甲壳虫：经典论文精讲 (6小时)](https://lianxh.duanshu.com/#/brief/course/c3f79a0395a84d2f868d3502c348eafc)，嘉宾：连玉君    
> &emsp;     
> **时间**：2020 年 3月9日 | 3月10日，19:00-22:00. [「课程详情」](https://www.lianxh.cn/news/9efc337689a84.html)
  

&emsp; 




---
## 直播视频集锦
- **F.** &#x1F533; [直播-R语言初识](https://lianxh.duanshu.com/#/brief/course/a719037536de4812a630a599f8cd7b43)，嘉宾：游万海。
- **E.** &#x1F4D7; [直播-经济学中的大数据应用](https://lianxh.duanshu.com/#/brief/course/da1a75bc3acc4e238f489af3367efa26)，嘉宾：李兵 (中山大学). [「课程详情」](https://www.lianxh.cn/news/761e6bbfe07a8.html)
- **D.** &#x1F535; [直播-空间计量全局模型及Matlab实现](https://efves.duanshu.com/#/brief/course/ed1bc8fc5e7748c5aca7e2c39d28e20e), 嘉宾：范巧。[「课程详情」](https://www.lianxh.cn/news/6fdb88905419e.html)
- **C.** &#x1F532; [直播-动态面板数据模型](https://efves.duanshu.com/#/brief/course/3c3ac06108594577a6e3112323d93f3e), 嘉宾：连玉君。[「课程详情」](https://www.lianxh.cn/news/594aa12c096ca.html)
- **B.** &#x1F34F; [直播-实证研究设计](https://mp.weixin.qq.com/s/NGwsr92_Vr1DGRbVqDVQIA)，嘉宾：连玉君。[「课程详情」](https://www.lianxh.cn/news/2f31aa3347e83.html)    
- **A.** &#x1F36A; [直播-文本分析与爬虫专题](https://gitee.com/arlionn/Course/blob/master/Done/2020Text.md)，**2020.3.28-29， 4.4-5**，嘉宾：司继春, 游万海。[「课程详情」](https://www.lianxh.cn/news/88426b2faeea8.html)      
- **O.** &#x1F4D5; [公开课-直击面板数据模型](https://lianxh.duanshu.com/#/brief/course/7d1d3266e07d424dbeb3926170835b38)，嘉宾：连玉君，**免费**. [「课程详情」](https://gitee.com/arlionn/PanelData)     







&emsp;

---
>#### 关于我们

> ##### 导航： 📍 [连享会主页](https://www.lianxh.cn)  | 📍 [知乎专栏](https://www.zhihu.com/people/arlionn/) | 📍 [直播课](http://lianxh.duanshu.com) 

![点我 - 更多推文](https://images.gitee.com/uploads/images/2020/0222/181340_968f61e0_1522177.png)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)