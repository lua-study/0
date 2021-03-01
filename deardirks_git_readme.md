# Git操作问题库

#### 介绍
项目中遇到的Git操作问题库

#### 问题列表
1. git push时出现 failed to push some refs 的解决方案
```
在使用git对源代码进行push到gitHub时可能会出错(很多人会尝试下面的命令把当前分支代码上传到master分支上)。

$ git push -u origin master
但依然没能解决问题

出现错误的主要原因是github中的README.md文件不在本地代码目录中

可以通过如下命令进行代码合并【注：pull=fetch+merge]
git pull --rebase origin master
此时git push差不多就可以了
```
2. 使用git连接码云的远程项目库
```
目标：将本地的项目代码存储在远程仓库中。 
第一步： 
下载安装git 
注册码云的帐号 记好邮箱 和用户名 

第二步： 
代码操作git 
1. 首次使用码云配置 输入： 

git config --global user.email "you@example.com" 
git config --global user.name "Your Name" 

2.对本地git库进行初始化（在项目文件下） 
git init 
3.链接远程仓库 
git remote add origin "你的项目地址(刚才在码云创建的项目的地址)" 

4.将当前项目目录下的文件提交到git库中 
git add . 

5.对项目的修改和提交作描述： 
git commit -m ‘说明内容’ 

6.将本地的文件提交到远程仓库中 
git push -u origin master 

7.输入用户名和登录密码； 

```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)