# budo-warehouse

基于Binlog等技术的数据同步工具

## 功能特性

1. 数据入口支持 Binlog MQ/Kafka 接口调用(Dubbo/HTTP)

2. 数据出口支持 JDBC(ES/Solr/Mongo/CVS文件/Hive/HBase) MQ/Kafka 接口调用(Dubbo/HTTP) 邮件(发送变更告警)

3. 支持所有入口出口的动态搭配，级联串联

4. 支持根据表和类型筛选部分变更事件

5. 支持异结构同步（同步时增减改列,或变更列的值）

## 核心配置
```
// 数据端点(入口或出口)
class DataNode {
    // jdbc:mysql://127.0.0.1 
    // async:activemq://127.0.0.1:61616
    private String url;

    private String username;

    private String password;
}

// 传输通道
class Pipeline {
    // 动态筛选事件(SPEL表达式) 
    // #{eventType == 'UPDATE' and tableName.startsWith('backup_')}
    private String eventFilter;

    // 数据入口
    private Integer sourceDataNodeId;

    private String sourceSchema;

    private String sourceTable;

    // 数据出口
    private Integer targetDataNodeId;

    private String targetSchema;

    // #{'backup_' + sourceTable}
    private String targetTable;

    // 是否保留原始数据结构
    private Boolean originalFields;
}

// 配置数据结构对应关系
class FieldMapping {
    // 关联通道
    private Integer pipelineId;

    // 目标列名
    private String fieldName;

    // 目标列的值的表达式(SPEL) 
    // #{id}
    // #{name + age + school} 
    // #{T(org.budo.support.lang.util.UuidUtil).randomUuid()} 
    // #{T(com.alibaba.fastjson.JSON).toJSONString($row)} 
    // #{T(org.budo.time.Time).now().toTimestamp()}
    private String fieldValue;
}
```


## 参考资料

通过Interface收发MQ消息 [budo-dubbo-protocol-async](https://gitee.com/budogroup/budo-common/tree/master/budo-dubbo-protocol-async)

[budo-csv-jdbc-driver](https://gitee.com/budogroup/budo-common/tree/master/budo-csv-jdbc-driver)

[budo-elasticsearch-jdbc-driver](https://gitee.com/budogroup/budo-common/tree/master/budo-elasticsearch-jdbc-driver)

[budo-hbase-jdbc-driver](https://gitee.com/budogroup/budo-common/tree/master/budo-hbase-jdbc-driver)

[budo-solr-jdbc-driver](https://gitee.com/budogroup/budo-common/tree/master/budo-solr-jdbc-driver)

[budo-mongo-jdbc-driver](https://gitee.com/budogroup/budo-common/tree/master/budo-mongo-jdbc-driver)

[https://github.com/alibaba/otter/wiki/Otter双向回环控制](https://github.com/alibaba/otter/wiki/Otter双向回环控制)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)