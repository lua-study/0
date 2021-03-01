#![输入图片说明](https://gitee.com/uploads/images/2017/1213/211714_5aad0487_3843.png "ocquant.png")


> ###QQ交流群：452113084
>

#支持CMAKE构建项目了！！！


#《一》简介

> 1.本平台基于tushare,sina,ctp接口的实现A股，期货策略交易的平台，使用c++,python语言开发，建议使用visualStudio/2013 ，g++/5以上版本进行编译。
> 
> 2.平台可挂载自定义策略，使用实时行情/历史数据，进行行情回放，交易点模拟。
>
> 3.提供各种常用K线指标：KDJ,MACD,RSI...
>
> 4.策略的撰写交由个人完成，自由保密。
>
> 5.行情展示使用matplotlib进行渲染。
>

#《二》核心模块介绍
> 1.thosttraderapi.dll,thostmduserapi.dll是上期CTP的官方库，可自行更新。
>
> 2.StrategyPlatform.dll 是平台库，负责动态加载自定义dll，实现自有策略的平台化运行。
>
> 3.FATrade.dll,FAQuote.dll 是对CTP标准接口的二次封装。
>
> 4.FAStrategyCore.dll 是平台的指标库。
>
> 5.FAPython是基于boost.python的封装。
>
> 6.其他模块参考文件夹内md说明,发现更多惊喜。
>


#《重要开源更新历史》
>1.2016.8  项目雏形。
>
>2.2016.9  完成自定义策略平台及简易Demo测试。
>
>3.2016.10 多种Indicator加入指标核心库。
>
>4.2016.11 QuoteUI：实时行情渲染程序，基于第三方Chart控件。
>>引入双工共享内存模块FASHM作为进程间通信IPC。
>
>5.2016.11.15 将过去的CTPAndroid项目迁移到该平台下，作为行情模块的子项目"QuoteAndroid"。
>
>6.2016.12.6 Redis数据中心发布，将过去QuoteServer的基于Mysql的工程，升级到redis数据库。
>
>7.2017.2开始对跨期统计套利模型，进行规划。
>
>8.2017.3推出炒单王工具。
>
>9.2017.5推出CMAKE工具来构建项目，减少项目容积，并方便用户采用自己的vs编译环境。cmake选项时采用32位编译（如用64位，则ctp库替换x64,请自行调整）。
>>亲测：vs2008,vs2010,vs2012,vs2013,vs2017 均顺利编译通过。
>>cmake 官方下载地址：https://cmake.org/download/
>
>10.将OPEN_DATACENTER项目移植到本项目，作为一个完整个体。
>>(1) tick数据进行redis读写，主从/读写分离。
>>
>>(2) libevent服务器核心，支持大并发。
>>
>>(3) redis行情多k周期切分工具，方便导出cvs,txt等。
>
>11. **2017.8推出CrossPlatform《ctp互动交易平台》，使用cocos游戏引擎支持windows,IOS,Android的客户端；** 
>>>(1)https://git.oschina.net/openctp/open_ctp_x
>
>12. 2017.11基于开放的tushare,backTrader等，推出OC适用的python混合模块。
>>>结合历史的OPEN_STOCK工程，将A股和期货合并在OCQuant。
>FAPython模块，是基于tushare行情数据的A股回测模块；oc_strategy_1.py 是python写的策略demo。
>FAQuoteSt，DemoTushare分别是封装的A股行情下载模块和Demo,适用于c++ x64环境。
>

13.OCQuant已经全面支持linux环境编译和运行。（测试环境ubuntu-16.64.3 LTS）
>

#《特别说明》
>1,作者默认编译环境是win32；如用win64编译的；请ctp库，log4cplus，event等均自行替换win64相应库；linux不受限制；
>




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)