#CasperMagic

CasperMagic是基于PlantomJS&CasperJS和WebMagic的一个整合。CasperJS可以很方便对动态网页进行测试，但Javascript不太容易执行数据持久化和数据分析，而一般的爬虫很难抓取动态网页的内容或对页面进行操作并爬取。CasperMagic是基于WebMagic对CasperJS的封装。

![CasperJS](http://docs.casperjs.org/en/latest/_images/casperjs-logo.png "CasperJS")
![WebMagic](https://raw.github.com/code4craft/webmagic/master/assets/logo.jpg "WebMagic")


##工作模式

和CasperJS的工作模式类似，CasperMagic同样采用分步的方式。当需要对页面进行操作时，基于一个tag的操作作为一个Action，多个Action形成一个ActionChain，按照ActionChain的顺序依次执行Action的操作，最后得到操作后的页面，使用WebMagic中抽取数据。

CasperMagic的执行环境需要安装PlantomJS和CasperJS,并将路径配置到CasperMagic。CasperMagic根据ActionChain生成相应的js脚本，然后执行脚本得到网页数据。

ActionChain的配置相当简单
```
 ActionChain  chain=new ActionChain();
 ActionNode  node=new ActionNode();
 node.setNodetype(ActionNodeType.Click).setEventElement("div.article-content p a");
 chain=ActionFactory.CreateActionChain(node).ChainEnd("click.js");
 Spider.create(this).startUrls(url).setDownloader(new JsDownload(env,chain).setEnableclick(true)).run();

```

JsDownload是CasperMagic实现的获取动态网页的下载器。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)