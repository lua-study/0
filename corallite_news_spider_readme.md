
##README
爬取到的新闻数据：
![Image text](https://gitee.com/mobilesec110/news_spider/raw/master/pic/1.png)

欢迎广大爱好者私聊-共同合作开发运营，可以加楼主QQ：7727-57-263 也可以加QQ群交流 704802627
-------------------------------

- 当前的`settings.py`经过调试相对比较稳定，不要轻易修改！！！
- 当前，所有爬虫**增量**抓取的开关已经打开，如果需要，可以手动关闭，`/spiders/***.py`文件的`FLAG_INTERRUPT = True`常量

- 证券日报 2007.09.17~ http://zqrb.ccstock.cn/ `scrapy crawl zqrb`
- 证券时报 2010.12.17~ http://epaper.stcn.com/paper/zqsb/html/2010-12/17/node_2.htm `scrapy crawl zqsb`
- 证券日报网
  http://www.ccstock.cn/finance/hongguanjingji/index.html
  http://www.ccstock.cn/finance/hangyedongtai/index.html
  http://www.ccstock.cn/gscy/gongsi/index.html
  http://www.ccstock.cn/gscy/qiyexinxi/index.html
  `scrapy crawl zqrbw`
- 南华早报
  http://www.nanzao.com/sc/business/more-business-news
  http://www.nanzao.com/sc/national/more-national-news
  'scrapy crawl nhzb'
- 中国经营网
  http://www.cb.com.cn/deep/
  http://www.cb.com.cn/economy/
  http://www.cb.com.cn/companies/
  'scrapy crawl zgjyw'



- 经济观察报
http://www.eeo.com.cn/politics/bjxx/
http://www.eeo.com.cn/politics/shengyin/
http://www.eeo.com.cn/politics/shuju/
http://www.eeo.com.cn/nation/shiju/
http://www.eeo.com.cn/comment/commentsygc/commentsygccjsd/
http://www.eeo.com.cn/comment/commentsygc/commentsygczcxj/
http://www.eeo.com.cn/comment/commentsygc/commentsygccyzs/
'scrapy crawl jjgcb'
- 财经网
http://economy.caijing.com.cn/economynews/
http://economy.caijing.com.cn/observation/
http://economy.caijing.com.cn/economics/
http://economy.caijing.com.cn/region/
http://economy.caijing.com.cn/policy/
http://economy.caijing.com.cn/report/
http://industry.caijing.com.cn/industrianews/
http://industry.caijing.com.cn/steel/index.html
http://industry.caijing.com.cn/energy/
http://industry.caijing.com.cn/aviations/
http://industry.caijing.com.cn/traffic/
http://industry.caijing.com.cn/food/
http://industry.caijing.com.cn/medicals/
http://industry.caijing.com.cn/consumption/
http://industry.caijing.com.cn/industrys/
‘scrapy crawl cjw’
- 证券时报网
http://news.stcn.com/xwyw/
‘scrapy crawl zqsbw’
- 中证网
http://www.cs.com.cn/xwzx/hg/
http://www.cs.com.cn/xwzx/cj/ 
http://www.cs.com.cn/ssgs/gsxw/
三个分类必须分开运行
‘scrapy crawl zzw’
- 华尔街见闻
http://wallstreetcn.com/news?status=published&type=news&cid=17&order=-created_at&limit=100&page=1
http://wallstreetcn.com/news?status=published&type=news&cid=22&order=-created_at&limit=100&page=1
`scrapy crawl hejjw`
深圳新闻网
http://www.sznews.com/news/node_141128.htm
http://www.sznews.com/news/node_150507.htm
http://www.sznews.com/news/node_237320.htm
http://www.sznews.com/news/node_109926.htm


##参与贡献
Fork 本仓库
- 新建 Feat_xxx 分支
- 提交代码    
- 新建 Pull Request
##码云特技
- 使用 Readme_XXX.md 来支持不同的语言，例如 Readme_en.md, Readme_zh.md
- 码云官方博客 blog.gitee.com
- 你可以 https://gitee.com/explore 这个地址来了解码云上的优秀开源项目
- GVP 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
- 码云官方提供的使用手册 https://gitee.com/help
- 码云封面人物是一档用来展示码云会员风采的栏目 https://gitee.com/gitee-stars/

## 打赏
如果你觉得对你有用，打赏下作者吧：
![Image text](https://gitee.com/mobilesec110/xiaoyouhui/raw/master/imagePic/5.png)
![Image text](https://gitee.com/mobilesec110/xiaoyouhui/raw/master/imagePic/6.png)
![Image text](https://gitee.com/mobilesec110/xiaoyouhui/raw/master/imagePic/7.png)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)