
# 中国科学技术大学课程资源
[![Stars](https://img.shields.io/github/stars/USTC-Resource/USTC-Course.svg?label=Stars&style=social)](https://github.com/USTC-Resource/USTC-Course/stargazers)
[![Forks](https://img.shields.io/github/forks/USTC-Resource/USTC-Course.svg?label=Forks&style=social)](https://github.com/USTC-Resource/USTC-Course/network/members)
[![Build](https://travis-ci.org/USTC-Resource/USTC-Course.svg?branch=master)](https://travis-ci.org/USTC-Resource/USTC-Course?branch=master)
[![repo-size](https://img.shields.io/github/repo-size/USTC-Resource/USTC-Course.svg)]()
[![License](https://i.creativecommons.org/l/by-nc-sa/4.0/80x15.png)](http://creativecommons.org/licenses/by-nc-sa/4.0/)

>>本仓库收录中国科学技术大学众多课程资源的笔记，总结，经验等**学生原创内容**

# 目录索引
* [版权说明](#版权说明)
* [反馈方式](#反馈方式)
* [资料下载](#资料下载)
* [课程结构](#课程结构)
* [课程关系](#课程关系)
* [课程目录](#课程目录)
* [贡献投稿](#贡献投稿)

# 版权说明
本仓库分享资料遵守其创作者之规定, 由同学自愿投稿，仅接收学生原创的或者获得授权的资源。

对无特别声明的资料，谨以[知识共享署名 - 非商业性使用 - 相同方式共享 4.0 国际许可协议](http://creativecommons.org/licenses/by-nc-sa/4.0/) 授权。![](https://i.creativecommons.org/l/by-nc-sa/4.0/80x15.png)

请创作者及公众监督，如有资料违反许可协议，请告知我们改正错误。

# 反馈方式
- [issue](https://github.com/USTC-Resource/USTC-Course/issues/new)
-  email 

# 资料下载
[戳我(●'◡'●)](https://ustc-resource.github.io/USTC-Course)

 

# 课程结构
每门课程大致结构如下，有些栏目可能没有，也可以自己添加认为合理的栏目
```
course
├ codes
│   ├ mbinary0
│   ├ mbinary1
│   └ mbinary2
├ labs
├ exams
├ notes
└ README.md
```
# 课程关系
![](https://user-images.githubusercontent.com/29198767/53245024-851b1280-36e7-11e9-9d22-7ee65446c68a.png)

更多信息可以下载[官网的培养方案](https://www.teach.ustc.edu.cn/education/241.html/attachment/14-215%E8%AE%A1%E7%AE%97%E6%9C%BA%E5%AD%A6%E9%99%A2-2013)

# 课程目录
**根据拼音字母排序**, 可以通过在此页面搜索课程名快速定位。

* [.](.)
    * [编译原理和技术](./编译原理和技术)
    * [操作系统原理与设计](./操作系统原理与设计)
    * [c程序设计](./c程序设计)
    * [代数结构](./代数结构)
    * [大学物理实验](./大学物理实验)
    * [光学与原子物理](./光学与原子物理)
    * [计算机网络](./计算机网络)
    * [计算机系统详解](./计算机系统详解)
    * [计算机与信息类](./计算机与信息类)
    * [计算机组成原理](./计算机组成原理)
    * [模拟与数字电路](./模拟与数字电路)
    * [数据结构](./数据结构)
    * [数理方程](./数理方程)
    * [数理逻辑](./数理逻辑)
    * [算法基础](./算法基础)
    * [随机过程](./随机过程)
    * [utils](./utils)
    * [Web-信息处理与应用](./Web-信息处理与应用)
    * [微机原理与系统](./微机原理与系统)

# 贡献投稿
[这里是](https://github.com/USTC-Resource/USTC-Course/graphs/contributors) GitHub commit 贡献名单
内容创作者包括：

- mbinary
- Lyncien
- kingzevin
- ksqsf
- cclauss
- 吴颖文
- 童世炜

如果遗漏了你的名字，可自行 PR 或者联系贡献者。

欢迎大家的参与与贡献^_^
* 仅接受学生原创的或者获得授权的资源
* github 上不能直接上传大于 100mb 的文件。对于超过 100 mb 的文件，可以存在网盘，然后在 README 文件中贴上链接
* 文件内容的改动会使 git 重新上传, 在没有必要的情况下, 不要对二进制文件做任何更改.

 > .git/info/sparse-checkout  #这里工作目录就是在那个 repo 主页下

#如果还有其他目录，都像上面一样加入即可，如 `echo  "计算机与信息类/图论/slides" >> .git/info/sparse-checkout`
#只需记住的是 加入的目录应该在远程仓库存在，否则报错“error: Sparse checkout leaves no entry on the working directory”

git pull origin master
git remote add upstream git@github.com:mbinary/USTC-CS-Courses-Resource.git
```
更新内容后
```shell
git fetch upstream/master
git merge upstream/master
```
-->



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)