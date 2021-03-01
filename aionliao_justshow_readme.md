# 关于JustShow

一个基于node命令行工具构建的纯静态博客系统。

A pure html blog system based on node cli.

## Install

> npm install justshow -g

> show &lt;command&gt;

## Command

### -v

显示当前程序版本号。

### init &lt;name&gt;

在当前目录下初始化一个网站，name仅作为网站目录名称，因此name只能包含字母数字和下划线。

### start

先用cd定位到网站目录下，然后使用show start启动网站，用于本地预览。

可以在后面使用-p参数，自定义服务端口号，例如：

```
show start -p 8823
```

如果要结束，直接使用Ctrl+C终止该命令的运行。

### build

生成网站所有静态html文件（除404页面）。生成好的文件位于网站目录下的builds文件夹中。

### location

如果node的当前工作目录为一个网站，则将显示当前网站的完整路径。

### listsite

列出本机上所有通过init命令创建的网站及其位置。

### unlink [name]

彻底删除一个网站，删除之后不可恢复。

## Custom

网站模板文件位于网站的template目录下，可以通过直接修改模板文件来自定义网站样式。

### index.html

首页。

### list.html

列表页和分类列表页。

### article.html

文章页。

### single.html

单页。

### 404.html

404错误页，仅用于本地预览。

## data

模板使用[ejs](https://github.com/mde/ejs)渲染，因此您可以在模板中使用以下数据。例如：

```html
 
 
```

### data.blog

config.json中blog部分的内容，如网站标题、关键字、描述等。

### data.cate

所有的分类信息，即cates.json中保存的内容。

### data.page

根据页码获取到的列表页信息。

- total: 总页数
- index: 当前页码
- list: 列表数据
- prev: 上一页的链接
- next: 下一页的链接

### data.article

根据文章别名获取文章内容。

### data.single

根据单页别名获取单页内容。

## resource

与模板有关的css、js和图片文件都放在template目录下的resource文件夹中，这个位置是固定的，不能更改。否则，在访问生成的静态html文件时，会导致这些文件的路径不正确。

## uploads

文章中使用的附件，需要放到builds\uploads目录下，否则无法正确获取。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)