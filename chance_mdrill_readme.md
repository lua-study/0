 项目简介 
&nbsp;&nbsp;&nbsp;&nbsp;数据越来越多，传统的关系型数据库支撑不了，分布式数据仓库又非常贵。几十亿、几百亿、甚至几千亿的数据量，如何才能高效的分析？ 
mdrill是由阿里妈妈开源的一套数据的软件，针对TB级数据量，能够仅用10台机器，达到秒级响应，数据能实时导入,可以对任意的维度进行组合与过滤。 
&nbsp;&nbsp;&nbsp;&nbsp;mdrill作为数据在线分析处理软件，可以在几秒到几十秒的时间，分析百亿级别的任意组合维度的数据。 
在阿里10台机器完成每日30亿的数据存储，其中10亿为实时的数据导入，20亿为离线导入。目前集群的总存储1000多亿80~400维度的数据。

 mdrill的特性 
 1.满足大数据查询需求： adhoc每天的数据量为30亿条，随着日积月累，数据会越来越大，mdrill采用列存储，索引，分布式技术，适当的分区等满足用户对数据的实时在线分析的需求。 
 2.支持增量更新： 离线形式的mdrill数据支持按照分区方式的增量更新。 
 3.支持实时数据导入： 在仅有10台机器的情况下，支持每天10亿级别（高峰每小时2亿）的实时导入。 
 4.响应时间快： 列存储、倒排索引、高效的数据压缩、内存计算，各种缓存、分区、分布式处理等等这些技术，使得mdrill可以仅在几秒到几十秒的时间分析百亿级别的数据。 
 5.低成本： 目前在阿里adhoc仅仅使用10台48G内存的PC机，但确存储了超过千亿规模的数据。 
 6.全文检索模式： 在mdrill的全文检索模式数据可以直接存储在hdfs中，并且以每天160亿*70维度的数据增量提供全文检索服务（注：该模式下不能进行统计，只能进行关键词匹配查询数据明细） 


  发行日志 
 2013.07.24 version 0.18-beta  初始化版本   
 2013.08.07 version 0.18.1-beta bug fix  see detail    
 2013.08.17 version 0.18.2-beta speed up  see detail   ( 下载 )  
 2013.09.01 version 0.19-alpha HA by replication  see detail   (此版本需要一定时间的测试与调整，慎用)  
 2013.09.26 version 0.19.1-beta Bug Fix  see detail   ( 下载 )  
 2013.09.29 version 0.19.2-beta Bug Fix ( 下载 )  
 2013.10.09 version 0.19.3-beta speed up (此版本有严重BUG,请勿使用, 下载 )  
 2013.10.13 version 0.19.4-beta mergerServer优化&&bugfix (推荐版本, 下载 ,依赖的zeromq从 这里下载 )  
 2013.11.19 version 0.20.1-alpha 使用hdfs进行检索&&实时append  see detail (alpha版本，慎用。  源码下载 )  
 2013.12.03 version 0.20.2-alpha 全文检索模式优化  see detail (alpha版本，慎用。  源码下载 )  
 2013.12.05 version 0.20.3-alpha bugfix (alpha版本，慎用。  源码下载 )  
 2014.01.02 version 0.20.4-alpha 通过editlog来保证实时数据的可靠性  see detail (alpha版本，慎用。  源码下载 )  
 2014.01.14 version 0.20.5-alpha bug fix ( 下载 )  
 2014.01.26 version 0.20.6-alpha bug fix ( 下载 )  
 2014.02.08 version 0.20.7-alpha cache改进  see detail   ( 点击这里下载  。)  
 2014.02.18 version 0.20.8.3-alpha bugfix&&重写调度&&优化  see detail   ( 推荐版本 。  点击这里下载  。依赖的zeromq从 这里下载 )  

 
  版本源码路径 
 https://github.com/alibaba/mdrill/tree/master/release   


 资源列表 
 
  mdrill介绍  
  mdrill介绍PPT  
  安装部署  
  sql使用手册  
  版本开发计划  
  阿里妈妈-AdHoc-基于mdrill的大数据自助分析平台  



  LICENSE  
 

 mdrill Core contributors 
 
  母延年(子落) 、 秦剑(含光) 、 郑博文(士远) 、陈鹏(伯时)、木晗、逸客、张壮、凌凝 
 
 jstorm Core contributors  点击进入  
 
  封仲淹(纪君祥) 、 李鑫(丙吉) 、 母延年(子落) 、 周鑫(陈均)  



 


 其他 
 
  FAQ  
 mdrill技术交流群:171465049 
 微博： http://weibo.com/mynyannian  

 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)