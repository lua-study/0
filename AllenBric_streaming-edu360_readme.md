# 大数据实战训练系列丛书--实战案例玩转Spark--StreamingETL项目

------

Ngxin日志采集到Kafka,Streming消费到hdfs。

 * 1.logstash采集
 * 2.缓冲kafka
 * 3.streaming消费，etl部分grok正则。
 * 4.存hdfs
 * 5.hive外部表指向hdfs路径，按天分区。

------

## 参考
#### 1.携程[hangout](https://github.com/childe/hangout)
#### 2.在线正则[grok](http://grokdebug.herokuapp.com/)

------

## 相关命令
#### 1.打包：sbt clean assembly
#### 2.提交：spark-submit --queue root.bigdata.streaming --class "cn.edu360.streaming.NginxLogToHive" --name "edu360streaming3" --executor-cores 1 --num-executors 20 --master yarn-cluster streaming-edu360-assembly-1.0.jar NginxLogToHive
#### 3.killjob：yarn application -kill applicationId
#### 4.查看zk中offsets信息：kafka-run-class.sh kafka.tools.ConsumerOffsetChecker --zookeeper zkhost --topic topicName --group groupId
#### 5.手动更新zk中offsets值：set /consumers/groupId/offsets/topicName/分区 值

------

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)