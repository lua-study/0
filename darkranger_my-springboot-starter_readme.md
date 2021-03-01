# my-springboot-starter

#### 升级说明

本分支spring-boot-2.X将我个人于18年夏天基于springboot1.5以及springCloud Edgware版的自定义starter做了升级 

目前升级内容如下

1. springboot升级到2.2.4.RELEASE版本

2. springCloud升级到Hoxton.RELEASE版本

3. orika新增两种自定义枚举类转换器

4. swagger新增接口版本定义

5. elasticsearch去除5.x版本starter,新增7.x版本starter

6. elasticsearch改用spring-data-elasticsearch组件,不再支持TransportClient(鉴于elastic公司官方声明8.0版本中将完全移除TransportClient)

7. elasticsearch新增NestedObject嵌套对象搜索,最多可支持五重嵌套

8. redis新增自定义缓存过期时间设置,允许使用方在同一缓存下针对不同key值数据,使用不同的过期时间

9. redis新增key值分类,采用应用名打头方式,格式变为applicationName:cacheName:cacheValue,方便过滤查找缓存数据

10. prometheus新增Java应用自定义监控指标功能,且引入grafana UI配合实时监控指标

11. 所有模块单元测试升级到Junit5,因此部分sample模块会被移除

12. application.properties弃用,全部改用application.yml配置文件

13. 部分模块包名原先有点混乱,全部整理一遍

14. 部分sample项目中的logback-spring.xml升级为异步打印日志,且增加"启动日志中打印请求路径列表"功能

#### 未来计划

1. 全部模块涉及的工具日后都采用docker进行集群安装,因此document目录下部分文档会更新和移除

2. 增加rabbitmq-starter

3. 增加kafka-starter

4. 鉴于目前更多公司开始使用elasticsearch来做分布式搜索,不排除日后会去除mongodb-starter

5. redis可能会放弃jedis,改用springboot2.x版本缺省的lettuce

6. 增加mybatis-starter,目的去除xml配置写法.新增功能可能但不包含下列所有

| 编号   | 功能 | 
| :----:|:----:| 
| 1     | 采用FP模式编写sql语句 |
| 2     | 引入crud代码自动生成 | 
| 3     | 额外支持原有provider写法 | 
| 4     | druid,hikari等数据库连接池多选 | 
| 5     | pageHelper插件支持 | 
| 6     | 整合Mybatis-plus | 

#### 项目介绍

自研的自定义starter

有些许幼稚,有些许bug,只博君一笑尔~

不喜可喷,但希望提供建设性意见

#### 使用说明

**Prometheus(普罗米修斯)**

一套开源的监控&报警&时间序列数据库的组合,由SoundCloud公司开发。

[github地址](https://github.com/prometheus/prometheus)

[starter文档](https://gitee.com/darkranger/my-springboot-starter/blob/master/prometheus/README.md)

**Swagger**

一套RESTFUL接口文档，提供在线自动生成和功能测试2个功能。

[github地址](https://github.com/swagger-api/swagger-core)

[starter文档](https://gitee.com/darkranger/my-springboot-starter/blob/master/swagger/README.md)

**ElasticSearch**

ElasticSearch(简称ES)是一个基于Lucene的搜索服务。相当于一个分布式多用户功能的全文搜索引擎，且提供RestFul web接口。

[github地址](https://github.com/elastic/elasticsearch)

[5.x版本starter文档](https://gitee.com/darkranger/my-springboot-starter/blob/master/elasticsearch/5.x/README.md)

[6.x版本starter文档](https://gitee.com/darkranger/my-springboot-starter/blob/master/elasticsearch/6.x/README.md)

**Redis**

Redis是一个高性能的key-value数据库。目前作为分布式缓存，被企业应用的场景比较多

[github地址](https://github.com/antirez/redis)

[starter文档](https://gitee.com/darkranger/my-springboot-starter/blob/master/redis/README.md)

**MongoDB**

MongoDB一个基于分布式文件存储的数据库

[github地址](https://github.com/mongodb/mongo)

[starter文档](https://gitee.com/darkranger/my-springboot-starter/blob/master/mongodb/README.md)

**Orika**

Orika是一个Bean映射工具，底层采用javassist类库生成Bean映射的字节码

然后直接加载执行生成的字节码文件，因此速度很快

具体介绍和性能比较见下列网址：

http://tech.dianwoda.com/2017/11/04/gao-xing-neng-te-xing-feng-fu-de-beanying-she-gong-ju-orika/

(不知道什么原因,已经被删除),见https://www.jianshu.com/p/40e0e64797b9 有前述链接内容

[github地址](https://github.com/orika-mapper/orika)

[starter文档](https://gitee.com/darkranger/my-springboot-starter/blob/master/orika/README.md)

**SnowFlake(雪花算法)**

SnowFlake是twitter公司为了生成分布式ID而使用的一个算法。

产生原因:为了满足Twitter每秒上万条消息的请求，每条消息都必须被分配一个唯一的id

这些id还需一定顺序（方便客户端排序），并要求在分布式系统中，不同的机器生成的id必须不同。

[github地址](https://github.com/twitter/snowflake)

[starter文档](https://gitee.com/darkranger/my-springboot-starter/blob/master/snowflake/README.md)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)