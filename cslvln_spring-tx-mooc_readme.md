#spring-tx-mooc
##Demo1
	- 示例1为编程式的事务管理方式主要是使用 使用TransactionTemplate对Dao层的操作进行管理来使用它来进行事务管理
	- 该方式是显式的进行事务管理
	- 由于该方式在代码中有太多的事务相关代码所以不常使用
##Demo2
	- 示例2为声明式的事务管理该方式主要是使用org.springframework.transaction.interceptor.TransactionProxyFactoryBean
	- 来对要进行事务管理的service来进行增强在注入时使用该增强的bean来进行注入
	- 由于该方式在配置文件中有一个service就要有一个增强配置所以不常使用
##Demo3
	- 示例3为声明式事务管理方式 该方式主要是使用Aop的该方式对Service的事务进行管理
	- 该方式是代码配置最少的经常使用
	- 该方式的缺点就是限制死了Service的各个方法的名称
	- 以下为通配写法示例：
 ```
 
     
         
             
             
             
             
             
             
             
             
             
             
             
         
     
      
     
    	  
   		  
     
```
##Demo4
	- 示例4为声明式事务管理方式 该方式主要是使用@Transactional注解放到Service上面进行配置管理事务
	- 该方式是配置最少的但是事务管理声明比较多故而经常使用
	- 该方式的缺点就是不能对每个类的每个方法进行详细的事务管理而且使用的注解太多维护不便


###本示例使用的是mysql数据库其他数据库也一样的
 ```
SQL脚本：
CREATE TABLE `account` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(20) NOT NULL,
  `money` double DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8;
INSERT INTO `account` VALUES ('1', 'aaa', '1000');
INSERT INTO `account` VALUES ('2', 'bbb', '1000');
INSERT INTO `account` VALUES ('3', 'ccc', '1000');
SQL脚本注意之处 mysql中InnoDB是支持事务的其他像MyISAM不支持事务
```


传播行为：解决业务层方法之间的相互调用的问题（7种分3类）
1.PROPAGATION_REQUIRED 支持当前事务，如果不存在就新建一个
2.PROPAGATION_SUPPORTS 支持当前事务，如果不存在，就不使用事务
3.PROPAGATION_MANDATORY 支持当前食物，如果不存在，抛出异常

1.PROPAGATION_REQUIRES_NEW 如果有事务存在，挂起当前事务，创建一个新事物
2.PROPAGATION_NOT_SUPPORTED 以非事务方式运行，如果有事物，挂起当前事物
3.PROPAGATION_NEVER 以非事物方式运行，如果有事务存在，抛出异常

1.PROPAGATION_NESTED 如果当前事务存在，则嵌套事务执行


spring的事务隔离级别
 - DEFAULT
 - READ_UNCOMMITTED
 - READ_COMMITTED
 - REPEATABLE_READ
 - SERIALIZABLE

 隔离级别（isolation level），是指事务与事务之间的隔离程度。
显然，事务隔离程度越高，并发性越差、性能越低；事务隔离程度越低，并发性越强、性能越高。
ANSI/ISO SQL92标准中定义了4种事务隔离级别：
1.  序列化（serializable）SERIALIZABLE
最高隔离级别。系统中所有的事务都是一个接一个执行的。因此也就不会发生任何事务之间的冲突问题。
2.  可重复读（repeatable read） REPEATABLE_READ
一个事务所读取的数据记录不允许被其他事务所修改。
3. 读已提交（read committed）READ_COMMITTED
该级别允许其他事务修改当前事务所读取的数据记录，并且那个事务提交之后，当前事务可以看到修改后的数据。
4. 读未提交（read uncommitted） READ_UNCOMMITTED
该级别允许其他事务修改当前事务所读取的数据记录，并且那个事务尚未提交时，当前事务就可以看到修改后的数据。即允许脏读。
5.default DEFAULT 使用数据库的默认事务隔离级别
事务隔离级别不同，执行一条数据库查询，得到的结果很可能让你感到意外，下面是这些情况的总结：
1.       脏读
读取了其他事务还没有提交的数据。
2.       不可重复读
当前事务已经读取的数据记录，被其他事务修改或删除。
3.       幻影读
其他事务插入了新的数据，当前事务以相同的查询条件，在那个事务插入数据之前和之后查询数据，得到的数据记录的条数不一样。


隔离级别       脏读 不可重复读  幻影读
序列化            N     N     N
可重复读        N     N     Y
读已提交        N     Y     Y
读未提交        Y     Y     Y

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)