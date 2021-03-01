finance：Stata与金融 
========================================================
[![](https://img.shields.io/badge/My-Stata-brightgreen.svg?style=plastic)](http://www.czxa.top) [![](https://img.shields.io/badge/github-Stata-orange.svg?style=plastic)](http://www.czxa.top) [![](https://img.shields.io/badge/platform-Mac_OS|Windows_OS-orange.svg?style=plastic)](http://www.czxa.top) [![](https://img.shields.io/badge/Fork-0-orange.svg?style=social)](http://www.czxa.top)

这个程序包里面包含了一些金融数据获取、绘图的Stata命令。

## 安装

### 安装方法一：

```py
net install finance, from("http://www.czxa.top/finance")
```

### 安装方法二(推荐)：

* 首先你需要安装github命令，这个命令是用来安装github上的命令的：

```py
net install github, from("https://haghish.github.io/github/")
```

* 然后就可以安装这个命令了：

```py
github install czxa/finance, replace
```

### 安装方法三：

* 另外你也可以从这里把ado文件和sthlp文件下载下来，然后放在你的Stata系统文件夹里，查看系统文件夹的路径可以运行下面的命令：

```js
sysdir
```

* 放在那个文件夹里都可以，推荐放在plus文件夹里。


## 使用
### bitcoin -- 自动获取比特币价格数据和波动率指数并绘制一幅JavaScript图表
```stata
bitcoin
```
![](http://www.czxa.top/finance/img/czxa_2018-09-17_21.56.33.png)

### cnstock2 -- 爬取沪市、深市或两市所有上市公司基本情况数据
这个命令需要两个shell命令支持，具体阅读我的这篇博客：[彻底解决Stata无法读取过宽文件的问题&cnstock2命令获取上市公司基本情况信息](http://www.czxa.top/posts/43828/)。Mac用户可以直接使用。Windows用户需要安装curl和[sed](http://batch-cn.qiniudn.com/tool/sed.exe)才能使用。
```stata
/* 下载两市所有上市公司的基本情况数据： */
cnstock2
/* 下载沪市所有上市公司的基本情况数据： */
cnstock2, m(SH)
/* 下载深市所有上市公司的基本情况数据： */
cnstock2, m(SZ)
```
![](http://www.czxa.top/finance/img/czxa_2018-09-17_22.01.25.png)

### cntrade2 -- 从网易财经获取股票交易数据
这个命令是对李春涛的cntrade的修改，主要是通过修改变量的名称使之更方便使用。
#### 语法
```stata
cntrade2 codelist, [s:tart(string) e:nd(string) s:tock i:ndex]
```
+ codelist 一列股票代码，使用空格分割。
+ 对于每一个股票代码会输出一个Stata数据集文件；
+ 输出的数据集中包含了该股票的交易数据； 输出数据集的名字是上市公司的股票代码；
+ 中国上市公司的股票代码为六位数字，这不同与纽约证券交易所。 例如:
    000001 平安银行
    000002 万科
    600000 浦发银行
    600005 武钢股份
+ 开头的0是可以被省略的。

#### 选项
+ start(string):数据起始日期；
+ end(string):数据截止日期；
+ stock:指定代码为股票代码，这是默认的；
+ index:指定代码为股票指数代码。

#### 示例
```stata
cntrade2 1, start(20180101) end(20180701)
cntrade2 1, start(20180101) end(20180701) index
```
![](http://www.czxa.top/finance/img/czxa_2018-09-17_22.04.21.png)

###  copen -- 在Stata中打开指定文件、网页或文件夹
 注意：Windows系统下只能打开文件。 
```stata
copen www.baidu.com
copen temp.txt
```

### ctbc2 -- 从中国债券信息网获取2002年以来的各个期限的中债国债到期收益率数据
```stata
ctbc2
```
![](http://www.czxa.top/finance/img/czxa_2018-09-17_22.07.14.png)

### exrate -- 从第一黄金网获取财经时间序列数据
这个命令的详细介绍可以参考这篇文章：[exrate——从第一黄金网获取财经数据](http://www.czxa.top/posts/40913/)。这个命令大概可以获取400个观测值，可以用于获取汇率、黄金、指数等数据。
```stata
exrate USDCNY
```
![](http://www.czxa.top/finance/img/czxa_2018-09-17_22.08.28.png)

### exrate2 -- 从和讯网获取汇率时间序列数据
这个比起上面的那个有所进步，可以获取过去一千个观测值。
由于exrate命令获取数据的能力有限，所以我又写了这个exrate2命令。
一些可以获得的汇率列表可以在这个网页上找到：http://quote.hexun.com/forex/default.aspx
```stata
exrate2 USDCNY
```
![](http://www.czxa.top/finance/img/czxa_2018-09-17_22.13.06.png)

### fxrate -- 在Stata中查询人民币的汇率
```stata
fxrate
```
![](http://www.czxa.top/finance/img/czxa_2018-09-17_22.15.02.png)

###  ipanel -- Tradeconomics数据接口，提供30+种各国数据的下载
#### 语法
```stata
ipanel arg [, c:ontinent(string)]
```

#### 描述
+ 该命令将会自动爬取指定的数据变量。
+ arg: 指定下载的数据变量。

#### 选项
continent(string): 指定下载哪个大洲的国家，如果不指定则为全世界。可选洲为：europe/america/asia/africa/australia/g20(G20国家)

#### 示例
```stata
ipanel interest-rate
ipanel interest-rate, c(g20)
```
![](http://www.czxa.top/finance/img/czxa_2018-09-17_22.19.22.png)

#### 可选变量

含义|arg
:---:|:---:
利率|interest-rate
通货膨胀率|inflation-rate
失业率|unemployment-rate
政府债务占国内生产总值比重|government-debt-to-gdp
就业率|employment-rate
劳动力参与率|labor-force-participation-rate
长期失业率|long-term-unemployment-rate
青少年失业率|youth-unemployment-rate
核心通胀率|core-inflation-rate
食品通胀|food-inflation
通货膨胀率|inflation-rate
生产者价格指数变化率|producer-prices-change
存款准备金率|cash-reserve-ratio
存款利率|deposit-interest-rate
银行间同业拆借利率|interbank-rate
利率|interest-rate
贷款利率|lending-rate
贷款增长率|loan-growth
GDP年增长率|gdp-annual-growth-rate
GDP增长率|gdp-growth-rate
政府支出占国内生产总值|government-spending-to-gdp
政府债务占国内生产总值比重|government-debt-to-gdp
政府预算|government-budget
自置居所比率|home-ownership-rate
员工社会保障覆盖率|social-security-rate-for-employees
企业所得税税率|corporate-tax-rate
个人所得税税率|personal-income-tax-rate
销售税率|sales-tax-rate
社会保障覆盖率|social-security-rate
企业社会保障覆盖率|social-security-rate-for-companies
零售销售（月率环比)|retail-sales-mom
零售销售（年率同比)|retail-sales-yoy
个人消费|personal-spending
银行贷款利率|bank-lending-rate
工业生产|industrial-production
工业生产（月）|industrial-production-mom
矿业生产|mining-production

###  irate -- 从中国债券信息网获取数据绘制中债国债到期收益率曲线图
 注意：暂不适用WindowsOS！ 
```stata
irate
```
![](http://www.czxa.top/finance/img/irate.png)

### kline2 -- 调用ECharts绘制蜡烛图
#### 语法
```stata
kline2 code, [start(string) end(string) stock index scheme(string)]
```
+ code 股票代码
+ 中国上市公司的股票代码为六位数字，这不同与纽约证券交易所。 例如:
    000001 平安银行
    000002 万科
    600000 浦发银行
    600005 武钢股份
+ 开头的0是可以被省略的。

#### 选项

    start(string):数据起始日期；
    end(string):数据截止日期；
    stock:指定代码为股票代码，这是默认的；
    index:指定代码为股票指数代码；
    scheme(string):
        控制绘图的主题，有dark/roma/vintage/macarons/infographic/shine六种可选，默认vintage主题。

#### 示例
```stata
kline2 1, start(20180101) end(20180701)
kline2 1, start(20180101) end(20180701) index
```
![](http://www.czxa.top/finance/img/czxa_2018-09-17_22.23.55.png)

### numdate2string -- 将数值型日期转变成字符串型日期
#### 语法
```stata
numdate2string [, split(string)]
```
#### 示例
```stata
clear
set obs 10
gen date = 10000 + _n
format date %tdCY-N-D
numdate2string date, split(/)
. list

     +-----------+
     |      date |
     |-----------|
  1. | 1987/5/20 |
  2. | 1987/5/21 |
  3. | 1987/5/22 |
  4. | 1987/5/23 |
  5. | 1987/5/24 |
     |-----------|
  6. | 1987/5/25 |
  7. | 1987/5/26 |
  8. | 1987/5/27 |
  9. | 1987/5/28 |
 10. | 1987/5/29 |
     +-----------+
```

### numdate2timestamp -- 把日期时间变量转换成毫秒记的时间戳

#### 语法
```stata
numdate2timestamp [, gen:erate(newvarname)]
```

#### 示例
```stata
clear
set obs 10
gen date = 10000 + _n
format date %tdCY-N-D
numdate2timestamp date, gen(timestamp)
. list

     +---------------------------+
     |       date      timestamp |
     |---------------------------|
  1. | 1987-05-20   548467212288 |
  2. | 1987-05-21   548553588736 |
  3. | 1987-05-22   548639997952 |
  4. | 1987-05-23   548726407168 |
  5. | 1987-05-24   548812816384 |
     |---------------------------|
  6. | 1987-05-25   548899192832 |
  7. | 1987-05-26   548985602048 |
  8. | 1987-05-27   549072011264 |
  9. | 1987-05-28   549158387712 |
 10. | 1987-05-29   549244796928 |
     +---------------------------+
```

## pzrate -- 在Stata中查询中国重要利率
这就是著名的裴政利率！
该命令将会自动输出一个包含人民币重要利率的表格。
```stata
pzrate
```
![](http://www.czxa.top/finance/img/czxa_2018-09-17_22.36.24.png)

## stkd -- 根据输入的股票代码查询股票的详细信息
### 用法：
#### 基本语法：

**stkd** codelist, **[path**(*string*) **store** **iterm**(*string*) **fmt**(*string*) **cite]**

**codelist**: 是一列你想要查询详细信息的股票代码列表。如果不足六位，该命令会自动在代码前面加0补齐至六位。

#### 选项

**path**(*string*): 指定保存文件的路径，默认为当前工作目录。

**store**: 选择是否要储存股票信息文件，默认不保存。

**fmt**(*string*): 选择要储存股票信息文件的格式，默认为txt格式，指定该选项时会自动保存。

**cite**: 如果你需要引用该命令，加上该选项可以显示引用格式。

**iterm**(*string*): 选择要直接显示出来的股票信息，默认会显示股票的名称。有一下选择，很容易发现，这些都是对应股票信息的拼音缩写：

* 可选选选项主要分为基础信息、工商信息、经营范围、证券信息、联系方式以及公司简介六类，使用这六个词的拼音缩写就会显示该类别的所有信息，另外可以使用_all选项显示所有的信息。

- `_all`: 全部信息
- jcxx: 【基础信息】
    - gpdm: 股票代码
    - gsqc: 公司全称
    - gsywmc: 公司英文名称
    - cym: 曾用名
    - clrq: 成立日期
    - sshy: 所属行业
    - ssgn: 所属概念
    - ssdy: 所属地域
    - fddbr: 法定代表人
    - dlds: 独立董事
    - zxfwjg: 咨询服务机构
    - kjssws: 会计师事务所
    - zqswdb: 证券事务代表
- jyfw: 【经营范围】
    - jyfw: 经营范围
- zqxx: 【证券信息】
    - ssrq: 上市日期
    - ssjys: 上市交易所
    - zqlx: 证券类型
    - ltgb: 流通股本
    - zgb: 总股本
    - zcxs: 主承销商
    - fxj: 发行价
    - sssrkpj: 上市首日开盘价
    - sssrzdf: 上市首日涨跌幅
    - sssrhsl: 上市首日换手率
    - tbclhts: 特别处理和退市
    - fxsyl: 发行市盈率
    - zxsyl: 最新市盈率
- lxfs: 【联系方式】
    - lxdhdm: 联系电话（董秘）
    - gscz: 公司传真
    - dzyx: 电子邮箱
    - gswz: 公司网站
    -  lxr: 联系人
    - yzbm: 公司邮编
- gsjj: 【公司简介】
    - gsjj: 公司简介

### 返回值

在运行完stkd后运行下面的命令可以查看返回值。

```stata
return list
```
上面所列的每一条信息都储存在返回值里。可以使用r()进行调用。

### 示例

```stata
stkd 1
stkd 2, i(jyfw)
stkd 4, s
stkd 5, path(~/Desktop) s
stkd 6, fmt(dta)
stkd 7, c
```
![](http://www.czxa.top/finance/img/czxa_2018-09-17_22.40.18.png)

### stkpv2 -- 绘制股价棒状图
#### 语法
```stata
stkpv2 code, [start(string) end(string) stock index]
```

+ code 股票代码
+ 中国上市公司的股票代码为六位数字，这不同与纽约证券交易所。 例如:
    000001 平安银行
    000002 万科
    600000 浦发银行
    600005 武钢股份
+ 开头的0是可以被省略的。

#### 选项

+ start(string):数据起始日期；
+ end(string):数据截止日期；
+ stock:指定代码为股票代码，这是默认的；
+ index:指定代码为股票指数代码；

#### 示例
```stata
stkpv2 1, start(20180101) end(20180701)
stkpv2 1, start(20180101) end(20180701) index
```
![](http://www.czxa.top/finance/img/stkpv2.png)

### stkpv3 -- 绘制股价蜡烛图
#### 语法
```stata
stkpv3 code, [start(string) end(string) stock index]
```
+ code 股票代码
+ 中国上市公司的股票代码为六位数字，这不同与纽约证券交易所。 例如:
   000001 平安银行
   000002 万科
   600000 浦发银行
   600005 武钢股份
+ 开头的0是可以被省略的。

#### 选项

+ start(string):数据起始日期；
+ end(string):数据截止日期；
+ stock:指定代码为股票代码，这是默认的；
+ index:指定代码为股票指数代码；

#### 示例
```stata
stkpv3 1, start(20180101) end(20180701)
stkpv3 1, start(20180101) end(20180701) index
```
![](http://www.czxa.top/finance/img/stkpv3.png)

### stkpv4 -- 绘制股价蜡烛图+移动平均线
#### 语法
```stata
stkpv4 code, [s:tart(string) e:nd(string) s:tock i:ndex a:dd(string)]
```
+ code 股票代码
+ 中国上市公司的股票代码为六位数字，这不同与纽约证券交易所。 例如:
    000001 平安银行
    000002 万科
    600000 浦发银行
    600005 武钢股份
+ 开头的0是可以被省略的。

+ 选项

    add(string):添加移动平均线；
    start(string):数据起始日期；
    end(string):数据截止日期；
    stock:指定代码为股票代码，这是默认的；
    index:指定代码为股票指数代码。

### 示例
```stata
stkpv4 1, start(20180101) end(20180701)
stkpv4 1, start(20180101) end(20180701) index
stkpv4 1, start(20180101) end(20180701) index add(5 15 30 90)
```
![](http://www.czxa.top/finance/img/stkpv4.png)

###  utrans -- UTF-8转码
这个可以非常方便的进行文件转码。
例如：
```stata
utrans temp.dta
utrans temp.txt
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)