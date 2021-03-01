# GitTest

![git](https://images.gitee.com/uploads/images/2020/0515/103532_3818a453_889341.png "https://git-scm.com/book/zh/v2")

## 一、git中文乱码问题

1. 执行指令

		git config --global core.quotepath false
		git config --global gui.encoding utf-8
		git config --global i18n.commit.encoding utf-8
		git config --global i18n.logoutputencoding utf-8

2. 配置环境变量

		在系统环境变量中加入：**LESSCHARSET=utf-8**

		windows下：set LESSCHARSET=utf-8
		Linux下：export LESSCHARSET=utf-8

## 二、关联本地和远程仓库

1. 指令版
 
    - 本地和码云上分别创建项目
    - 执行如下指令：

			git init
			git add .
			git commit -m "init"
			git remote add origin https://gitee.com/cuncaojin/git6.git
			git pull origin master --allow-unrelated-histories
			git push --set-upstream origin master

		注：https://gitee.com/cuncaojin/git6.git 为自己的仓库地址
		
2. 手工版

	- 本地创建Android项目，码云上创建项目
	- Create git Repository，创建git仓库，绑定到本地android项目
	- add、commit本地项目并push
	- 上一步push出错，会让选择远程仓库，此时复制码云项目地址，设置远程仓库
	- pull拉取仓库代码，如果失败报“fatal: refusing to merge unrelated histories”，执行

			git pull origin master --allow-unrelated-histories

	   **前提：** 都commit后再执行，防止有文件本地与远程仓库因有文件冲突而pull失败
	- git push --set-upstream origin master

## 三、 IDEA中，git忽略.idea文件夹无效处理

    情形：明明在gitignore中忽略了.idea文件夹,但是提交时仍旧会出现.idea内文件变动的情况
    原因：.idea已经被git跟踪，之后再加入.gitignore后是没有作用的
    解决：清除.idea的git缓存，在.gitignore文件中添加.idea并执行：

		git rm -r --cached .idea

## 四、基础概念
	
1. **`origin`** ：默认远程仓库名

	**注意：** 该名字是可自定义的，如：`git clone -o myResp https://gitee.com/cuncaojin/GitTest.git`，则远程仓库名是`myResp`
	
1. **`master`**： 默认本地和远程分支名

1. **[远程跟踪分支](https://git-scm.com/book/zh/v2/Git-%E5%88%86%E6%94%AF-%E8%BF%9C%E7%A8%8B%E5%88%86%E6%94%AF)** 是远程分支状态的引用，命名格式：**`(remote)/(branch)`**，如：`origin/master`。

	**跟踪分支** 是与远程分支有直接关系的本地分支。 当克隆一个仓库时，它通常会自动地创建一个跟踪 origin/master 的 master 分支。如果在一个跟踪分支上输入 git pull，Git 能自动地识别去哪个服务器上抓取、合并到哪个分支。

1. 本地的修改，如果没有提交，在merge或pull时会被**覆盖**！
1. git commit -am "xxx" 只会添加并提交被git追踪的文件，新建的文件没有add前，都是未受git管理的，不会被递交，但在执行pull或merge时会被覆盖掉！高级版本git会报错，防止了被**覆盖**。
1. **`HEAD`** 是当前分支引用的指针，它总是指向该分支上的最后一次提交。 这表示 HEAD 将是下一次提交的父结点。 通常，理解 HEAD 的最简方式，就是将它看做 你的上一次提交的快照。
1. **`索引`** 是你的 预期的下一次提交。 我们也会将这个概念引用为 Git 的“暂存区域”，这就是当你运行 git commit 时 Git 看起来的样子

- [git工作流程图](https://git-scm.com/book/en/v2/images/reset-workflow.png)

- [工作目录添加文件图解](https://git-scm.com/book/en/v2/images/reset-ex1.png)
	
- [git add图解](https://git-scm.com/book/en/v2/images/reset-ex2.png)
	
- [git commit图解](https://git-scm.com/book/en/v2/images/reset-ex3.png)
	
- [修改工作目录文件](https://git-scm.com/book/en/v2/images/reset-ex4.png)
	
- [再次git add图解](https://git-scm.com/book/en/v2/images/reset-ex5.png)
	
- [再次git commit图解](https://git-scm.com/book/en/v2/images/reset-ex6.png)

## 五、常用指令

    指令忘记怎么办？自助！
    git
    git xxx --help，如git add --help

1. **git init**
    
    将当前目录作为git仓库

1. **git clone**
    
    拷贝一个Git仓库默认分支到本地。
	
		`git clone -b stable https://github.com/flutter/flutter.git` 拷贝指定分支

1. **git add**
    
    将该文件添加到缓存。如添加目录下所有文件到暂存区：`git add .`

1. **git rm -f  **

    移除文件，如果没有加入到暂存区，可以不加-f参数强制删除
        
        git rm --cached   从缓存区移除
        git rm –r *  递归删除目录及文件

1. **git mv README README.md**

    移动或重命名文件
    
1. **git status -s**

    查看上次提交之后是否有修改，如果没加该参数会详细输出内容

1. **git diff**

    查看执行 git status 的结果的详细信息
    
    - `git diff`: 尚未缓存的改动
    - `git diff --cached`: 查看已缓存的改动
    - `git diff HEAD`：查看已缓存的与未缓存的所有改动
    - `git diff --stat`：显示摘要而非整个diff
    - **`git diff branch1 branch2 --stat`** 显示出所有有差异的文件列表
    - `git diff branch1 branch2 文件名(带路径)` 显示指定文件的详细差异
    - `git diff branch1 branch2` 显示出所有有差异的文件的详细差异

1. **git commit**

    将缓存区内容添加到仓库中

    - **`git commit -am '备注'`**：添加并提交，等于add+commit

1. **git commit --amend**

    追加提交。输入该命令后会要求修改msg，保存退出即可。

1. **git reset HEAD**
    
	取消已缓存的内容，相当于取消add操作，但保留修改。没有add的文件commit操作提交不到本地仓库。 
	
        HEAD表示当前版本，也就是最新的提交1094adb...（注意我的提交ID和你的肯定不一样），
        HEAD^表示上一个版本
		HEAD~表示上一个版本
        HEAD^^表示上上一个版本
        往上100个版本写100个^，可写成HEAD~100
            
    - [**`git reset HEAD~1` 或 `git reset HEAD~`**](https://git-scm.com/book/en/v2/images/reset-mixed.png)
	
        取消上一次提交，不删除现有修改。或 **git reset "HEAD^1"**
		撤销一上次提交，同时还会取消暂存所有的东西。 于是，我们回滚到了所有 git add 和 git commit 的命令执行之前。
    
    - [**`git reset --hard HEAD~1`**](https://git-scm.com/book/en/v2/images/reset-hard.png)

        回退到上一次提交，删除上一次提交后的所有修改。也可写为：
        
            git reset --hard "HEAD^"
			
		或
			
			git reset --hard HEAD~
        
        注意^为cmd.exe的escape字符，windows下需要加引号使用。

    - git reset --hard HEAD~n
    
        取消前n次commit，并删除修改。恢复到最近一次commit后的代码，指令：

            git reset --hard HEAD

    - **git reset --hard bbfd81e**
    
        硬回退到bbfd81e开头的commitId版本

1. **git reset --hard origin/master**

    强制更新本地仓库使用远程版本代码

1. git log --reverse --oneline

    逆向查看简洁版日志
        
    - **`git log --oneline --graph`**
        
        拓扑图形式显示简洁版日志
    
    - **`git log --author=zhangsan --oneline -5`**
    
        查看zhangsan用户的5条日志
    
    - `git log --oneline --before={3.weeks.ago} --after={2010-04-18} --no-merges`
    
        查看项目中三周前且在四月十八日之后的所有提交，我可以执行这个（我还用了 --no-merges 选项以隐藏合并提交）
    
1. **git reflog --oneline**

    查看当前版本后的历史记录，用于回退到未来版本    

1. **git push [remote-name] [branch-name]**

	推送本地commit内容到远程仓库分支，如`git push origin master`

	- `git push -u origin master -f` 或 `git push -f`
		
		强制push更新远程仓库，可用于回退远程仓库历史版本。
    
1. **git remote -v**

    查看远程仓库    

1. git fetch

	从远程抓取本地没有的数据，但并不会修改工作目录中的内容。它只会获取数据然后让你自己合并。`git pull = git fetch + git merge`。 

1. **git pull    : **

    拉取远程仓库某分支。如：
    
        git pull origin dev:dev
            
    取回远程库中的dev分支，与本地的dev分支进行merge。
    如果是要与本地当前分支merge，则冒号后面的 可以不写，如：
        
        git pull origin dev
    
## 六、分支管理

> 实现开发新代码和维护已上线代码两不误

1. **查看分支** `git branch`
    
        $ git branch
        * master
          testing
        含义：当前项目有2个分支，现在在星花所指的master分支
        
    - `git branch -a` 查看所有分支
    - `git branch -r` 查看远程分支
    - **`git branch -vv`** 查看所有本地及远程分支对应关系

    ![查看分支示例图](https://images.gitee.com/uploads/images/2020/0515/103217_04bfd3b6_889341.png "屏幕截图.png")
    
1. **创建分支**

    - 创建本地分支: `git branch 新分支名`
	
	- 创建远程分支： `git push --set-upstream origin 远程分支名`
	
		将本地分支推送到远程分支，即创建了远程分支

1. **切换分支** `git checkout 要切换到的分支名`

	- 如切换到主分支：`git checkout master`
	
	- **`git checkout -b 新分支名`**
		
		创建并切换到某分支
		
1. **删除分支**
	
	- 删除本地分支 `git branch -d 本地分支名`
	
	- 删除远程分支
	
		- 方式1:  `git push origin :远程分支名`
		- 方式2： `git push origin --delete 远程分支名`

1. **创建并切换分支，并设置跟踪分支**  **`git checkout -b dev origin/dev`** 

    创建并切换到本地dev分支，并设置其[跟踪分支](https://git-scm.com/book/zh/v2/Git-%E5%88%86%E6%94%AF-%E8%BF%9C%E7%A8%8B%E5%88%86%E6%94%AF)为origin/dev。
 
 
1. **关联上游分支** `git push --set-upstream origin dev`

    将当前分支关联到远程origin仓库dev分支。推送分支，就是把该分支上的所有本地提交推送到远程库。

1. **合并分支** `git merge 分支名`

    合并指定分支到当前分支

1. **解决合并冲突**

    merge后可能会有冲突，修改冲突后，我们可以用 git add 告诉 Git 文件冲突已经解决

### 七、merge操作时，忽略分支差异文件处理

1. 工程目录下创建.gitattribute文件
2. 向文件中增加如下内容：
	
		要忽略的文件 merge=ours       
		*.md merge=ours
		README.md merge=ours
		...

3. 执行 

		git config --global merge.ours.driver true
	
**注意：** 
	
- merge=ours中不能有空格，和前面要有空格;
- **`只有先修改的忽略文件的分支，往后来修改的忽略文件的分支中合并，才会生效，否则忽略失效`**
- 含义同上。合并到当前分支的话，要保证要合并到的分支的被忽略的文件是最后被修改的，否则.gitattribute文件中配置的忽略会失效！

**举例：** 
	
- release和debug两个分支都有个config文件，现要将debug分支合并到release分支且忽略config文件。
- 需要先改debug分支的config，然后再改release分支的config，然后再执行git merge debug时，就会忽略config文件，否则不会忽略。

### 八、储藏工作与恢复工作

1. [**储藏工作** `git stash`](https://www.liaoxuefeng.com/wiki/896043488029600/900388704535136)

	存储当前状态。用于想临时切换到其他分支进行操作，又不想提交当前分支情况。

2. [**恢复工作** `git stash pop`](https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E5%82%A8%E8%97%8F%E4%B8%8E%E6%B8%85%E7%90%86)

	恢复到之前stash存储前的状态，并删除stash内容。
	
		工作现场还在，Git把stash内容存在某个地方了，但是需要恢复一下，有两个办法：
		一是用git stash apply恢复，但是恢复后，stash内容并不删除，你需要用git stash drop来删除；
		另一种方式是用git stash pop，恢复的同时把stash内容也删了

### 九、[不同分支同样bug修复](https://www.liaoxuefeng.com/wiki/896043488029600/900388704535136) `git cherry-pick  `
	
复制一个特定的提交到当前分支。

**用处：** 在两个分支存在同样的bug时，一个分支处理了bug后，另一个分支只需要复制这次提交即可，不用再在另一个分支再操作一遍。
	
### 打标签

1. **列出已有的标签** `git tag`
    
    git tag -l 'v1.4.2.*' 列出符合某种正则规则的标签
    
1. **git tag 标签名**
    
    打标签
    
    git tag -a v1.4 -m 'my version 1.4' 新建含附注的标签

        -a: annotated
        -m: message

1. **git tag -a 标签名 commitId**

    追加标签。git tag -a v0.9 85fc7e7：向85fc7e7提交追加标签v0.9
    
1. **git tag -d 标签名**
    
    删除标签，如：git tag -d v1.1

1. **git show 标签名**

    查看此版本所修改的内容，如：git show v1.0

1. **git push origin 标签名**

    分享标签，即push标签到远程仓库分支。如：git push origin v1.5。
    git push 并不会把标签传送到远端服务器上，只有通过显式命令才能分享标签到远端仓库。
    
    git push origin --tags 一次推送所有本地新增的标签上去

### 发布 Release

	高级的tag，不属于git功能范畴，Github/GitEE等支持。[参考](https://gitee.com/cuncaojin/GitTest/releases/V3.0)

### [打破GitHub单个文件限制100M大小限制](https://blog.csdn.net/cuncaojin/article/details/100904386)

### 子模块

1. **git submodule add *https://gitee.com/cuncaojin/GitTestModelOne* git**

## 插图

![记录每次更新到仓库](https://images.gitee.com/uploads/images/2020/0515/104029_de748d93_889341.png "https://git-scm.com/book/zh/v2/Git-%E5%9F%BA%E7%A1%80-%E8%AE%B0%E5%BD%95%E6%AF%8F%E6%AC%A1%E6%9B%B4%E6%96%B0%E5%88%B0%E4%BB%93%E5%BA%93")
![分支](https://images.gitee.com/uploads/images/2020/0515/104312_7b543ae7_889341.png "https://git-scm.com/book/zh/v2/Git-%E5%88%86%E6%94%AF-%E5%88%86%E6%94%AF%E7%AE%80%E4%BB%8B")

## 参考

1. [git官方教程](https://git-scm.com/book/zh/v1/Git-%E5%9F%BA%E7%A1%80-%E6%89%93%E6%A0%87%E7%AD%BE)
1. [git官方教程Book第二版](https://git-scm.com/book/zh/v2) 
1. [廖雪峰git教程](https://www.liaoxuefeng.com/wiki/896043488029600/897013573512192)
1. [菜鸟git教程](https://www.runoob.com/git/git-basic-operations.html)
1. [莫烦git教程](https://morvanzhou.github.io/tutorials/others/git/3-1-reset/#reset-%E5%9B%9E%E5%88%B0-add-%E4%B9%8B%E5%89%8D)
1. [易百教程](https://www.yiibai.com/git/git_fetch.html)
1. [Android studio项目上传至oschina（码云）教程](https://blog.csdn.net/lei_notes/article/details/53287447)
1. [git中文乱码处理](https://juejin.im/post/5b4ca078e51d4519115cfa66)
1. [忽略 .idea文件夹无效处理](https://blog.csdn.net/lj402159806/article/details/78599765)
1. [git无法pull仓库refusing to merge unrelated histories处理](https://blog.csdn.net/lindexi_gd/article/details/52554159)
1. [git获取远程服务器的指定分支](https://www.cnblogs.com/phpper/p/7136048.html)
1. [\[Git高级教程(二) \]远程仓库版本回退方法](https://blog.csdn.net/fuchaosz/article/details/52170105)
1. [为何无法正确执行git reset –hard HEAD^](https://blog.csdn.net/m0_37477061/article/details/83004887)
1. [忽略merge差异文件](https://www.jianshu.com/p/716fafb6f39e)
1. [git merge合并忽略某些文件](https://blog.csdn.net/qq_39176597/article/details/89210686)
1. [打破GitHub单个文件限制100M大小限制](https://blog.csdn.net/cuncaojin/article/details/100904386)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)