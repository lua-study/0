# json2post

## 说明
* 实现了将唐诗300首内容的json格式数据源通过python解析后并生成符合jekyll静态网站指定格式的post贴.
* 实践了python中对json的解析(目前只用了python3自带的json库，没用第三方库).
* 实践了对诗歌post生成时候，对句号逗号语句的指定宽度约束的换行调整，详见代码[json2post](gen_post/json2post.py)


## 运行
* 从GITHUB或GITEE网站fork本项目，并拉源码到本地.
* 直接运行[json2post](gen_post/json2post.py),源码有足够多的注释.
* 代码会解析json子目录下的某个json文件(源码中配置即可),并生成大量符合jekyll框架风格的post文件到post目录下.

## 版权
* 本项目开源，您可随意fork本项目源码并用于任何合法用途，但本项目作者不承担引起引发的任何风险和损失.
* 本项目用到的json数据源大都是来源于网络和其他项目,作者在此表示感谢，如涉及版权问题，请及时联系作者处理.

## 致谢
本项目的数据和代码参考了其他开源项目及网络资料(python语法及参考),得到很多帮助，部分列举如下，再次表示感谢.
* 唐诗300首的json来源于项目[GuShiWen](https://github.com/zhouzhaoxin/GuShiWen)
* 参考了这个项目[chinese-poetry](https://github.com/chinese-poetry/chinese-poetry)

## Change Notes

* V.0.0.2(2018-01-14)
  * Feature
    * 补充解析json和生成post文件的详细注释.
    * 完善了README.MD文档，补充了说明和运行章节.
    * 增加了部分错误捕获及成功失败的统计输出.
    * 调整了LOG信息输出.
    * 删除了无用的名句小节
  * Bug
    * 修复正文小结生成的时候缺漏最后的换行符的问题.
    * 修复正文没有考虑换行导致偶发错位的问题.
    
* V.0.0.1(2018-01-13)
  * Feature
    * 实现json的唐诗300首数据源的解析及生产jekyll静态网站框架要求的post格式.

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)