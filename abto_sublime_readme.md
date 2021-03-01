# Sublime Text 3
Sublime text拓展插件整理，间断更新补全中...

## 安装Sublime Text 2插件的方法：

### 1. 直接安装
安装Sublime text 2插件很方便，可以直接下载安装包解压缩到Packages目录（菜单-\>preferences-\>packages）。

### 2. 使用Package Control组件安装
也可以安装package control组件，然后直接在线安装：
 	 
* 按 Ctrl+调出 `console`       
* 粘贴以下代码到底部命令行并回车：    
  import urllib2,os;pf='Package Control.sublime-package';
ipp=sublime.installed_packages_path();os.makedirs(ipp) if not os.path.exists(ipp) else None;
open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read())  
* 重启Sublime Text。               
* 如果在Perferences-\>package settings中看到package control这一项，则安装成功。  

如果这种方法不能安装成功，可以到这里[下载文件手动安装](http://wbond.net/sublime_packages/package_control/installation)。
  
### 用Package Control安装插件的方法（未有梯子用户慎用）：

1. 按下`Ctrl+Shift+P`调出命令面板	
2. 输入install 调出 Install Package 选项并回车，然后在列表中选中要安装的插件。


## 拓展插件：
### 1. Emmet（原名：Zen Coding）
> [github官方](https://github.com/emmetio/emmet)

Zen Coding估计大家都不会陌生，前不久改名为Emmet了，你只需按约定的缩写形式书写而不用写整个代码，然后按“扩展”键，这些缩写就会自动扩展为对应的代码内容。 比如，你只需要输入 `((h4>a[rel=external])+p>img[width=500 height=320])*12 `，然后它会被扩展转换成12个列表项和紧随其后的图像。然后你就可以在此基础上再填写内容，就这么简单。虽然用Emmet编辑html很快，但是要用好用快它需要付出不小的学习成本，以下文献可以作为参考。

* [Zen Coding: A Speedy Way To Write HTML/CSS Code](http://www.smashingmagazine.com/2009/11/21/zen-coding-a-new-way-to-write-html-code/)
* [使用Emmet加速Web前端开发](http://www.w3cplus.com/tools/using-emmet-speed-front-end-web-development.html)
* [Emmet 插件使用教程（转载）](http://www.yunxiu.org/blog/article/5490.htm)

![
](http://static.oschina.net/uploads/img/201402/05081902_YBUL.gif)

### 2. SublimeEnhancements
> [github官方](https://github.com/titoBouzout/SideBarEnhancements)

这个插件可以给SublimeText的边栏菜单带来扩充的功能，包括：在当前工程文件夹中新建文件，移动文件或文件夹，产生文件或文件夹的副本，在新窗口或浏览器中打开，刷新等。这只是概括地说，安装后探索它更多的功能吧。

![image](http://static.oschina.net/uploads/img/201402/05081904_CJ8r.gif)

安装此插件，点击工具栏的preferences > package setting > side bar > Key Building-User，键入以下代码，这里设置按Ctrl+Shift+C复制文件路径，按F1~F5分别在firefox，chrome，IE，safari，opera浏览器预览效果，当然你也可以自己定义喜欢的快捷键，最后注意代码中的浏览器路径要以自己电脑里的文件路径为准。
  [
    { "keys": ["ctrl+shift+c"], "command": "copy_path" },
    //firefox
    { "keys": ["f1"], "command": "side_bar_files_open_with",
             "args": {
                "paths": [],
                "application": "C:\\software\\Browser\\Mozilla Firefox\\firefox.exe",
                "extensions":".*" //匹配任何文件类型
            }
    },
    //chrome
    { "keys": ["f2"], "command": "side_bar_files_open_with",
            "args": {
                "paths": [],
                "application": "C:\\Users\\Mr.DenGo\\AppData\\Local\\Google\\Chrome\\Application\\chrome.exe",
                "extensions":".*"
            }
     },
    //ie
     { "keys": ["f3"], "command": "side_bar_files_open_with",
             "args": {
                "paths": [],
                "application": "C:\\Program Files\\Internet Explorer\\iexplore.exe",
                "extensions":".*"
            }
    },
    //safari
    { "keys": ["f4"], "command": "side_bar_files_open_with",
            "args": {
                "paths": [],
                "application": "C:\\software\\Browser\\Safari\\safari.exe",
                "extensions":".*"
            }
     },
     //opera
     { "keys": ["f5"], "command": "side_bar_files_open_with",
             "args": {
                "paths": [],
                "application": "C:\\software\\Browser\\opera\\opera.exe",
                "extensions":".*"
            }
    }
]
  
### 3. FileDiffs

这个插件允许你看到SublimeText中两个不同文件的差异。你可以比较的对象可以是从剪贴板中复制的数据，或工程中的文件，当前打开的文件等。

![image](http://static.oschina.net/uploads/img/201402/05081912_1if7.gif)

### 4. AutoFileName
> [github官方](https://github.com/BoundInCode/AutoFileName)

自动补全文件路径-非常方便。

![image](http://ww1.sinaimg.cn/large/7cc829d3gw1elzufip4n6j20m809hdgz.jpg)

### 5. CSS Format
> [github官方](https://github.com/mutian/Sublime-CSS-Format)

CSS代码风格格式化

每个人写CSS都有不同的风格，有些人喜欢写成一行，有些人喜欢写成多行，各有各的好处，我倒喜欢将CSS写成一行，这样能减少CSS文件大小，且屏幕能显示更多的Class方便查找。如果阅读别人的代码不符合自己的习惯，可以用CSS Compact Expand这个插件将CSS格式化一下，按 Ctrl+Alt+[ 收缩CSS代码为一行显示，按 Ctrl+Alt+] 展开CSS代码为多行显示;

### 6. ConvertToUTF8
> [github官方](https://github.com/seanliang/ConvertToUTF8)

最新版的Sublime Text 2/3可识别UTF-8格式的中文，不识别GBK和ANSI，因此打开很多含中文的文档都会出现乱码。可以通过安装插件ConvertToUTF8,来识别GBK和ANSI。

### 7. Modific
> [github官方](https://github.com/gornostal/Modific)

Modific配合GitGutter这些插件可以高亮相对于上次提交有所变动的行，换句话说是实时的diff工具。
![image](http://www.itjavaer.com/wp-content/uploads/2015/05/7cc829d3gw1elzuf87j9yj20m80dqabr.jpg)

### 8. Goto-CSS-Declaration
> [github官方](https://github.com/rmaksim/Sublime-Text-2-Goto-CSS-Declaration)

跳转到css文件该class的声明处，注意对应的css文件要同时打开才行

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)