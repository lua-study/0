# **Hexo_NexT-cli**
![node-v8.11.2][1]
![npm-v5.6.0][2]
![Hexo-v3.7.1][3]
![gulp-v3.9.1][4]

---

本项目为Hexo博客资源文件，使用NexT主题，已经做了常见的优化配置，可以直接下载修改相关配置，快速搭建自己的博客。

> **注意：** 该项目仅做了NexT的优化配置，其他主题自行配置优化

我的博客地址：
> [https://anyer.github.io/alex.d-blog/][5]
> [https://alex_d.gitee.io/alex.d-blog/][6]

---

### **环境要求**

- 必要
	- Node.js  >=6.9.0 (新版Hexo)
	- npm
	- Git
- 推荐
	- nvm （Node.js版本管理工具）
	- nrm （NPM镜像源管理工具）
	- cnpm
	- Markdown编辑器 （依据个人喜好选择）

---


### **使用说明**

``` bash

# 拉取项目到本地
git clone https://gitee.com/alex_d/HexoBlogSource

# 安装需要的模块（国内推荐使用cnpm install，需要提前安装cnpm)
npm install

# 生成静态文件（可缩写  hexo g）
hexo generate

# 静态资源打包
gulp

# 本地运行 （可缩写 hexo s）
hexo server

```


> **注意：** 如需远程部署可以修改主目录配置文件 `_config.yml` 的 url、root、deploy等内容。
> 远程部署使用命令 `hexo deploy` 可缩写为 `hexo d`，具体部署方式，查看下文推荐阅读。

---

###  **推荐阅读**

- Pages服务
	- [码云Pages使用说明][7]
	- [GitHub的Pages使用说明][8]
	- [Coding的Page使用说明][9]
	- 其他平台自行百度...
- Hexo
	- [Hexo中文站点][10]
	- [Hexo项目GitHub地址][11]
- NexT主题使用及优化
	- [用Hexo+Github 搭建属于自己的博客 详细步骤 - CSDN博客][12]
	- [2018最新版Hexo博客Next主题6.0配置优化 - CSDN博客][13]
	- [hexo链接持久化终极解决之道 - CSDN博客][14]
	- [打造个性超赞博客Hexo+NexT+GithubPages的超深度优化 | reuixiy][15]
	- [基于Hexo+Github+Coding搭建个人博客——基础篇(从菜鸟到放弃) | ookamiAntD's Blog][16]
	- [Hexo-Next-主题优化(一) - 简书][17]
	- [Hexo 4：【高阶】NexT 主题优化之加入网易云音乐、网易云跟帖、动态背景、自定义主题、统计功能][18]
	
	- 如上内容基本够用，需要其他优化自行百度...
- Hexo自动部署
	- [Github和Coding同步部署hexo说明(搭建篇) | Orange's Avenue][19]
	- [\[小题大做\] Github + Jenkins 实现自动化部署 hexo 博客静态文件 - 个人文章 - SegmentFault 思否][20]
	- [用Jenkins自动部署hexo搭建的GitHub静态博客 - 51Testing软件测试网][21]
	- [搭建github免费个人博客之Travis自动部署Hexo一_百度经验][22]

其他内容后续补充~


  [1]: https://img.shields.io/badge/node-v8.11.2-green.svg
  [2]: https://img.shields.io/badge/npm-v5.6.0-brightgreen.svg
  [3]: https://img.shields.io/badge/hexo-v3.7.1-blue.svg
  [4]: https://img.shields.io/badge/gulp-v3.9.1-orange.svg
  [5]: https://anyer.github.io/alex.d-blog/
  [6]: https://alex_d.gitee.io/alex.d-blog/
  [7]: http://git.mydoc.io/?t=154714
  [8]: https://pages.github.com/
  [9]: https://coding.net/pages/
  [10]: https://hexo.io/zh-cn/
  [11]: https://github.com/hexojs/hexo
  [12]: https://blog.csdn.net/wilver/article/details/75246428
  [13]: 2018%E6%9C%80%E6%96%B0%E7%89%88Hexo%E5%8D%9A%E5%AE%A2Next%E4%B8%BB%E9%A2%986.0%E9%85%8D%E7%BD%AE%E4%BC%98%E5%8C%96%20-%20CSDN%E5%8D%9A%E5%AE%A2
  [14]: https://blog.csdn.net/yanzi1225627/article/details/77761488
  [15]: https://reuixiy.github.io/technology/computer/computer-aided-art/2017/06/09/hexo-next-optimization.html
  [16]: http://yangbingdong.com/2017/build-blog-hexo-base/
  [17]: https://www.jianshu.com/p/3ff20be8574c
  [18]: http://cherryblog.site/Hexo-high-level-tutorialcloudmusic,bg-customthemes-statistical.html
  [19]: https://linky-fan.github.io/2018/03/08/gitandcoding/
  [20]: https://segmentfault.com/a/1190000009232463
  [21]: http://www.51testing.com/html/90/n-3725690.html
  [22]: https://jingyan.baidu.com/article/359911f5a3744657fe030683.html

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)