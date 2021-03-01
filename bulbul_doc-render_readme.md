
## 项目背景
项目主页:http://git.oschina.net/lemonzone2010/doc-render

公司需要生成PDF，会有一个固定样式格式，然后添加动态数据。于是就有了一个想法：编写模板->填充数据->生成pdf。

基于这个需求和想法调研了下，了解到FreeMarker、IText 和 flying saucer工具。


## 技术简介
### IText
iText是一个生成PDF文档的开源java库，能够动态从XML或者数据库生成PDF，同时它具备PDF文档的绝大多数属性(比如加密……)，支持java，C#等。官网:http://www.itextpdf.com/

### Flying Saucer
Flying Saucer(或者叫xhtmlrender project on java.net)是一个基于iText的开源java库，能够轻松的将html(带css2.1)生成pdf。 网站:https://github.com/flyingsaucerproject/flyingsaucer

### FreeMarker
FreeMarker是一个模版引擎，一个基于文本的模板输出工具（生成任意的HTML表单代码）。官网:http://freemarker.org/


## 主要功能

1. 支持中文

    a.目录doc-render/src/test/resources/config/fonts中自带字体ARIALUNI.TTF

    b.window系统字体路径:C:/Windows/Fonts/ARIALUNI.TTF

    c.html模板文档css字体设置: font-family: Arial Unicode MS;

1. 能够加载图片,设置的默认图片路径 classpath:config/images/

1. 运行Junit测试类 TestPdfGenerator.testGenerate() 即可生成pdf,pdf生成路径见日志(doc-render/tmp/).

1. 由于生成pdf需要加载中文字体文件(一般字体文件>10M),本例中增加了资源池(最大资源数15),相关详细见ITextRendererObjectFactory.getObjectPool();经过简单测试能够支持:150个用户迭代10次

1. 模板html:[点击查看](doc-render/src/test/resources/config/templates/overseaAssistance.html)

1. pdf生成文件[点击查看](doc-render/tmp/1549647421978.pdf)




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)