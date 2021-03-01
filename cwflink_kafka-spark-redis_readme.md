# mybigdata

[![Build Status](https://travis-ci.org/supermy/kafka-spark-redis.svg?branch=master)](https://github.com/supermy/kafka-spark-redis)

## 简介 
*  大数据实时流的计算框架，kafka+spark+redis
*  确保 spark所使用的scala版本与你系统scala的版本一致



## 特点
* 实时计算
* 窗口框架计算
* Spark 调用Redis采用单例+pipeline ，性能比普通模式提升10倍


## 适用场景

时间片段数量统计
时间片段筛选


## 优势：

* kafka 大数据量传输优势
* spark 时间窗的灵活计算
* redis 基于内存的定制计算

## 劣势：

 Redis 最大存储量的限制


## 快速试用
    1.  需要 jdk8环境；
    2.  配置 kafka 环境；
    3.  运行示例1
    4.  运行示例2



## kafka 环境配置 

### 安装
```aidl
    brew install kafka redis 
```

### 配置及性能测试
```
1.先启动zookeeper服务，端口确保2181.

2.kafka-server-start.sh /usr/local/etc//kafka/server.properties

3.创建一个主题
    创建，
        kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test 
    获取，
        kafka-topics.sh --list --zookeeper localhost:2181

4.发送一些消息: 在控制台输入消息
    kafka-console-producer.sh --broker-list localhost:9092 --topic test 

5.启动一个消费者：观察在数据台显示消息
    kafka-console-consumer.sh --zookeeper localhost:2181 --topic test --from-beginning


Topic的分区和复制
1. 创建debugo01，这个topic分区数为3，复制为1（不复制）。该topic跨越全部broker。下面管理命令在任意kafka节点上执行即可
    kafka-topics.sh --create --zookeeper debugo01,debugo02,debugo03 --replication-factor 1 --partitions 3 --topic debugo01
    kafka-topics.sh --create --zookeeper localhost --replication-factor 1 --partitions 3 --topic debugo01

2. 创建debugo02，这个topic分区数为1，复制为3（每个主机都有一份）。该topic跨越全部broker。下面管理命令在任意kafka节点上执行即可
    需要三台主机
    kafka-topics.sh --create --zookeeper debugo01,debugo02,debugo03 --replication-factor 3 --partitions 1 --topic debugo02
    
3. 列出topic信息
    kafka-topics.sh --list --zookeeper localhost:2181
    
4. 列出topic描述信息
    kafka-topics.sh --describe --zookeeper localhost:2181 --topic debugo01
    
5. 检查log目录，对于topic debugo01，debugo01为0号分区，debugo02为1号分区。而topic debugo02则复制了3份，都为0号分区
    
6. 下面topic debugo03，replication-factor为2，partition为3.那么broker id为1的debugo01会如下面describe所示，保存0号分区和1号分区。
    而0号分区的repica leader为broker id = 3，包含3和1两个replicas。
        kafka-topics.sh --create --zookeeper debugo01,debugo02,debugo03 --replication-factor 2 --partitions 3 --topic debugo03
    
    kafka-topics.sh --describe --zookeeper localhost:2181 --topic debugo03
    ll /var/kafka/debugo03*
    
    消息的产生和消费
    kafka-console-producer.sh --broker-list debugo01:9092 --topic debugo03
    kafka-console-consumer.sh --zookeeper debugo01:2181 --from-beginning --topic debugo03
    

7.性能测试
    4线程
    生产数据：50w/12sec 4w/sec
    消费数据：150/27sec 5w/sec
    下面使用perf命令来测试几个topic的性能，需要先下载kafka-perf_2.10-0.8.1.1.jar，并拷贝到kafka/libs下面。
    50W条消息，每条1000字节，batch大小1000，topic为debugo01，4个线程（message size设置太大需要调整相关参数，否则容易OOM）。只用了13秒完成，kafka在多分区支持下吞吐量是非常给力的。
    
        kafka-producer-perf-test.sh --messages 500000 --message-size 1000  --batch-size 1000 --topics debugo01 --threads 4 --broker-list debugo01:9092,debugo02:9092,debugo03:9092
    
    同样的参数测试debugo02, 由于但分区加复制（replicas-factor=3），用时39秒。所以，适当加大partition数量和broker相关线程数量会极大的提高性能。
        kafka-producer-perf-test.sh --messages 500000 --message-size 1000  --batch-size 1000 --topics debugo02 --threads 4 --broker-list debugo01:9092,debugo02:9092,debugo03:9092
    
    同样的参数测试debugo03，用时30秒。
        kafka-producer-perf-test.sh --messages 500000 --message-size 1000  --batch-size 1000 --topics debugo03 --threads 4 --broker-list debugo01:9092,debugo02:9092,debugo03:9092    
    
        kafka-consumer-perf-test.sh --zookeeper debugo01,debugo02,debugo03 --messages 500000 --topic debugo01 --threads 3
        kafka-consumer-perf-test.sh --zookeeper debugo01,debugo02,debugo03 --messages 500000 --topic debugo02 --threads 3
        kafka-consumer-perf-test.sh --zookeeper debugo01,debugo02,debugo03 --messages 500000 --topic debugo03 --threads 3
    
    单机测试
        kafka-producer-perf-test.sh --messages 500000 --message-size 1000  --batch-size 1000 --topics debugo01 --threads 4 --broker-list localhost:9092
        kafka-consumer-perf-test.sh --zookeeper localhost --messages 500000 --topic debugo01 --threads 3


```

## 编译运行

```aidl
    mvn scala:compile
    
```
## 使用

### 示例1：生产数据，KafkaWordCountProducer 消费数据，KafkaWordCount

```aidl
        spark-streaming-kafka 包：支持向 kafka 传送数据
            //topic 与 随机数 构造消息
            val message = new ProducerRecord[String, String](topic, null, str)
            //发送消息到 kafka
            producer.send(message)
        
        

        运行时编辑configuration,
        (1)KafkaWordCountProducer
        选择KafkaWordCount.scala中的KafkaWordCountProducer方法
        VM options 设置为:-Dspark.master=local
        设置程序输入参数,Program arguments: localhost:9092 test 3 5
        
```

```aidl
        从 zookeeper 获取地址消费数据，此方式已被废弃
        val lines = KafkaUtils.createStream(ssc, zkQuorum, group, topicpMap).map(_._2) //创建流并且获取数据

```

### 示例2：生产数据，KafkaEventProducer$ 消费数据，UserClickCountAnalytics$
```aidl
    生产数据
          val producer = new Producer[String, String](kafkaConfig)
          producer.send(new KeyedMessage[String, String](topic, event.toString))

    消费数据，目前采用的方式快速且好用资源较少
          val kafkaStream = KafkaUtils.createDirectStream[String, String, StringDecoder, StringDecoder](ssc, kafkaParams, topics)

```

### 示例3：打包提交版本到生产环境

```aidl
    1. source /etc/profile  
    2.   
    3. grapher=`ps -ef | grep spark |grep SparkStreaming.jar | awk '{print $2}'`  
    4. echo $grapher  
    5.   
    6. kill -9 $grapher  
    7.   
    8. nohup /opt/modules/spark/bin/spark-submit \  
    9. --master spark://127.0.0.1:7077 \  
    10. --driver-memory 3g \  
    11. --executor-memory 3g \  
    12. --total-executor-cores 24 \  
    13. --conf spark.ui.port=56689  \  
    14. --jars /opt/bin/sparkJars/kafka_2.10-0.8.2.1.jar,/opt/bin/sparkJars/spark-streaming-kafka_2.10-1.4.1.jar,/opt/bin/sparkJars/metrics-core-2.2.0.jar,/opt/bin/sparkJars/mysql-connector-java-5.1.26-bin.jar,/opt/bin/sparkJars/spark-streaming-  
    15. kafka_2.10-1.4.1.jar \  
    16. --class com.hexun.streaming.StockCntSumKafkaLPcnt \  
    17. /opt/bin/UDF/SparkStreaming.jar \  
    18.  >/opt/bin/initservice/stock.log 2>&1 & \ 

```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)