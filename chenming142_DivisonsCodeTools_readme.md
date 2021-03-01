#DivisonsCodeTools
根据国家统计局网址 http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm

进行统计的统计用区划和城乡划分代码

1 程序使用了HtmlAgilityPack 和 Newtonsoft.Json 

2 统计到第四级: 省-市-区-县/街道,其实程序,也已经取到了第五级居委,一般用的少,就没加. 有需要的朋友,可以自己加.

3 爬下来的数据,转换为json 并保存.

4 原理很简单,网页抓取-- 解析-- 取数据 -- 再根据数据--再抓取.

5 没有啥特别的技术.发布这个源码,也是为了给自己,或者有这方面需要的朋友提供一个方便.



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)