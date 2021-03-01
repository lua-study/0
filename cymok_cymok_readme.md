# 描述

完整的模板在这里呢，点击链接获取

HardCandy-Jekyll  
[https://github.com/xukimseven/HardCandy-Jekyll](https://github.com/xukimseven/HardCandy-Jekyll)

---

#### Jekyll

原汁原味的Jekyll  
[Jekyll源码](https://github.com/jekyll/jekyll)

官方网站  
[https://jekyllrb.com/](https://jekyllrb.com/)

中文网站  
[https://www.jekyll.com.cn/](https://www.jekyll.com.cn/)

---

目录结构

|文件|简介|
|:-:|:-:|
| _config.yml | 保存配置数据。很多配置选项都会直接从命令行中进行设置，但是如果你把那些配置写在这儿，你就不用非要去记住那些命令了。 |
| _drafts     | drafts是未发布的文章。这些文件的格式中都没有title.MARKUP数据。 |
| _includes   | 你可以加载这些包含部分到你的布局或者文章中以方便重用。可以用这个标签{%include file.ext%}来把文件_/includes/file.ext包含进来。 |
| _layouts    | layouts是包裹在文章外部的模板。布局可以在YAML头信息中根据不同文章进行选择。这将在下一个部分进行介绍。标签{{  content  }}可以将content插入页面中。 |
| _posts      | 这里放的就是你的文章了。文件格式很重要，必须符合：`YEAR-MONTH-DAY-TITLE.MARKUP`。The permalinks可以在文章中自己定制，但是数据和标记语言都是根据文件名来确定的。 |
| _data       | Well-formatted site data should be placed here.the jekyll engine will autoload all yaml file`members.yml`under the directory,then you can access contents of the file through`site.data.members`. |
| _site       | 一旦jekyll完成转换，就会将生成的页面放在这里（默认）。最好将这个目录放进你的`.gitignore`文件中。 |
| index.html and other HTML,MarkDown,Textile files | 如果这些文件中包含YAML头信息部分，jekyll就会自动将它们进行转换。当然，其他的如.html,.markdown,.md,或者.textile等在你的站点根目录下或者不是以上提到的目录中的文件也会被转换。 |
| Other Files/Folders | 其他一些未被提及的目录和文件如css还有images文件夹,favicon.icon等文件都将被完全拷贝到生成的site中。 |



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)