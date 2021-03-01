#MQ2 - 基于PG的物化队列 -- anthony chen

* 场景 -- 交易系统当中的异步[生产者消费者模型]数据处理,数据以jsonb的形式进行交换
* 实现 -- 队列的数据保存在磁盘，属于可靠性队列，支持事务,入列出列都可以被审计。依赖PG行锁实现互斥，条件索引进行性能提升。
* 性能 -- 以10为批次处理， 出列速度可以轻松超10000/s,入列速度基本和表的插入速度完全一致
* 特点 -- 宏哥出品. 在可靠的消费者/生产者模型当中，可以替代目前任何的队列实现，更简单，无BUG之忧.并且非常灵活.
* 可靠 -- 宏哥已经大规模部署这个模块. 
* 简单 -- 只支持PG9.4以及以上版本，只支持jsonb数据类型
* 荣耀 -- 180行代码包括注释， 可以在物化队列这个场景碾压任何open source MQ.
* 自由 -- 既然开源， 请随意使用。不提供技术支持

#使用

* 创建队列  select mq_create_queue('【QUEUE NAME】');
* 删除队列  select mq_drop_queue('【QUEUE NAME】');

* 数据入列  select mq_send('【QUEUE NAME】','【JSON STRING】',【 **OPTIONAL** MSG TYPE ID:bigint】);
* 数据出列  select mq_recv('【QUEUE NAME】', 【 **OPTIONAL** NUMBER OF MSG:big int】,【 **OPTIONAL** MSG TYPE ID:bigint】）
      number of msg 可以指定一次性出列的数据数量,默认1, 
      msg type id 可以指定 只取type id 相同的数据， 不设定则取队列中任何type. 
* 数据出列  select mq_recv('【QUEUE NAME】', '【MSG TYPE ID RESULT SET】',【 **OPTIONAL** MSG TYPE ID:bigint】） 
     RESULT SET可以指定Raw SQL用于限定出列数据的类型范围
     number of msg 可以指定一次性出列的数据数量,默认1


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)