# htmlp

## 概述
Html 页面内容中属性的自动解析工具，自动提取文章标题、正文、作者、发布时间、来源、原始来源

## 使用
```
// 提取正文
String txt = HtmLP.getContent(html).getTxt(); // 正文不带标签
String content = HtmLP.getContent(html).getContent(); // 正文带标签
// 提取标题
String title = HtmLP.getTitle(html, metaTitle);
// 提取作者
String author = HtmLP.getAuthor(txt);
// 提取时间
String time = HtmLP.getTime(html);
```

## 原理

### 正文提取
基于行块统计的正文提取，认为：当页面中内容过滤掉 html 标签后，剩余的内容逐行统计字数，指定行数后的数量当大于阈值时，则认为是正文的开始，当再次小于指定阈值时，认为正文已结束

### 标题提取
取正文中与 title 标签内容最相似的内容为标题

### 属性提取（作者、时间、来源）
基于正则的数据提取，同时来源认为有两种，一种是设定当前网站为文章来源，一种是当前网站会转发来自其它媒体的文章，此时其它媒体则做为一种来源，根据实际需求自行选择提取方法

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)