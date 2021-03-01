# spring-scheduling-cluster
Spring Boot 自带定时器Scheduled增加分布式/集群环境下任务调度控制插件，其原理是对任务加锁实现控制，支持能实现分布锁的中间件。
下面提供了redis缓存和mysql数据库的实现，如果使用到其它中间件暂时麻烦请自行实现，下面会讲如果实现的。

## 环境要求和关键技术
- [JDK1.7](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
- [Spring Boot 1.5.7.RELEASE](https://docs.spring.io/spring-boot/docs/1.5.7.RELEASE/reference/html/)

## 添加插件到项目中并启用

### 添加插件
1. 方式一：下载本项目源码然后加添加到项目中。
2. 方式二：下载本项目的[jar包](https://gitee.com/lnkToKing/spring-scheduling-cluster/attach_files)，添加到项目的libs包库中。
3. 方式三：下载本项目的[jar包](https://gitee.com/lnkToKing/spring-scheduling-cluster/attach_files)，添加到本地maven库中，然后在pom.xml文件添加引用

``` xml
 
     pres.lnk.springframework 
     spring-scheduling-cluster 
     1.0-BATE 
 
```

### 启用插件
在 Spring 配置中添加以下代码将插件注册成Bean（注意，原来用来启动定时器的注解@EnableScheduling还是要添加的）

``` java
@Bean(name = TaskManagementConfigUtils.SCHEDULED_ANNOTATION_PROCESSOR_BEAN_NAME)
@Role(BeanDefinition.ROLE_INFRASTRUCTURE)
public ScheduledAnnotationBeanPostProcessor scheduledAnnotationProcessor() {
    return new ScheduledClusterAnnotationBeanPostProcessor();
}
```

## 实现调度器中间件对定时任务进行锁操作

### 使用 redis 缓存做中间件
将下面类的代码添加到项目中，并注册成SpringBean限可   
redis实现代码 https://gitee.com/lnkToKing/codes/a8lpt3qu0dxsofgneyck293


### 使用 mysql数据库 做中间件
由于每个项目使用的持久化框架不一样，下面只提供了MyBatis的实现做参考，请根据自己项目框架做改动   
mysql实现代码 https://gitee.com/lnkToKing/codes/58odhmxnve63ua41qlgs064#MysqlSchedulerImpl.java   
基本MyBatis实现的数据访问Mapper代码 https://gitee.com/lnkToKing/codes/58odhmxnve63ua41qlgs064#TimedTaskMapper.java   

数据库表结构   
t_timed_task

字段 | 类型 | 说明
 --- | --- | --- 
id | varchar(255) PRIMARY NOT NULL | 任务id
timeout | bigint NOT NULL | 锁的失效时间
value | varchar(255) DEFAULT NULL | 锁对应的值

``` sql
DROP TABLE IF EXISTS `t_timed_task`;

CREATE TABLE `t_timed_task` (
  `id` varchar(255) NOT NULL,
  `timeout` bigint(20) NOT NULL,
  `value` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```


### 使用 zookeeper 做中间件
将下面类的代码添加到项目中   
zookeeper实现代码 https://gitee.com/lnkToKing/codes/70mzu5eday6gtip1nw9vj67   
然后注册成SpringBean
``` java
@Bean
public ZookeeperSchedulerImpl getScheduler(CuratorFramework zkClient) throws Exception {
    return new ZookeeperSchedulerImpl(zkClient);
}
```
需要注意一点：实现类的currentTimeMillis方法获取的是本地时间，如果集群中某些或某个服务器系统时间误差太大，可能会造成任务执行间隔缩短。所以最好修改该方法从指定的服务器获取一致的时间，例如可以获取数据库的时间。


### 自定义中间件
自定义类继承抽象类`AbstractScheduler`，实现父类的方法并注册成Spring Bean。   
`AbstractScheduler` 方法说明

 方法 | 必须 | 说明
  --- | --- | --- 
 boolean check(String id) | 是 | 检查任务id是否没被锁，如果没被锁则表示可以执行任务，下一步就获取锁 
 boolean lock(String id, long timeoutMillis) | 是 | 对任务id加锁，并在下次执行任务前释放锁，返回加锁是否成功 
 void relock(String id, long timeoutMillis) | 是 | 修改任务id锁的释放时间 
 long currentTimeMillis() | 是 |  获取中间件的服务器时间，做为锁的参考时间。集群所有服务器最好做时间同步，避免cron任务出现误差 
 void keepAlive() | 如果启用优先级功能则必须重写 | 将服务器最高优先级别保存到中间件
 int getMaxAliveLevel() | 如果启用优先级功能则必须重写 | 获取中间件保存的最高级别 
 void executed(Method method, Object targer, long startTimeMillis, long endTimeMillis, String description) | 否 | 定时任务执行结束的后续处理 


## 设置主从服务器
主从服务器是通过设置服务器优先级实现，实现原理是优先级高的服务器定时（心跳时间）告诉中间件我还活着（运行中），
然后优先级低的服务器则不执行任务。如果优先级高级服务器挂了，中间件不再接收到信息了，优先级低的服务器就会接替继续工作。

#### 设置方式
在spring的yml配置文件中添加下面配置
``` yaml
spring:
  scheduling:
    cluster:
      level: 1      #优先级别
      heartTime: 60 #心跳时间（秒）
```

配置说明：   
level ： 优先级别，1 等级最高，数字越大等级越低。其中 0 是该服务器不执行定时任务。 -1 是不参与集群服务调度，不受优先级影响，任务每次都会执行。   
heartTime ： 心跳时间，服务器会以这个时间频率告诉中间件我还活着   

重写中间件的getLevel()方法，可自定义level规则，例如根据ip判断level，这样不用每个服务器单独改配置文件

## 注解@ScheduledCluster
该注解用在`@Scheduled`的方法上，可选的，有以下属性和作用

属性 | 必填 | 说明
--- | --- | ---
id | 否 | 自定义任务id，同一个时间段内同一个id的任务只有一个能执行成功
description | 否 | 任务描述
ignore | 否 | 是否忽略集群控制，作用跟level=-1一样，但只针对该任务

``` java
@ScheduledCluster(id="updateData", description = "每小时更新一次数据")
@Scheduled(cron = "0 0 0/1 * * ?")
public void update(){
    // 更新数据
}
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)