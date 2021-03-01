#bodsite
#项目模块：
	1、公共模块：日志、分布式锁、读写分离、搜索、自定义异常、对Bean操作、验证、配置等等公共类。
	2、支付服务模块：对业务服务提供支付宝支付、微信支付。
	3、搜索服务模块：对业务服务提供通用搜索服务（基于Solr）。
	4、业务相关服务模块：暂无业务，定义了接口相关返通用回Json，全局异常处理等等。
#采用技术：
	1、Dubbo:采用Dubbo实现SOA架构，各个模块服务化、对内外提供服务。
	2、Zookeeper:采用Zookeeper作为注册中心，管理Dubbo配置、分布式锁。
    3、Thrift：RPC远程调用（bodsite-rpc-thrift）。
	4、Solr:搜索引擎服务使用SolrCloud实现。
	5、Redis:远程缓存,实现分布式锁。
	6、Jenkins:采用Jenkins提供自动化持续部署。
	7、Spring
	8、Mybatis
	9、dangdang shard-jdbc:实现分表分库，读写分离（bodsite-rpc-thrift-service）。
	10、ehcache:本地缓存（与redis缓存组成二级缓存）。

#后期模块添加：
	1、消息服务中心
	2、分布式存储服务中心
	3、会员中心
#后期技术添加：
	1、Mycat相关
	2、Nginx相关
	3、Mongodb相关
#近期
已有Zookeeper集群、ActiveMq集群、SolrCloud集群实现
近期将添加该项目分布式锁实现、搜索代码实现、Jenkins+Docker自动化构建相关文章。
博客地址：https://my.oschina.net/u/1416405/blog

项目导入说明：https://my.oschina.net/u/1416405/blog/821859


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)