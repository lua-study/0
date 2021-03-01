# 克隆代码

    git clone  

# 获取代码

    git pull    ： 
    //git pull origin master:master

    // 强制拉取远端代码，覆盖本地
    git fetch --all
    git reset --hard origin/master
    git pull

# 提交代码

    git add .   //暂存修改内容
    git commit -m '修改信息'    //提交到本地
    git push    ：    //推送到远程仓库
    git push -u origin master   //设置当前远程origin分支为默认分支推送，以后就可以用 git push 代替
    git push -f origin master  //强制提交

# 远程仓库管理

    git remote    //查看远程仓库信息
    git remote rm    //删除远程仓库
    git remote add       //新增远程仓库

# 分支

    git branch  //查看分支信息
    git checkout -b      //新增并切换到新分支
    git checkout     //切换分支
    git branch --set-upstream-to origin/master master     //关联本地分支和远程分支

    //删除分支
    git branch -d(-D) master  //-D强制删除

# 合并分支

    //merge合并
    git merge       //合并分支, –-no-ff 可以保存你之前的分支历史。--allow-unrelated-histories 合并非相关分支
    //git merge --no-ff -m "merged bug fix 001" issue-001 --allow-unrelated-histories

    //rebase合并
    git rebase master # 将dev上的c2、c5在master分支上做一次衍合处理
    # git提示出现了代码冲突，此处为之前埋下的冲突点，处理完毕后
    git add readme # 添加冲突处理后的文件
    git rebase --continue # 加上--continue参数让rebase继续处理


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)