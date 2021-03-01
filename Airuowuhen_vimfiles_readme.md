# [vimfiles](https://gitee.com/Airuowuhen/vimfiles)
我的vim配置


安装：

    $ mkdir -p /tmp/vimtest && cd /tmp/vimtest                                # 创建并切换至测试目录
    $ git clone --recursive https://gitee.com/Airuowuhen/vimfiles.git ./.vim  # 克隆项目及vundle子项目
    $ vim -u .vim/vimrc +BundleInstall +qall                                  # 运行安装至当前目录


配置：

    1、创建符号链接 `ln -s ~/.vim/vimrc ~/.vimrc`

    2、安装tags
    1. `sudo apt-get install ctags`
    编辑vim/setting.vim根据自己的需要修改SetTags()函数。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)