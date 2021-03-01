# HTML简介
参考文档：https://www.w3school.com.cn/html/html_jianjie.asp

## 什么是 HTML？
HTML 是用来描述网页的一种语言。
1. HTML 指的是超文本标记语言 (Hyper Text Markup Language)；
2. HTML 不是一种编程语言，而是一种标记语言 (Markup language)；
3. 标记语言是一套标记标签 (Markup tag)；
4. HTML 使用标记标签来描述网页。

## HTML 标签
HTML 标记标签通常被称为 HTML 标签 (HTML tag)；
1. HTML 标签是由尖括号包围的关键词，比如 \ ；
2. HTML 标签通常是成对出现的，比如 \  和 \ ；
3. 标签对中的第一个标签是开始标签，第二个标签是结束标签；
4. 开始和结束标签也被称为开放标签和闭合标签。

## HTML 文档 = 网页
1. HTML 文档描述网页
2. HTML 文档包含 HTML 标签和纯文本
3. HTML 文档也被称为网页
4. Web 浏览器的作用是读取 HTML 文档，并以网页的形式显示出它们。浏览器不会显示 HTML 标签，而是使用标签来解释页面的内容：

# HTML元素
HTML 文档是由 HTML 元素定义的。
## 什么是HTML元素
1. HTML 元素指的是从开始标签（Start tag）到结束标签（End tag）的所有代码；
2. 开始标签常被称为开放标签（Opening tag），结束标签常称为闭合标签（Closing tag）。
## 元素语法
1. HTML 元素以开始标签起始；
2. HTML 元素以结束标签终止；
3. 元素的内容是开始标签与结束标签之间的内容；
4. 某些 HTML 元素具有空内容（Empty content）；
5. 空元素在开始标签中进行关闭（以开始标签的结束而结束）；
6. 大多数 HTML 元素可拥有属性。
## 嵌套的 HTML 元素
大多数 HTML 元素可以嵌套（可以包含其他 HTML 元素）。
HTML 文档由嵌套的 HTML 元素构成。
```html
 

 
 This is my first paragraph. 
 

 
```
## 不要忘记结束标签
即使您忘记了使用结束标签，大多数浏览器也会正确地显示 HTML：
```html
 This is a paragraph
 This is a paragraph
```
上面的例子在大多数浏览器中都没问题，但不要依赖这种做法。忘记使用结束标签会产生不可预料的结果或错误。
注释：未来的 HTML 版本不允许省略结束标签。
## 空的 HTML 元素
1. 没有内容的 HTML 元素被称为空元素。空元素是在开始标签中关闭的；
2. \  就是没有关闭标签的空元素（\  标签定义换行）；
3. 在 XHTML、XML 以及未来版本的 HTML 中，所有元素都必须被关闭；
4. 在开始标签中添加斜杠，比如 \ ，是关闭空元素的正确方法，HTML、XHTML 和 XML 都接受这种方式；
5. 即使 \  在所有浏览器中都是有效的，但使用 \  其实是更长远的保障。
## 使用小写标签
1. HTML 标签对大小写不敏感：\  等同于 \ 。许多网站都使用大写的 HTML 标签；
2. W3School 使用的是小写标签，因为万维网联盟（W3C）在 HTML 4 中推荐使用小写，而在未来 (X)HTML 版本中强制使用小写。
### 元素示例
|  开始标签   | 元素内容  |结束标签|
|  ----  | ----  |----|
| \   | This is a paragraph |\ |
| \   | This is a link |	\ |
| \   |  |  |
# 属性
属性为 HTML 元素提供附加信息。
## HTML 属性
1. HTML 标签可以拥有属性。属性提供了有关 HTML 元素的更多的信息。
2. 属性总是以名称/值对的形式出现，比如：name="value"。
3. 属性总是在 HTML 元素的开始标签中规定。
## 使用小写属性
属性和属性值对大小写不敏感。  
不过，万维网联盟在其 HTML 4 推荐标准中推荐小写的属性/属性值。  
而新版本的 (X)HTML 要求使用小写属性。
## 始终为属性值加引号
属性值应该始终被包括在引号内。双引号是最常用的，不过使用单引号也没有问题。  
在某些个别的情况下，比如属性值本身就含有双引号，那么您必须使用单引号，例如：  
```html
name='Bill "HelloWorld" Gates'
```
## 常用HTML属性参考
|  属性   | 值 | 描述 |
|  ----  | ----  | ---- |
| class  | classname | 规定元素的类名（classname） |
| id  | id | 规定元素的唯一 id |
| style  | style_definition | 规定元素的行内样式（inline style） |
| title  | text | 规定元素的额外信息（可在工具提示中显示） |
#### 参与贡献

1.  Fork 本仓库
2.  新建 Feat_xxx 分支
3.  提交代码
4.  新建 Pull Request


#### 码云特技

1.  使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2.  码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3.  你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4.  [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5.  码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6.  码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)