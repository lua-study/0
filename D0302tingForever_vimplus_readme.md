![vimplus-logo][1]

An automatic configuration program for vim
===============================================

 
       
       
       
       
       
       
 

![main][2]

## 安装

### Mac OS X

#### 安装[HomeBrew][3]
 
    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

#### 安装vimplus

    git clone https://github.com/chxuan/vimplus.git ~/.vimplus
    cd ~/.vimplus
    ./install.sh
    
#### 设置Nerd Font

为防止vimplus显示乱码，需设置mac终端字体为`Droid Sans Mono Nerd Font`。

#### 更新vimplus

紧跟vimplus的步伐，尝鲜新特性

    ./update.sh
    

### Linux 64-bit

#### 支持以下发行版

 
 
       
       
       
       
       
       
       
       
       
       
 
 
       
       
       
 
 


#### 安装vimplus

    git clone https://github.com/chxuan/vimplus.git ~/.vimplus
    cd ~/.vimplus
    ./install.sh //不加sudo
    
#### 设置Nerd Font

为防止vimplus显示乱码，需设置linux终端字体为`Droid Sans Mono Nerd Font`。

#### 多用户支持

将vimplus在某个用户下安装好后，若需要在其他用户也能够使用vimplus，则执行

    sudo ./install_to_user.sh username1 username2 //替换为真实用户名
    
#### 更新vimplus

紧跟vimplus的步伐，尝鲜新特性

    ./update.sh


### Android 64-bit([Termux][87])

#### 安装vimplus

    git clone https://github.com/chxuan/vimplus.git ~/.vimplus
    cd ~/.vimplus
    ./install.sh
    
#### 更新vimplus

紧跟vimplus的步伐，尝鲜新特性

    ./update.sh
    

### Docker

[ubuntu-vimplus][79]是vimplus基于ubuntu18.04的docker镜像，无需安装vimplus，即可快速体验vimplus带来的快乐

    docker run -it chxuan/ubuntu-vimplus
    

## 自定义

> * [~/.vimrc][82]为vimplus的默认配置，一般不做修改
> * [~/.vimrc.custom.plugins][83]为用户自定义插件列表，用户增加、卸载插件请修改该文件
> * [~/.vimrc.custom.config][84]为用户自定义配置文件，一般性配置请放入该文件，可覆盖[~/.vimrc][82]里的配置


## 插件列表

| 插件                                | 说明                                                                           |
| -------                             | -----                                                                          |
| [cpp-mode][58]                      | 提供生成函数实现、函数声明/实现跳转、.h .cpp切换等功能(I'm author:smile:)      |
| [vim-edit][72]                      | 方便的文本编辑插件(I'm author:smile:)                                          |
| [change-colorscheme][27]            | 随心所欲切换主题(I'm author:smile:)                                            |
| [prepare-code][67]                  | 新建文件时，生成预定义代码片段(I'm author:smile:)                              |
| [vim-buffer][70]                    | vim缓存操作(I'm author:smile:)                                                 |
| [vimplus-startify][66]              | vimplus开始页面(修改自[mhinz/vim-startify][25])                                |
| [tagbar][74]                        | 使用[majutsushi/tagbar][13]的v2.3版本，[taglist][14]的替代品，显示类/方法/变量 |
| [vim-plug][4]                       | 比[Vundle][54]下载更快的插件管理软件                                           |
| [YouCompleteMe][5]                  | 史上最强大的基于语义的自动补全插件，支持C/C++、C#、Python、PHP等语言           |
| [NerdTree][6]                       | 代码资源管理器                                                                 |
| [vim-nerdtree-syntax-highlight][52] | NerdTree文件类型高亮                                                           |
| [nerdtree-git-plugin][53]           | NerdTree显示git状态                                                            |
| [vim-devicons][15]                  | 显示文件类型图标                                                               |
| [Airline][8]                        | 可以取代[powerline][9]的状态栏美化插件                                         |
| [auto-pairs][10]                    | 自动补全引号、圆括号、花括号等                                                 |
| [LeaderF][56]                       | 比[ctrlp][12]更强大的文件的模糊搜索工具                                        |
| [ack][62]                           | 强大的文本搜索工具                                                             |
| [vim-surround][16]                  | 自动增加、替换配对符的插件                                                     |
| [vim-commentary][17]                | 快速注释代码插件                                                               |
| [vim-repeat][18]                    | 重复上一次操作                                                                 |
| [vim-endwise][19]                   | if/end/endif/endfunction补全                                                   |
| [tabular][20]                       | 代码、注释、表格对齐                                                           |
| [vim-easymotion][23]                | 强大的光标快速移动工具，强大到颠覆你的插件观                                   |
| [incsearch.vim][24]                 | 模糊字符搜索插件                                                               |
| [vim-fugitive][36]                  | 集成Git                                                                        |
| [gv][64]                            | 显示git提交记录                                                                |
| [vim-slash][50]                     | 优化搜索，移动光标后清除高亮                                                   |
| [echodoc][57]                       | 补全函数时在命令栏显示函数签名                                                 |
| [vim-smooth-scroll][60]             | 让翻页更顺畅                                                                   |
| [clever-f.vim][68]                  | 强化f和F键                                                                     |


## 快捷键

以下是部分快捷键，可通过vimplus的`,h`命令查看[vimplus帮助文档][59]。

| 快捷键              | 说明                                      |
| -------             | -----                                     |
| `,`                 | Leader Key                                |
| ` n`         | 打开/关闭代码资源管理器                   |
| ` t`         | 打开/关闭函数列表                         |
| ` a`         | .h .cpp 文件切换                          |
| ` u`         | 转到函数声明                              |
| ` U`         | 转到函数实现                              |
| ` u`         | 转到变量声明                              |
| ` o`         | 打开include文件                           |
| ` y`         | 拷贝函数声明                              |
| ` p`         | 生成函数实现                              |
| ` w`         | 单词跳转                                  |
| ` f`         | 搜索~目录下的文件                         |
| ` F`         | 搜索当前目录下的文本                      |
| ` g`         | 显示git仓库提交记录                       |
| ` G`         | 显示当前文件提交记录                      |
| ` gg`        | 显示当前文件在某个commit下的完整内容      |
| ` ff`        | 语法错误自动修复(FixIt)                   |
| ` `             | 切换到上一个buffer                        |
| ` `             | 切换到下一个buffer                        |
| ` d`         | 删除当前buffer                            |
| ` D`         | 删除当前buffer外的所有buffer              |
| `vim`               | 运行vim编辑器时,默认启动开始页面          |
| ` `              | 显示语法错误提示窗口                      |
| ` `              | 显示上一主题                              |
| ` `             | 显示下一主题                              |
| ` l`         | 按竖线对齐                                |
| ` =`         | 按等号对齐                                |
| `Ya`                | 复制行文本到字母a                         |
| `Da`                | 剪切行文本到字母a                         |
| `Ca`                | 改写行文本到字母a                         |
| `rr`                | 替换文本                                  |
| ` r`         | 全局替换，目前只支持单个文件              |
| `rev`               | 翻转当前光标下的单词或使用V模式选择的文本 |
| `gcc`               | 注释代码                                  |
| `gcap`              | 注释段落                                  |
| `vif`               | 选中函数内容                              |
| `dif`               | 删除函数内容                              |
| `cif`               | 改写函数内容                              |
| `vaf`               | 选中函数内容（包括函数名 花括号）         |
| `daf`               | 删除函数内容（包括函数名 花括号）         |
| `caf`               | 改写函数内容（包括函数名 花括号）         |
| `fa`                | 查找字母a，然后再按f键查找下一个          |
| ` e`         | 快速编辑~/.vimrc文件                      |
| ` s`         | 重新加载~/.vimrc文件                      |
| ` vp`        | 快速编辑~/.vimrc.custom.plugins文件       |
| ` vc`        | 快速编辑~/.vimrc.custom.config文件        |
| ` h`         | 打开vimplus帮助文档                       |
| ` H`         | 打开当前光标所在单词的vim帮助文档         |
| `  t` | 生成try-catch代码块                       |
| `  y` | 复制当前选中到系统剪切板                  |
| `  i` | 安装插件                                  |
| `  u` | 更新插件                                  |
| `  c` | 删除插件                                  |


## FAQ

- **`vimplus怎么安装新插件？`**

    编辑[~/.vimrc.custom.plugins][83]，添加自定义插件。

- **`vimplus怎么添加自定义配置？`**

    编辑[~/.vimrc.custom.config][84]，添加自定义配置。

- **`vimplus安装脚本会在自己电脑上安装哪些软件？`**

    网络良好情况下，vimplus只需30分钟左右即可将vim cpp环境配置好，vimplus真正的做到了一键配置，不让用户操心。vimplus会安装一些必备软件，比如说python、cmake、gcc、fontconfig等，vimplus也考虑到了有些系统的vim不支持python，它会自动去下载vim源码将python支持编译进去，vimplus也会安装nerd-font不让vim显示出现乱码，最最重要的是vimplus实现了ycm自动编译安装，给折腾了几天ycm都没有安装好的用户带来了新的希望，而且vimplus也支持macos和linux众多发行版，让linux发烧友频繁切换发行版而不用操心vim环境配置。最后说了这么多，不如看[vimplus安装脚本][78]来的直接:smile:。

- **`启动vim报错：RequestsDependencyWarning: Old version of cryptography ([1, 2, 3]) may cause slowdown.`**

    可以尝试将cryptography删掉，具体见[issues #208][81]。

- **`vimplus不支持目前用户正在使用的系统怎么办？`**

    可以给作者提[Issues][39]，或者自己fork vimplus来修改，并提交pr，贡献自己的一份力量。

- **`安装vimplus后Airline等插件有乱码，怎么解决？`**

    linux和mac系统需设置终端字体为`Droid Sans Mono Nerd Font`。

- **`xshell连接远程主机不能使用vim-devicons或乱码。`**

    windows系统安装[Nerd Font][51]字体后并更改xshell字体即可。

- **`ubuntu18.04安装了nerd font但通过终端属性并没有看到该字体。`**

    可以试试dconf-editor软件来设置，可以参考[这里][76]。

- **`使用第三方库时怎么让ycm补全第三方库API？`**

    vimplus安装完毕之后，`~`目录下将会生成两个隐藏文件分别是.vimrc和.ycm_extra_conf.py，其中.vimrc是vim的配置文件，.ycm_extra_conf.py是ycm插件的配置文件，当你需要创建一个project时，需要将.ycm_extra_conf.py拷贝到project的顶层目录，通过修改该配置文件里面的`flags`变量来添加你的第三方库路径。

- **`使用vi命令报错：E492: Not an editor command:`**

    vimplus安装完成后，linux下可能会同时存在vi和vim命令，执行vi时，vi加载~/.vimrc文件可能会报错，但不影响使用，如果要消除错误可以设置软链接`ln -s /usr/bin/vim /usr/bin/vi`

- **`怎么自定义文件头，比如说添加作者、创建时间？`**

    你可以修改[chxuan/prepare-code][67]插件来达到目的，可以参考[这里][77]。

- **`安装vimplus在“[ 95%] Building CXX object ycm/CMakeFiles/ycm_core.dir/ycm_core.cpp.o”等进度时出现编译报错`**

    编译ycm需要消耗较大内存，建议内存大于1G，实在不行也可以开启linux swap分区。

- **`以上没有我遇到的问题怎么办？`**

    您可以通过上网找解决方法，或提[Issues][39]，也可以通过加QQ`787280310`、发邮件方式`787280310@qq.com`一起讨论解决方法。

- **`vimplus用起来真的太棒了，怎么办？`**

    那就麻烦您打赏一颗:star::star:吧，给予我继续维护的动力。


## 贡献者

> 有代码贡献或有好的建议，帮助vimplus发展的小伙伴

 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 


## 支持开源:heart:

> 有意愿献爱心的小伙伴，务必将github账号写入捐款备注哦，谢谢大家

| wechat                                                                                                     | alipay                                                                                                       |
| ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
|     |     |

| 序号  | 支持者             | RMB   | 时间       |
| ----- | -------            | ----- | -----      |
| 1     | [zhoumengkang][80] | ¥50   | 2019-09-28 |
| 2     | [zhoumengkang][80] | ¥50   | 2019-09-29 |
| 3     | [zibraque][85]     | ¥50   | 2019-11-25 |
| 4     | [gfreewind][86]    | ¥20   | 2019-12-27 |


## vimplus:star:趋势图

[![Sparkline](https://stars.medv.io/chxuan/vimplus.svg)](https://stars.medv.io/chxuan/vimplus)


## License

This software is licensed under the [MIT license][75]. © 2016 chxuan


  [1]: https://raw.githubusercontent.com/chxuan/vimplus/master/screenshots/vimplus-logo.png
  [2]: https://raw.githubusercontent.com/chxuan/vimplus/master/screenshots/main.png
  [3]: https://brew.sh/
  [4]: https://github.com/junegunn/vim-plug
  [5]: https://github.com/Valloric/YouCompleteMe
  [6]: https://github.com/scrooloose/nerdtree
  [8]: https://github.com/vim-airline/vim-airline
  [9]: https://github.com/powerline/powerline
  [10]: https://github.com/jiangmiao/auto-pairs
  [12]: https://github.com/ctrlpvim/ctrlp.vim
  [13]: https://github.com/majutsushi/tagbar
  [14]: https://github.com/vim-scripts/taglist.vim
  [15]: https://github.com/ryanoasis/vim-devicons
  [16]: https://github.com/tpope/vim-surround
  [17]: https://github.com/tpope/vim-commentary
  [18]: https://github.com/tpope/vim-repeat
  [19]: https://github.com/tpope/vim-endwise
  [20]: https://github.com/godlygeek/tabular
  [23]: https://github.com/easymotion/vim-easymotion
  [24]: https://github.com/haya14busa/incsearch.vim
  [25]: https://github.com/mhinz/vim-startify
  [27]: https://github.com/chxuan/change-colorscheme
  [36]: https://github.com/tpope/vim-fugitive
  [38]: https://github.com/Valloric/YouCompleteMe
  [39]: https://github.com/chxuan/vimplus/issues
  [50]: https://github.com/junegunn/vim-slash
  [51]: https://github.com/ryanoasis/nerd-fonts
  [52]: https://github.com/tiagofumo/vim-nerdtree-syntax-highlight
  [53]: https://github.com/Xuyuanp/nerdtree-git-plugin
  [54]: https://github.com/VundleVim/Vundle.vim
  [56]: https://github.com/Yggdroot/LeaderF
  [57]: https://github.com/Shougo/echodoc.vim
  [58]: https://github.com/chxuan/cpp-mode
  [59]: https://github.com/chxuan/vimplus/blob/master/help.md
  [60]: https://github.com/terryma/vim-smooth-scroll
  [62]: https://github.com/mileszs/ack.vim
  [64]: https://github.com/junegunn/gv.vim
  [66]: https://github.com/chxuan/vimplus-startify
  [67]: https://github.com/chxuan/prepare-code
  [68]: https://github.com/rhysd/clever-f.vim
  [70]: https://github.com/chxuan/vim-buffer
  [72]: https://github.com/chxuan/vim-edit
  [74]: https://github.com/chxuan/tagbar
  [75]: https://github.com/chxuan/vimplus/blob/master/LICENSE
  [76]: https://blog.csdn.net/wang73ying/article/details/82491993
  [77]: https://blog.csdn.net/liuyangbo121/article/details/82971736
  [78]: https://github.com/chxuan/vimplus/blob/master/install.sh
  [79]: https://hub.docker.com/r/chxuan/ubuntu-vimplus
  [80]: https://github.com/zhoumengkang
  [81]: https://github.com/chxuan/vimplus/issues/208
  [82]: https://github.com/chxuan/vimplus/blob/master/.vimrc
  [83]: https://github.com/chxuan/vimplus/blob/master/.vimrc.custom.plugins
  [84]: https://github.com/chxuan/vimplus/blob/master/.vimrc.custom.config
  [85]: https://github.com/zibraque
  [86]: https://github.com/gfreewind
  [87]: https://termux.com/



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)