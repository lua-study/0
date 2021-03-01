# git项目测试

#### 项目介绍
git项目测试

#### 软件架构
软件架构说明


#### 安装教程

1、本地初始化一个项目
首先，你需要执行下面两条命令，作为 git 的基础配置，作用是告诉 git 你是谁，你输入的信息将出现在你创建的提交中。

git config --global user.name "你的名字或昵称"
git config --global user.email "你的邮箱"
然后在你的需要初始化版本库的文件夹中执行：

git init 
git remote add origin   //注:项目地址形式为:https://gitee.com/xxx/xxx.git或者 git@gitee.com:xxx/xxx.git
这样就完成了一次版本你的初始化。

如果你想克隆一个项目，只需要执行：

git clone  
2、完成第一次提交
进入你已经初始化好的或者克隆项目的目录,然后执行：

git pull origin master
 
git add .
git commit -m "第一次提交"
git push origin master
然后如果需要账号密码的话就输入账号密码，这样就完成了一次提交。
按照本文档新建的项目时，在码云平台仓库上已经存在 readme 文件，故在提交时可能会存在冲突，这时您需要选择的是保留线上的文件或者舍弃线上的文件，如果您舍弃线上的文件，则在推送时选择强制推送，强制推送需要执行下面的命令：

git push origin master -f
如果您选择保留线上的 readme 文件,则需要先执行：

git pull origin master


#### 使用说明

1. xxxx
2. xxxx
3. xxxx

#### 参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


#### 码云特技

1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [http://git.mydoc.io/](http://git.mydoc.io/)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)