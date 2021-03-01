'请一定记得使用dev分支开发，本地也可以建立自己的分支'
'git clone http://git.oschina.net/harleydog/hedge -b dev'
# 研究股票量化对冲

##一、项目环境搭建

1.安装Java
  >请安装jdk1.8,官网链接(http://www.oracle.com/technetwork/java/javase/downloads/index.html) 

  >环境变量设置: 
  >`JAVA_HOME = JAVA安装目录，默认是C:\Program Files\Java\jdk1.8.0_65` 
  >`PATH = %PATH%;%JAVA_HOME%\bin;` 

2.开发工具
  >请使用Eclipse\ MyEclipse \ Intellij IDEA均可,支持正版 
  >![请参考Intellij IDEA中Java8语法的配置]
  >(http://git.oschina.net/harleydog/hedge/raw/master/attachment/idea-java8.png) 

3.Maven
  >Maven下载: (http://maven.apache.org/download.cgi#) 
  >环境变量配置 
  >`M2_HOME = Maven解压缩目录` 
  >`PATH = %PATH%;%JAVA_HOME%\bin;%M2_HOME%\bin;` 

  >另外请修改%M2_HOME%\conf\setting.xml配置文件 
  >将资源库修改为比较快的网站，推荐使用ibiblio或者oschina 
  >请参考配置（用代码直接覆盖[$MAVEN_HOME/conf/setting.xml]） 
  >(https://git.oschina.net/harleydog/hedge/blob/master/config/maven/settings.xml) 

3.nginx
  >本机开发可以考虑不安装nginx，直接用tomcat即可 
  >如打算安装nginx，请参考配置 
  >(https://git.oschina.net/harleydog/hedge/blob/master/config/nginx/nginx.conf) 

4.tomcat
  >本项目中使用tomcat作为提供后台服务的容器 
  >tomcat下载:(http://tomcat.apache.org/) 
  >本项目用到了JNDI数据源，请参考配置 
  >(https://git.oschina.net/harleydog/hedge/blob/master/config/tomcat/content.xml) 
  >(https://git.oschina.net/harleydog/hedge/blob/master/config/tomcat/content.xml) 

5.DB
   >如果开发请使用本地MySQL，DB初始化脚本请使用 
   >MySQL下载: (http://www.mysql.com/downloads/) 
   >(https://git.oschina.net/harleydog/hedge/blob/master/config/sql/database.sql) 
   >具体的数据导入 可以联系作者索要 

6.外部API参考
   >本项目中使用的一些外部API参考如下 
   >1. 盈透证券TWS API:(http://git.oschina.net/harleydog/IB_TWS_API) 
   >2.老虎证券API:(http://developers.tigerbrokers.com/docs/oauth2/) 
   >3.富途证券API:(https://www.futu5.com/faq/category/cid/366) 
   >4. DBTest,基于内存数据库的单元测试API(http://git.oschina.net/harleydog/dbtest) 
   >5. 淘宝开放平台:(http://open.taobao.com) 
   >6. 阿里大鱼短信发送接口:（http://www.alidayu.com/） 
   >7. 雪球网(抓取股票数据):(http://www.xueqiu.com) 


##二、代码说明
1. 重要的包说明 
>1.1. com.diorsunion.hedge.algo :算法实现包，量化算法和股票对冲算法都实现在此包中 
>1.2. com.diorsunion.hedge.bo.datasync :数据同步不包,完成每天抓取数据同步到本地库中的功能 
>1.3. com.diorsunion.hedge.bo.db 基于数据库CRUD的业务实现类 
>1.4. com.diorsunion.hedge.bo.net 访问外部网络接口（比如雪球网）的功能 
>1.5. com.diorsunion.hedge.bo.quota 一些量化指标的计算和实现，比如MACD,KDJ 
>1.6. com.diorsunion.hedge.bo.sms 手机短信发送功能的实现 
>1.7. com.diorsunion.hedge.bo.stockdatainit 算法启动数据初始化的功能 
>1.8. com.diorsunion.hedge.common 公共类库 
>1.9. com.diorsunion.hedge.dal.entity 数据访问实体层 
>1.10. com.diorsunion.hedge.dal.repository 数据访问操作层 
>1.11. com.diorsunion.hedge.domain 业务域对象 
>1.12. com.diorsunion.hedge.exception 异常包 
>1.13. com.diorsunion.hedge.task 定时任务调度 
>1.14. com.diorsunion.hedge.util 工具包集合 
>1.15. com.diorsunion.hedge.web web层，包括controller和interceptor 
>
>其他..

2. 重要的类说明
2.1.目前大部分的启动函数都在src/test/java中,以测试的方式来完成功能 
> 2.1.1 com.diorsunion.hedge.algo.test 算法测试包 
> 2.1.2 com.diorsunion.hedge.bo.datasync.test 数据同步测试包 
> 2.1.3 com.diorsunion.hedge.bo.db.test  业务测试包 
> 2.1.4 com.diorsunion.hedge.bo.net.test  网络接口测试包 
> 2.1.5 com.diorsunion.hedge.bo.quota.test  量化指标生成测试包 
> 2.1.6 com.diorsunion.hedge.bo.sms.test  短信息发送测试包 

2.2.重要的测试基类
> 2.2.1 com.diorsunion.hedge.base.EmbeddedBOBaseTest 内存数据库单元测试基类 
> 2.2.1 com.diorsunion.hedge.base.ExternalApiBaseTest 外部API集成测试基类 
> 2.2.1 com.diorsunion.hedge.base.NetBaseTest 网络接口集成测试基类 
> 2.2.1 com.diorsunion.hedge.base.RealDataSourceBOBaseTest 真实数据库集成测试基类 
> 2.2.1 com.diorsunion.hedge.base.RepositoryBaseTest 持久层单元测试基类 

##三、当前目标（2016-04-24）
1. 量化指标（MACD,KDK,RSI,BOLL）的计算和数据定时同步 
2. 核心算法的完善 
3. 网页的制作，包括算法运行效果等 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)