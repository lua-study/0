# Full Automatic Amazon Distributed crawler|spider (USA, Japan, Germany and UK)

[![GitHub forks](https://img.shields.io/github/forks/hunterhug/AmazonBigSpider.svg?style=social&label=Forks)](https://github.com/hunterhug/AmazonBigSpider/network)
[![GitHub stars](https://img.shields.io/github/stars/hunterhug/AmazonBigSpider.svg?style=social&label=Stars)](https://github.com/hunterhug/AmazonBigSpider/stargazers)
[![GitHub last commit](https://img.shields.io/github/last-commit/hunterhug/AmazonBigSpider.svg)](https://github.com/hunterhug/AmazonBigSpider)
[![Go Report Card](https://goreportcard.com/badge/github.com/hunterhug/AmazonBigSpider)](https://goreportcard.com/report/github.com/hunterhug/AmazonBigSpider)
[![GitHub issues](https://img.shields.io/github/issues/hunterhug/AmazonBigSpider.svg)](https://github.com/hunterhug/AmazonBigSpider/issues)

## 一. 介绍

### 1. 英语介绍

Support UAS/Japan/Germany/UK, Amazing!

Catch the best seller items in Amazon USA! Using redis to store proxy ip and the category url. First fetch items list and then collect many Asin, store in mysql. Items list catch just for the Asin, and we suggest one month or several weeks to fetch list page. We just need fetch the Asin detail page and everything we get!

We keep all Asin in one big table. And if catch detail 404, we set it as not valid. Also we can use API catch big rank but look not so good!

So, there are two ways to get the big rank：

1. catch list page(not proxy), using API get the big rank

2. catch list page(not proxy), and then get asin detail page(proxy), API can not catch all the asin big rank so must use this!

Due to we want list smallrank and the bigrank at the same time, but mysql update is so slow, we make two tables to save, one is smallrank, one is bigrank!

We test a lot,if a ip no stop and more than 500 times http get,the list page will no robot,but the detail asin page will be robot. So we bind a proxy ip with and fix useragent, and keep all cookie. But it still happen, a IP die still can fetch detail page after 26-100times get, It tell us we can still ignore robot, and catch max 100 times we will get that page. robot page is about 7KB.

However, if a lot of request, will be like that 500 error

For reason that the detail page is such large that waste a lot of disk space, we save the list page in the local file and the detail page you can decide whether to save it or not.

### 2. 中文介绍

用途： 选款，特别适合亚马逊电子商务运营公司

核心竞争力： 四个国际站点：美国/英国/日本/德国，分布式，配套后台可视化

原理： 首先通过获取亚马逊所有类目的URL，即从第一层大类，一直获取到第六层小类。通过这些类目URL可以依次抓取到这些类目某段时间的Top100的商品（类目下的爆款），这些Top100的商品排名我们称为小类排名，每个小时会变一次，但是由于变化基本不会太频繁以及抓取的商品数量很多，基本能覆盖。比如：有一个大类，下面有某一个三层类目，这个三层类目下面有几十个四层，四层下面又有五层，很多个Top100组在一起构成了三层我们需要的商品。通过这些小类商品数据，我们再进详情页获取更多的字段（评论数，星数，是否FBA，价格等），包括每件商品的最顶层排名，我们称大类排名。通过商品去重，分布式代理以及数据的一些预处理设计，加大马力，运用IT采集技术，我们能得到亚马逊大部分卖得好的商品，通过筛选，排序，我们可以从不同角度观察商品趋势。对于卖家来选款的话是极好的。

关于选款： 亚马逊和国内天猫的差别在于店铺概念弱化，亚马逊以单品为为单位，基本一个ASIN就是一个商品类型，卖得好的商品很多人可以跟卖。我没操作过亚马逊的产品发布，听运营总监说，不同的商家会有一样ASIN的商品，如果谁的商品好（省略。。怕误解他人）。步骤一般是：通过该平台Web端查看某大类排名前一万名，进行一些筛选，比如价格在20刀的，FBA的商品，然后可以再点进去商品，看这件商品十几天的排名和价格变化等，然后我决定跟卖，先去阿里巴巴批发看看有没有这个东西，有！价格利润很多。好，我们卖！然后每天可以上来平台搜我们这件商品的ASIN，查看最近的变化。

因为这套产品包括爬虫端和网站端（可视化数据，筛选导出数据，结果见result结果文件夹），并且对技能要求较高，安装并稳定运行较复杂，可见[产品概况](https://github.com/hunterhug/GoSpider/blob/master/doc/amazon.md)，彻底开源. 这是BI爬虫端, BI网站端见： [亚马逊四站BI产品网站端](https://github.com/hunterhug/AmazonBigSpiderWeb)

英文已经凌乱，Old English Read this [OutOfDateYouShouldReferChinese](old-readme.md) 仔细阅读，有益身心，老中文说明见[中文版说明](chinese.md)

亚马逊爬虫支持

1. 列表页和详情页可选择代理方式
2. 多浏览器保存cookie机制
3. 机器人检测达到阈值自动换代理
4. 检测日期过期自动停止程序
5. IP池扫描周期填充代理IP
6. 支持分布式跨平台抓取
7. 高并发进程设置抓取
8. 默认网页爬取去重
9. 日志记录功能
10. 配套可视化网站，支持多角度查看数据，小类数据，大类数据，Asin数据和类目数据，支持查看每件Asin商品的历史记录，如排名，价格，打分，reviews变化。部分数据支持导出，且网站支持RBAC权限，可分配每部分数据的查看和使用权限。
11. 网络端监控爬虫，可查看爬虫当前时段数据抓取状态，爬取的进度，IP的消耗程度。   **可支持网络端启动和停止爬虫，彻底成为Saas**（待做）
12. 可自定义填入IP，如塞入其他代理IP网站API获取的IP
13. 可选择HTML文件保存本地

分布式，高并发，跨平台，多站点，多种自定义配置，极强的容错能力是这个爬虫的特点。机器数量和IP代理足够情况下，每天每个站点可满足抓取几百万的商品数据。

以下为安装使用文档, 可以先`star`后慢慢看!

## 二. 文件目录

```
├── config  配置文件：运行前必须配置
│   ├── de_config.json    德国亚马逊爬虫远程配置（在本地新建一个空文件：远程.txt 即加载此配置）
│   ├── de_local_config.json   德国亚马逊爬虫本地配置（默认加载这个）
│   ├── de_log.json	德国亚马逊日志记录文件
│   ├── jp_config.json 
│   ├── jp_local_config.json
│   ├── jp_log.json
│   ├── uk_config.json
│   ├── uk_local_config.json
│   ├── uk_log.json
│   ├── usa_config.json
│   ├── usa_local_config.json
│   └── usa_log.json
├── doc
│   ├── categoryrecord.xlsx   你可以看看四站（ 美国/日本/英国/德国的商品类目情况）
│   ├── img
│   └── sql   你必须手动导入的四站类目SQL，很大，见tool/url
├── public
│   ├── core   核心包
│   └── log
├── result结果
│   ├── 20170731Clothing.xlsx   从网站端导出的数据
│   └── 20170731Kitchen&Dining.xlsx
├── sh       这个是脚本，我们用来快速启动爬虫的
│   ├── docker   用来快速启动docker版redis和mysql
│   ├── build.sh 在本地编译二进制，然后直接通过以下scp.sh发送到阿里云等机器
│   ├── scp.sh
│   ├── de-crontab.txt  定时器
│   ├── jp-crontab.txt
│   ├── uk-crontab.txt
│   ├── usa-crontab.txt
├── spiders   这个是爬虫入口
│   ├── de
│   ├── jp
│   ├── uk
│   └── usa
└── tool
    ├── python
    └── url   四站类目数据爬取程序在这里，需要手工改代码做类目，暂时你不需要用到
├── ip.txt   你可以将固定的代理IP放在这里，因为亚马逊详情页爬太多会反爬虫

```

## 三. 如何使用

### 1. 获取代码/安装环境

首先你必须安装MYSQL/Redis和Golang1.8(请百度)，你也可以参见[GoSpider-docker](https://github.com/hunterhug/GoSpider-docker)安装MYSQL/Redis(只需安装好docker和docker compose, 直接点击sh/docker/build.sh)

如果自己安装MYSQL，爬虫运行并发数太大时，会爆连接数，请编辑mysql配置文件（可百度）：

```
[mysqld]
max_connections = 15000
max_connect_errors = 6000
open_files_limit = 65535
table_open_cache = 1000
skip-name-resolve
```

然后获取代码(此阶段可能有防火长城，一般没问题, 有问题请手动下载, 可能库依赖下载不下来, 请逐个库下载)：

```
go get -v -u https://github.com/hunterhug/AmazonBigSpider
```

### 2. 配置爬虫

我们以美国亚马逊爬虫为例，如何启动它？首先你可以编辑`config/usa_local_config.json`(其他站点类似更改)，`###` 备注的为可选编辑，其他最好不要编辑

(以下为很久以前的配置说明，基本没变)

```
{
  "Type": "USA",     //美国站类型，有四种usa,jp,uk,de
  "Datadir": "/data/db/usa",   // 文件保存位置，可选择保存，/代表在本盘下
  "Proxymaxtrytimes": 40,     // ### 机器人错误最大次数，超过换IP
  "Rank": 80000,               // ### 只保存排名在这个数字之前的商品
  "Listtasknum": 30,        // ### 抓列表页进程数，建议不要太大，并发最多设置50
  "Asintasknum": 30,      // ### 抓详情页进程数，建议不要太大，并发最多设置50
  "Localtasknum": 150,  // 本地文件处理进程数，建议不要太大，并发最多设置50，可不管
  "Proxypool": "USAIPPOOL",   // Redis IP代理池名字
  "Proxyhashpool": "USAIPPOLLHASH",  // Redis IP已用池名字
  "Proxyloophours": 24,        // 重导IP时间（小时,Redis IP池用完）
  "Proxyasin": true,         // ### 详情页使用代理？
  "Proxycategory": false,    //列表页使用代理？
  "Proxyinit": false,   // IP池程序每次启动是否追加，可不管
  "Urlpool": "USAURLPOOL",  //列表页待抓池名字
  "Urldealpool": "USAURLDEALPOOL", //列表页处理中池
  "Urlhashpool": "USAURLHASHPOOL",  //列表页已抓池
  "Asinpool": "USAAsinPOOL",       // 同理
  "Asindealpool": "USAAsinDEALPOOL",
  "Asinhashpool": "USAAsinHASHPOOL",
  "Otherhashpool": "USAOtherHashPOOL",  // 小类数据额外redis池，方便填充大类数据，开关在ExtraFromRedis,如果关，大类数据填充查找小类数据库，大数据下会导致慢
  "Asinautopool": true,   //列表页抓取数据后自动把Asin数据塞在Asinpool,如果设置为false，需要手动运行asinpool.exe
  "ExtraFromRedis": true,  //搭配Otherhashpool
  "Asinlocalkeep": false,   //保存详情页在Datadir
  "Categorylocalkeep": false, //保存列表页在Datadir
  "Urlsql": "SELECT distinct url,id,bigpid ,name,bigpname,page FROM smart_category where isvalid=1 order by bigpid limit 100000",  //抓取那些列表页，可改
  "Asinsql": "SELECT distinct asin as id FROM `{?}` order by bigname limit 1000000", //抓取哪些Asin，{?}是程序预带占位符，被今天日期替代，可去掉
  "Spidersleeptime": 3, // 无用
  "Spidertimeout": 35,  // ### 链接抓取超时时间
  "Spiderloglevel": "DEBUG",  // ### 爬虫日志记录，可不管,建议设置为ERROR，注意！！！
  "Redisconfig": {  // ### redis配置
    "Host": "14.215.177.40:6379",  //主机
    "Password": "smart2016",   //密码
    "DB": 0
  },
  "Redispoolsize": 100,  // redis程序库连接池最大数量，应该比Listtasknum和Asintasknum都大
  "Basicdb": {   // ### 基础数据库配置
    "Ip": "14.215.177.38",
    "Port": "3306",
    "Username": "root",
    "Password": "smart2016",
    "Dbname": "smart_base"
  },
  "Hashdb": {   // ### 历史数据库配置
    "Ip": "14.215.177.38",
    "Port": "3306",
    "Username": "root",
    "Password": "smart2016",
    "Dbname": "smart_hash"
  },
  "Hashnum": 80,   //历史数据库按hashcode分表，分表数量
  "Datadb": {     // ### 日期数据库，按天分表
    "Ip": "14.215.177.38",
    "Port": "3306",
    "Username": "root",
    "Password": "smart2016",
    "Dbname": "smartdb"
  },
  "Ipuse": {   //要用的IP组
    "d": {    //端口和密码，密码可留空，组名所在的IP在下面
      "Port": "808",
      "Secret": "smart:smart2016"
    },
    "e": {
      "Port": "808",
      "Secret": "smart:smart2016"
    },
    "f": {
      "Port": "808",
      "Secret": "smart:smart2016"
    },
    "h": {
      "Port": "808",
      "Secret": "smart:smart2016"
    }
  },
  "Ips": {
    "d": [   //组名为d的IP们
      "146.148.149.203-254",   // 连续Ip,也可以不连续，如146.148.149.203
    ]
  }
}
```

我们目前的配置`只需改动数据库帐号和密码，以及Redis的密码（无密码留空）`，`其他不建议改`，只要你的数据库连接可远程，爬虫可以在不同机器并发启动，构造分布式爬虫（依靠Redis）。

```
  "Redisconfig": {
    "Host": "127.0.0.1:6379",
    "Password": "GoSpider",   ##########################请改Redis密码(无密码留空)
    "DB": 0
  },
  "Redispoolsize": 100,
  "Basicdb": {	
    "Ip": "127.0.0.1",
    "Port": "3306",
    "Username": "root",
    "Password": "459527502",	 ##########################请改密码
    "Dbname": "smart_base"
  },
  "Hashdb": {
    "Ip": "127.0.0.1",
    "Port": "3306",
    "Username": "root",
    "Password": "459527502",	 ##########################请改密码
    "Dbname": "smart_hash"
  },
  "Hashnum": 80,  ### 不要改，Hash在网站端已经写死80张表
  "Datadb": {
    "Ip": "127.0.0.1",
    "Port": "3306",
    "Username": "root",
    "Password": "459527502",	 ##########################请改密码
    "Dbname": "smartdb"
  },
  "Ipuse": {
  },
  "Ips": {
  }
}
```

### 3. 编译程序

爬虫入口在：

```
├──spiders
	├── de
	│   ├── asinmain.go
	│   ├── asinpool.go
	│   ├── initsql.go
	│   ├── ippool.go
	│   ├── listmain.go
	│   ├── listparsemain.go
	│   └── urlpool.go
	├── jp
	│   ├── asinmain.go
	│   ├── asinpool.go
	│   ├── initsql.go
	│   ├── ippool.go
	│   ├── listmain.go
	│   ├── listparsemain.go
	│   └── urlpool.go
	├── uk
	│   ├── asinmain.go
	│   ├── asinpool.go
	│   ├── initsql.go
	│   ├── ippool.go
	│   ├── listmain.go
	│   ├── listparsemain.go
	│   └── urlpool.go
	└── usa
	    ├── asinmain.go  4. 抓取详情页，补充大类排名等商品信息，打Mysql大类数据和Hash方便查看历史趋势
	    ├── asinpool.go  不用
	    ├── initsql.go  1.初始化数据库
	    ├── ippool.go   2.插代理IP到Redis并监控爬虫
	    ├── listmain.go	4.抓取类目列表Top100，打redis记录额外数据以及打Mysql小类数据
	    ├── listparsemain.go 不用
	    └── urlpool.go  3.打类目URL到redis，供4步骤使用
```

我们来编译二进制程序，如果报错，可能是Golang缺库（请go get补充安装），见`sh/build.sh`，请确保编译路径在`sh`路径下，执行以下命令编译程序:

```
./build
```

此时我们每个站点有`5个二进制文件`，我们以美国站为例子：

```
USQL	1.初始化数据库
UIP	2.插代理IP到Redis并监控爬虫
UURL	3.打类目URL到redis，供4步骤使用
ULIST	4.抓取类目列表Top100，打redis记录额外数据以及打Mysql小类数据
UASIN	4. 抓取详情页，补充大类排名等商品信息，打Mysql大类数据和Hash方便查看历史趋势
```

已经编译好Linux 64位的可执行文件, 你可以直接使用!

### 4. 初始化数据库

如果不申明，都是以美国站为例。需要填充四个站点8个数据基本数据库，以及4*80=320个HASH库，上面已经编译好二进制, 执行:

```
./USQL
或者
go run spiders/usa/initsql.go
```

之后请将`doc/sql`下的已经抓取到的类目SQL手动导入数据库，SQL文件如下

```
doc
└── sql
    ├── de_category.csv  德国的类目CSV，你可以打开看看
    ├── de_category.sql  需要导入的数据库
    ├── jp_category.csv
    ├── jp_category.sql
    ├── uk_category.csv
    ├── uk_category.sql
    ├── usa_category.csv
    └── usa_category.sql
```

导入数据库一般可以这样：

```
mysql -uroot -p

source jp_category.sql
source de_category.sql
source usa_category.sql
source uk_category.sql
```

填充这个数据是为了你可以抓取这些类目的商品，你可以开启网站端，在网站端设置抓取几页，是否抓取！

### 5. 运行程序

运行程序有步骤，先打URL到Redis，这样ULIST才可以爬到东西，ULIST爬到东西后就可以开UASIN爬了，因为UASIN需要代理IP，所以先要导UIP进去（导入之后打开浏览器：12345端口看爬虫情况）

```
UIP	2.插代理IP到Redis并监控爬虫
UURL	3.打类目URL到redis，供4步骤使用
ULIST	4.抓取类目列表Top100，打redis记录额外数据以及打Mysql小类数据
UASIN	4. 抓取详情页，补充大类排名等商品信息，打Mysql大类数据和Hash方便查看历史趋势
``` 

运行步骤是：

```
./UIP 或者后台运行 nohup ./UIP &
./UURL  只需运行一次
./ULIST 这个可以在不同机器开启，分布式
./UASIN 这个也可以分布式，抓详情页
```

小总结:

```
./USQL -core=$GOPATH/src/github.com/hunterhug/AmazonBigSpider/public/core -root=$GOPATH/src/github.com/hunterhug/AmazonBigSpider
./UIP -core=$GOPATH/src/github.com/hunterhug/AmazonBigSpider/public/core -root=$GOPATH/src/github.com/hunterhug/AmazonBigSpider
./UURL -core=$GOPATH/src/github.com/hunterhug/AmazonBigSpider/public/core -root=$GOPATH/src/github.com/hunterhug/AmazonBigSpider
./ULIST -core=$GOPATH/src/github.com/hunterhug/AmazonBigSpider/public/core -root=$GOPATH/src/github.com/hunterhug/AmazonBigSpider
./UASIN -core=$GOPATH/src/github.com/hunterhug/AmazonBigSpider/public/core -root=$GOPATH/src/github.com/hunterhug/AmazonBigSpider
```

因为我们是自动爬虫，不可能每次都是手动跑，所以我们使用定时器，并且我们编译成二进制了，所以二进制可以随便放，但要传入`-core`和`-root`指出代码位置（还有一个原因是定时器必须设置全路径）

敲入`crontab -e` ，写入以下定时器，每晚0-3点凌晨爬虫自动销毁和启动，其他站点类似，你可以参考`sh/*-crontab.txt`

```
5 0 * * * ps -ef|grep usa/U* | awk '{print $2}' |xargs -i kill {}
20 0 * * * docker exec -d GoSpider-redis redis-cli -a GoSpider flushall
10 2 * * * nohup /root/mydocker/go/src/github.com/hunterhug/AmazonBigSpider/spiders/usa/UURL -core=/root/mydocker/go/src/github.com/hunterhug/AmazonBigSpider/public/core -root=/root/mydocker/go/src/github.com/hunterhug/AmazonBigSpider > /dev/null 2>&1 &
15 2 * * * nohup /root/mydocker/go/src/github.com/hunterhug/AmazonBigSpider/spiders/usa/UIP -core=/root/mydocker/go/src/github.com/hunterhug/AmazonBigSpider/public/core -root=/root/mydocker/go/src/github.com/hunterhug/AmazonBigSpider > /dev/null 2>&1 &
20 2 * * * nohup /root/mydocker/go/src/github.com/hunterhug/AmazonBigSpider/spiders/usa/ULIST -core=/root/mydocker/go/src/github.com/hunterhug/AmazonBigSpider/public/core -root=/root/mydocker/go/src/github.com/hunterhug/AmazonBigSpider > /dev/null 2>&1 &
0 3 * * * nohup /root/mydocker/go/src/github.com/hunterhug/AmazonBigSpider/spiders/usa/UASIN -core=/root/mydocker/go/src/github.com/hunterhug/AmazonBigSpider/public/core -root=/root/mydocker/go/src/github.com/hunterhug/AmazonBigSpider > /dev/null 2>&1 &

```


### 6. 如何使用代理IP

因为亚马逊四站点对详情页会反爬虫，一个IP可以抓500页然后被封，但是现在市场上卖的代理IP特别多，几百万动态那种，所以不用担心这个问题。如果你自己有固定的代理IP，请把它写在`ip.txt`里面。

如果你没有固定代理IP，那么请去购买代理IP，国内的有(我并没有打广告哈)：

1. 快代理： [http://www.kuaidaili.com](http://www.kuaidaili.com)
2. 无忧代理： [http://www.data5u.com](http://www.data5u.com)
3. 芝麻代理：[http://www.zhimaruanjian.com](http://www.zhimaruanjian.com)
4. 米扑代理： [http://proxy.mimvp.com](http://www.zhimaruanjian.com)

如何对接不同代理IP的API呢，要写代码，是的，没错，你也可以打开浏览器，打开`http://127.0.0.1:12345`,自行手动导入IP(12346,12347,12348端口分别是日本/德国/英国亚马逊的爬虫监控)。如下图：

![12345](/doc/img/3.png)

EXPORT IP DIY，按行写入IP，然后塞，帐号和密码是:jinhan 459527502

我已经写好了一个米扑代理的接口，你可以通过打开这个URL导入：

```
curl http://127.0.0.1:12346/mi?orderid=cdddddddddd@qq.com&user=jinhan&password=459527502
```

其中`orderid=cdddddddddd@qq.com` = 后面的是你购买后给你的帐号，其他不变。我建议你还是购买其他的代理IP，毕竟这个产品如果很多人在用，会有IP冲突（某个人如果太暴力，分布式开太多，应该会），就是
IP已经被人用了，然后你再用就无效了。

### 7. 分布式部署(可选)

分布式部署时，由于数据量巨大，开启网站端时，容易卡，所以你可以对数据库进行读写分离，一般数据量 `不大` 可以不用。

可以购买腾讯云，阿里云，亚马逊云，我们一般只需买一台，花费大概是每年1500左右，然后根据上述起`docker mysql/redis`（你也可以自行安装），然后在本地编译好程序，使用`./scp.sh 189.55.55.55`将二进制文件以及配置文件，传到远程机器，跑一下测试，测试没问题，再开启定时器。`scp.sh`在`sh`文件夹中。

以下可选：

数据库读写分离步骤如下：

Master主服务器

```
1.vim /etc/my.cnf

[mysqld]
log-bin=mysql-bin
server-id=1
binlog-ignore-db=information_schema
binlog-ignore-db=beauty
binlog-ignore-db=mysql

2.service mysqld restart

3.grant all privileges on *.* to 'smart'@'%' identified by '123456';

4.flush tables with read lock;

5.show master status;

 mysql-bin.000001 |     6503 |              | information_schema,beauty,mysql |

6.unlock tables;
```

Slave阿里云从服务器

```
1.vim /etc/my.cnf
[mysqld]
server-id=2

2.stop slave ;
3.change master to master_host='192.168.2.119',master_user='smart',master_password='123456',master_log_file='mysql-bin.000001', master_log_pos=6503;
4.start slave ;
5.show slave status
```

### 8. 网站端

BI产品爬虫端的价值大，但是配套网站端，价值可以翻好多倍。你可以查看[Full Golang Automatic Amazon Distributed crawler|spider (USA, Japan, Germany and UK) | 亚马逊四站BI产品网站端 ](https://github.com/hunterhug/AmazonBigSpiderWeb)进行安装。

截图如下：

类目，你可以自行更改抓取页数，是否抓取。

![](/doc/img/ca.png)


小类数据，基本Top100商品数据。

![](/doc/img/asin.png)


大类数据，很详细，包括大类排名等，可以复杂查询条件筛选，下载。

![](/doc/img/big.png)

产品趋势，你可以看到产品十几天的排名变化，价格变化。

![](/doc/img/trend.png)

导出的EXCEL

![](/doc/img/excel.png)


# 四. 欢迎提建议（BUG等）

如果你想参与项目，我很欢迎，请发邮件或加我QQ。

# 五. 心路历程

开发这个产品从2016年10月就开始了(12月底试用期离职)，不再投入精力开发(2017年10月记录). 

核心的爬虫包也已经拆分成库了，见[Project:Marmot(Tubo) - Golang Web Spider/Crawler/Scrapy Package | 爬虫库](https://github.com/hunterhug/GoSpider)。网站端也拆分成库了[Project:Rabbit(Tuzi) - Golang Enterprise Web | 简单企业网站](https://www.github.com/hunterhug/GoWeb)

如果这个产品有帮助到你,可以抛出请我吃下辣条吗?

微信
![微信](https://raw.githubusercontent.com/hunterhug/hunterhug.github.io/master/static/jpg/wei.png)

支付宝
![支付宝](https://raw.githubusercontent.com/hunterhug/hunterhug.github.io/master/static/jpg/ali.png)

# 免责声明

关于版权，大规模使用，请提交发邮件或通过QQ告知我, 也可以不, 我还是希望告知一下...(爬虫有风险, 本人不承担由此开源项目带来的任何责任)。

PS：这篇文章[为什么我的代码进入闭源状态](http://www.yinwang.org/blog-cn/2017/04/18/close-source)希望能够撼动你的心灵。

```
	版权所有，侵权必究
	署名-非商业性使用-禁止演绎 4.0 国际
	警告： 以下的代码版权归属hunterhug，请不要传播或修改代码
	你可以在教育用途下使用该代码，但是禁止公司或个人用于商业用途(在未授权情况下不得用于盈利)
	商业授权请联系邮箱：gdccmcm14@live.com QQ:459527502

	All right reserved
	Attribution-NonCommercial-NoDerivatives 4.0 International
	Notice: The following code's copyright by hunterhug, Please do not spread and modify.
	You can use it for education only but can't make profits for any companies and individuals!
	For more information on commercial licensing please contact hunterhug.
	Ask for commercial licensing please contact Mail:gdccmcm14@live.com Or QQ:459527502

	2017.7 by hunterhug
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)