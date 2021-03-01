项目主页:http://git.oschina.net/lemonzone2010/doc-render

最近公司需要生成PDF,基于这个需求简单学习了下IText 和 flying saucer,对于这两个技术.我先简单介绍下:

Flying Saucer和iText介绍:

   A.  iText是一个生成PDF文档的开源java库，能够动态从XML或者数据库生成PDF，同时它具备PDF文档的绝大多数属性(比如加密……)，支持java，C#等。官网:http://www.itextpdf.com/

   B.  Flying Saucer(或者叫xhtmlrender project on java.net)是一个基于iText的开源java库，能够轻松的将html(带css2.1)生成pdf。 网站:http://code.google.com/p/flying-saucer/

基于这个两个技术,大致就有了以下思路方便的生成pdf:

编写HTML模板--->通过Flying Saucer和IText--->生成pdf

于是这里需要用到一个java模板工具freemarker

   C. FreeMarker是一个模版引擎，一个基于文本的模板输出工具（生成任意的HTML表单代码）。官网:http://freemarker.org/

范例说明:

项目主页:http://git.oschina.net/lemonzone2010/doc-render

1.支持中文

    a.目录doc-render/src/test/resources/config/fonts中如果没有字体,需要手动复制系统中字体文件ARIALUNI.TTF到目录

    b.window系统字体路径:C:/Windows/Fonts/ARIALUNI.TTF

    c. html模板文档css字体设置:   font-family: Arial Unicode MS;

2.能够加载图片,设置的默认图片路径 classpath:config/images/

3.关于中文不能正确换行问题需要替换jar

    a. 原有flying-saucer-core-9.0.3.jar,flying-saucer-pdf-itext5-9.0.3.jar 对于中文内容不能正确换行

    b.将上一条中两个jar包替换(已经将原jar包源码修改重新生成)如下:

          b1.  flying-saucer-core-9.0.3.jar             ---> doc-render/lib/flying-saucer-core-9.0.3-RC1.jar

          b2.  flying-saucer-pdf-itext5-9.0.3.jar    ---> doc-render/lib/flying-saucer-pdf-itext5-9.0.3-RC1.jar

4.运行Junit测试类 TestPdfGenerator.testGenerate() 即可生成pdf,pdf生成路径见日志(doc-render/tmp/).

5.由于生成pdf需要加载中文字体文件(一般字体文件>10M),本例中增加了资源池(最大资源数15),相关详细见ITextRendererObjectFactory.getObjectPool();经过简单测试能够支持:150个用户迭代10次

6.  模板html:点击查看:http://git.oschina.net/lemonzone2010/doc-render/blob/master/doc-render/src/test/resources/config/templates/overseaAssistance.html

7.  pdf生成文件点击查看:http://git.oschina.net/lemonzone2010/doc-render/raw/master/doc-render/tmp/1385449366836.pdf

8.基于maven构建,如果没有maven,需要手动下载以下依赖包:

commons-pool-1.5.1.jar

flying-saucer-core-9.0.3.jar           --需要替换 doc-render/lib/flying-saucer-core-9.0.3-RC1.jar

flying-saucer-pdf-itext5-9.0.3.jar     --需要替换  doc-render/lib/flying-saucer-pdf-itext5-9.0.3-RC1.jar

freemarker-2.3.20.jar

hamcrest-core-1.3.jar

itextpdf-5.3.0.jar

jackson-core-asl-1.9.2.jar

jackson-mapper-asl-1.9.2.jar

junit-4.11.jar

log4j-1.2.17.jar

slf4j-api-1.7.5.jar

6.  模板html:点击查看 overseaAssistance.html 

7.  pdf生成文件点击查看 

项目主页:http://git.oschina.net/lemonzone2010/doc-render

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)