

## 完整分库分表流程demo

### 一、技术

   a. 选用[sharding-jdbc](https://shardingsphere.apache.org/document/current/cn/quick-start/sharding-jdbc-quick-start/)做项目主要分库分表技术, sharding-proxy做运维辅助技术     
   b. 选用[uid-generator](https://github.com/baidu/uid-generator)做唯一id生成器     
   c. 选用[datax](https://github.com/alibaba/DataX)做单表数据迁移到分库分表同步工具, 需要[整合datax和sharding-jdbc](transform-history/transform-datax-config/sharding-jdbc/README.md)      
   
   


### 二、 模拟订单表分库分表迁移流程
   1) 确认分库分表键       
     a. 可以统计查询订单表的where条件， 选用命中率高的， 减轻主要查询压力        
     b. 需要考虑分布式事务       
        t_order表和t_order_item表, 保存一次订单，确保分库后order和order_item都放在同一个库中，这样就可以使用本地事务了       
        一般选用user_id, 选用order_id也可以， 本demo使用user_id      
       ```
       注意事项，选用了user_id做分片键，则原先使用order_id查询的接口会遍历各个分库查询数据
          a. 本demo将user_id和order_id映射关系保存到t_order_mapping表中， 使用order_id查询时先查询一次user_id，然后带上user_id查询订单
          b. 如果数据量不是特别大，可以不处理
          c. 基因id 处理， 参考美团订单分库分表实现， 定制order_id, 中间嵌入user_id后几位数字，  分片查询时根据user_id基因数字路由， 这种改造工程比较大
          d. 多列分库分表， 在将user_id做一次分库分表的同时，也将order_id做一次分库分表， 存了两份数据， 存储较大
       ```   
       
   2) 分片算法      
     a.range    
        按时间或id范围划分，如[1-10000]放到1库， [10001-20000]放到2库
        优点：单表大小可控，天然水平扩展。
        缺点：无法解决集中写入瓶颈的问题。       
     b. hash        
        hash取模 2^n      
        分2（库) * 4 (表), 即分2个库，每个库4张表     
        则  路由规则是 库号= user_id % 2, 表号= (user_id/2) % 4       
        优点: 易扩展，解决集中写入瓶颈的问题         
        缺点: 扩容麻烦，需要重新hash,(注意避免在同一张表的数据，重新hash到不同的表), 需要迁移数据       
        本demo采用该方法      
        
   3) 确定容量，考虑扩容     
     生产中一次性分够,够用好几年，不用考虑扩容， 32（库) * 32 (表) , 分成32个库， 每个库 32张表, 共 1024张表  或者  16 (库) * 64（表) 共 1024 张表，      
     初始逻辑分库，实际上可以部署4台机器，每台机器 8 库 ， 每个库 32 表     
     当表数据超过单机限制后， 可以部署8台机器， 每台机器4各库， 每个库 32表， 最多可以部署1024台机器，每台机器1张表     
     扩容时，仅仅是改一下配置，迁移数据就可以了, 原来在同一张表的数据，扩容之后，还在同一张表      
     路由规则是 库号= user_id % 32, 表号= (user_id/32) % 32      
     本demo 分 2 (库) * 4 (表)      
     更具体的介绍看[美团实现](https://tech.meituan.com/2016/11/18/dianping-order-db-sharding.html)
     
   4) 唯一id      
     a. uuid 字符串，占用空间较多， 不能做到递增     
     b. 雪花算法        
        可以做到递增，性能较好     
        维护workId比较麻烦        
        存在时间回拨问题  
        一般都是基于雪花算法进行改造      
     c. [美团leaf唯一id实现](https://tech.meituan.com/2019/03/07/open-source-project-leaf.html)              
        比较复杂，暂不考虑
     d. [百度uid-generator](https://github.com/baidu/uid-generator)       
        比较简单，解决workId维护问题，解决了时间回拨问题，workId暂未提供重用实现        
        [本人已实现复用workId](./uid-generator/src/main/java/com/baidu/fsg/uid/worker/MarkWorkerIdAssignerWrapper.java)         
        
        [ecp-uid](https://gitee.com/zmds/ecp-uid)整合了美团leaf、百度UidGenerator、原生snowflake 实现，可以参考，      
        由于直接使用uid-generator足够简单，且有效使用，暂不采用ecp-uid  
        
   5) 单库表 迁移 到分库        
     参考美团双写实现         
     a. 原系统中将需要订单表的关联查询(join)去掉，改成在应用中用代码处理join, 为后续分库分表做准备           
     b. 改造系统中订单id的实现，统一使用uid-generator生成的唯一id       
     c. 数据库双写，先写单库，后写分库， 事务以单库为主， 读数据以单库为主      
        同时，使用datax同步历史订单数据到分库   
        校验单库和分库数据，补偿数据到分库(插入或根据更新时间比较更新)        
     d. c步骤数据补平后，  数据仍双写，先写分库，后写单库， 事务以分库为主， 读数据以分库为主          
       (如果服务众多，可以切一小部分服务灰度尝试读写， 如果有问题，可以回退到c)        
       校验单库和分库数据，补偿数据到单库(插入或根据更新时间比较更新)     
     e. 观察几天没问题后，下线单库订单表        
       
   6) 分库分表中间件       
     a. mycat 基于代理实现，存在单点问题     
     b. [shardingsphere](https://shardingsphere.apache.org/document/current/cn/overview/)        
       目前成为apache顶级项目, 从前景上说，采用该技术应是最好的              
       sharding-jdbc, jdbc代理， 不存在单点问题， 可能会存在多份配置， 升级比较麻烦，需要统一升级，只能应用于java语言     
       sharding-proxy, 数据库代理， 存在单点问题，兼容性问题， 优点是没有语言限制       
       目前demo采用sharding-jdbc实现为主，sharding-proxy运维为辅     
     
     
     
          
   
   
### 本demo使用流程

#### 1. 创建单库
  ```
  create database db_lab;
  ```
#### 2. 运行数据初始[数据库脚本](single-datasource-lab/src/main/script)
    db_lab_table.sql 用于创建数据表
    db_lab_data.sql 用于创建测试数据，里面有3万订单(t_order)数据，和9万订单项(t_order_item)数据
    

#### 3. 创建2个分库
  ```
  create database db_lab_orders_0;
  create database db_lab_orders_1;
  ```  
  
#### 4. 创建uid-generator数据库
   ```
   create database uid;
   ```  
   创建uid数据表
   ```
   DROP TABLE IF EXISTS WORKER_NODE;
   CREATE TABLE WORKER_NODE
   (
   ID BIGINT NOT NULL AUTO_INCREMENT COMMENT 'auto increment id',
   HOST_NAME VARCHAR(64) NOT NULL COMMENT 'host name',
   PORT VARCHAR(64) NOT NULL COMMENT 'port',
   TYPE INT NOT NULL COMMENT 'node type: ACTUAL or CONTAINER',
   LAUNCH_DATE DATE NOT NULL COMMENT 'launch date',
   MODIFIED TIMESTAMP NOT NULL COMMENT 'modified time',
   CREATED TIMESTAMP NOT NULL COMMENT 'created time',
   PRIMARY KEY(ID)
   )
    COMMENT='DB WorkerID Assigner for UID Generator',ENGINE = INNODB;
   ```
   
   修改uid[数据库配置](./uid-generator/src/main/resources/application-uid.properties)用户名密码
  
#### 5. 修改对应数据库配置，用户名密码等
   [sharding-config中的分库配置application-sharding.yml和config-sharding.yaml](./sharding-config/src/main/resources)     
   [single-datasource-lab单库配置](./single-datasource-lab/src/main/resources/application.properties)     
   [transform-validate单库配置](./transform-validate/validate-common/src/main/resources/application-default-datasource.properties)
     
  
####  6. 搭建sharding-proxy后, 复制[proxy配置](./sharding-config/src/main/resources/config-proxy), 启动运行 
      
使用shrding-proxy创建分库分表后的订单表
```sql
CREATE TABLE `t_order` (
  `order_id` bigint(20) NOT NULL AUTO_INCREMENT,
  `user_id` int(11) NOT NULL,
  `address_id` bigint(20) NOT NULL,
  `status` varchar(50) DEFAULT NULL,
  `create_time` datetime NOT NULL,
  `update_time` datetime NOT NULL,
  PRIMARY KEY (`order_id`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8
```

```sql
CREATE TABLE `t_order_item` (
  `order_item_id` bigint(20) NOT NULL AUTO_INCREMENT,
  `order_id` bigint(20) DEFAULT NULL,
  `user_id` int(11) NOT NULL,
  `status` varchar(50) DEFAULT NULL,
  `create_time` datetime NOT NULL,
  `update_time` datetime NOT NULL,
  PRIMARY KEY (`order_item_id`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8
```
    
####  7. 启动single-datasource-lab项目，用于模拟原使用单库web应用
   注意以下配置，用于分库分表迁移的切换
   ```
   # 1 使用uid的初始下单  2 下单双写，以单库读写为主  3  下单双写， 以分库读写为主 4 下单只写在分库
   transfrom.step=2
   ```
   可以打包放到idea外部部署运行，高配机器可以忽略

#### 8. 启动single-datasource-lab中的[模拟客户端](./single-datasource-lab/src/test/java/com/ttx/single/lab/MockOrderService.java)，
   模拟用户访问订单服务
    
####  9. 下载datax部署同步订单历史数据
   本项目使用datax+sharding-jdbc同步订单历史数据，[使用方法](./transform-history/transform-datax-config/sharding-jdbc)              
   复制[配置](./transform-history/transform-datax-config/sharding-jdbc/datax/job)到本机datx/job目录下，并修改对应账号密码         
   使用命令运行'job-order.json','job-order_item.json'同步历史数据到分库，其中'job-order_mapping.json'是用于同步order_id和User_id的关系数据       
     
####  10. 在single-datasource-lab项目运行时配置是'transfrom.step=2'时，启动 validate-step2项目，用于校验补偿分库订单数据 
   
#### 11. 校验补平分库数据后，修改single-datasource-lab配置'transfrom.step=3',并重启
   观察是否有问题，如果有问题，则回退到step=2
     
####  12. 重启validate-step2项目，做分库最后一次校验， 因为step2启动时，会读取当前最大的订单id, 进行校验，重启是为了防止遗漏
   
   
#### 13. 启动 validate-step3项目，进行验证单库数据校验， 这里主要是为了可回滚
   
   
####  14. 继续观察single-datasource-lab，(真实项目需持续几天)， 没有问题下线单库订单
   有问题，则回退到step2, 注意，回退后，validate-step2也需重新运行校验
  




### 常见问题
  1. no table route info        
  根据路由规则得到的表名在数据库中不存在，检查[配置](./sharding-config/src/main/resources/application-sharding.yml)     
  可以开启sharding日志进行排查        
  ```
    props:
      sql:
        show: true # 打印 SQL
  ```


### 参考资料
  [大众点评订单系统分库分表实践](https://tech.meituan.com/2016/11/18/dianping-order-db-sharding.html)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)