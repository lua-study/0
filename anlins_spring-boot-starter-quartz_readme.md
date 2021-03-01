
# 痛点  
在Spring中使用计划任务，有两种方案可供选择：一、用Spring原生的计划任务，使用起来非常简单，只需要用到@Scheduled注解即可；二、集成Quartz来做计划任务，需要配置大量的Quartz原生类。     
对于第一种来说，局限性在于不支持计划任务的集群，如果有多个计划任务的项目一起启动的话，每个JVM都会执行一遍预定时间的计划任务。对于Quartz来说，可以通过集群来保证在预定的时间点只会执行一次对应的计划任务。     
这里有一个问题呢，就是Spring集成了Quartz，但却并没有提供像@Scheduled这样好用的注解。     
这个项目就是为了解决上述问题而生的，让Quartz的集成变得更简单直接，同时支持Quartz的集群模式。    

# Quartz集群
先说一下Quartz的集群。    
Quartz的集群有赖于数据库的支持，所以这里我们需要一个专门的库。建表的sql在resources/sqls下面（只支持MySQL），根据要用的数据库引擎选择不同的sql文件。    
这里要注意一下，这个建表的sql文件不是每个版本都适用的，这里只适用于quartz的2.2.3版本。如果你要换版本，去官网下载对应版本的quartz，里面有相应的sql。      
建完库之后，在使用这个Starter的时候，配置文件中需要有这些属性：    
```
#是否启用集群模式
quartz.cluster=true
#计划任务实例名称
quartz.scheduler.instanceName=
quartz.datasource.driver-class-name=
quartz.datasource.url=
quartz.datasource.username=
quartz.datasource.password=
quartz.datasource.maxConnections=
```  
下面是一些数据库配置。      

# @QuartzScheduled注解
@QuartzScheduled和@Scheduled使用起来比较相似，注解到方法上即可。     
@QuartzScheduled目前只支持cron表达式，例如：   
```
    /** 凌晨自动同步一次 */
    @QuartzScheduled("20 0 0 * * ?")
    public void execute() {
        alarmService.sendSyncDingUsers();
    }
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)