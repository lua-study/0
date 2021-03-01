### 关键组件
#### Scheduler
与调度程序交互的主要API。

#### Job
调度程序执行的组件需要实现该接口。
当Job的一个trigger被触发时，job的execute()方法由调度程序的一个工作线程调用。
传递给execute()方法的JobExecutionContext对象中保存着该job运行时的一些信息、执行job的scheduler的引用、触发job的trigger的引用，JobDetail对象引用、以及一些其它信息。

#### JobDetail
用于定义作业的实例。JobDetail对象是在将job加入scheduler时，由客户端程序（你的程序）创建的。它包含job的各种属性设置，以及用于存储job实例状态信息的JobDataMap。\
每次当scheduler执行job时，在调用其execute(…)方法之前会创建该类的一个新的实例；执行完毕，对该实例的引用就被丢弃了，实例会被垃圾回收；\
这种执行策略带来的一个后果是，job必须有一个无参的构造函数（当使用默认的JobFactory时）；\
另一个后果是，在job类中，不应该定义有状态的数据属性，因为在job的多次执行中，这些属性的值不会保留。\
通过JobDetail对象，可以给job实例配置的其它属性有：
- Durability：如果一个job是非持久的，当没有活跃的trigger与之关联的时候，会被自动地从scheduler中删除。也就是说，非持久的job的生命期是由trigger的存在与否决定的；
- RequestsRecovery：如果一个job是可恢复的，并且在其执行的时候，scheduler发生硬关闭（hard shutdown)（比如运行的进程崩溃了，或者关机了），则当scheduler重新启动的时候，该job会被重新执行。此时，该job的JobExecutionContext.isRecovering() 返回true。

#### Trigger（即触发器）
定义执行给定作业的计划的组件，用于触发Job的执行。Trigger也有一个相关联的JobDataMap，用于给Job传递一些触发相关的参数。\
Quartz自带了各种不同类型的Trigger，最常用的主要是SimpleTrigger和CronTrigger。

trigger的公共属性：
- jobKey属性：当trigger触发时被执行的job的身份；
- startTime属性：设置trigger第一次触发的时间；该属性的值是java.util.Date类型，表示某个指定的时间点；有些类型的trigger，会在设置的startTime时立即触发，有些类型的trigger，表示其触发是在startTime之后开始生效。比如，现在是1月份，你设置了一个trigger–“在每个月的第5天执行”，然后你将startTime属性设置为4月1号，则该trigger第一次触发会是在几个月以后了(即4月5号)。
- endTime属性：表示trigger失效的时间点。比如，”每月第5天执行”的trigger，如果其endTime是7月1号，则其最后一次执行时间是6月5号。
- priority：默认优先级为5，可以是任意整数，正数、负数都可以。只有同时触发的trigger之间才会比较优先级，越大优先级越高。
- 错过触发(misfire Instructions)：不同类型的trigger，有不同的misfire机制。它们默认都使用“智能机制(smart policy)”，即根据trigger的类型和配置动态调整行为。当scheduler启动的时候，查询所有错过触发(misfire)的持久性trigger。然后根据它们各自的misfire机制更新trigger的信息。
- 日历示例(calendar)：用于从trigger的调度计划中排除时间段（不是java.util.Calendar对象）。
##### SimpleTrigger
主要用于一次性执行的Job（只在某个特定的时间点执行一次），或者Job在特定的时间点执行，重复执行N次，每次执行间隔T个时间单位。
SimpleTrigger的属性包括：开始时间、结束时间、重复次数以及重复的间隔。重复次数，可以是0、正整数，以及常量SimpleTrigger.REPEAT_INDEFINITELY。重复的间隔，必须是0，或者long型的正数，表示毫秒。注意，如果重复间隔为0，trigger将会以重复次数并发执行(或者以scheduler可以处理的近似并发数)。
##### CronTrigger
基于crontab定时表达式

#### JobBuilder
用于定义/构建JobDetail实例，用于定义作业的实例。

#### TriggerBuilder - 用于定义/构建触发器实例。


### 概念
#### Key
将Job和Trigger注册到Scheduler时，可以为它们设置key，配置其身份属性。
Job和Trigger的key（JobKey和TriggerKey）可以用于将Job和Trigger放到不同的分组（group）里，然后基于分组进行操作。同一个分组下的Job或Trigger的名称必须唯一，即一个Job或Trigger的key由名称（name）和分组（group）组成。
#### JobDataMap
JobDataMap中可以包含不限量的（序列化的）数据对象，在job实例执行的时候，可以使用其中的数据；\
JobDataMap是Java Map接口的一个实现，额外增加了一些便于存取基本类型的数据的方法。
在Job执行时，可以通过JobExecutionContext.getJobDataMap()取出数据，它是JobDetail中的JobDataMap和Trigger中的JobDataMap的并集，但是如果存在相同的数据，则后者会覆盖前者的值。\
Quartz的默认JobFactory实现在job被实例化的时候会自动调用这些set 方法（如果key在JobDataMap中有存储），这样你就不需要在execute()方法中显式地从map中取数据了。
#### job状态和并发
##### @DisallowConcurrentExecution
将该注解加到job类上，告诉Quartz不要并发地执行同一个job定义（这里指特定的job类）的多个实例。该限制是针对JobDetail的，而不是job类的。
##### @PersistJobDataAfterExecution
将该注解加在job类上，告诉Quartz在成功执行了job类的execute方法后（没有发生任何异常），更新JobDetail中JobDataMap的数据，使得该job（即JobDetail）在下一次执行的时候，JobDataMap中是更新后的数据，而不是更新前的旧数据。\
如果你使用了@PersistJobDataAfterExecution注解，我们强烈建议你同时使用@DisallowConcurrentExecution注解，因为当同一个job（JobDetail）的两个实例被并发执行时，由于竞争，JobDataMap中存储的数据很可能是不确定的。
#### JobExecutionException
最后，是关于Job.execute(..)方法的一些额外细节。execute方法中仅允许抛出一种类型的异常（包括RuntimeExceptions），即JobExecutionException。


### Scheduler的生命期
从SchedulerFactory创建它时开始，到Scheduler调用shutdown()方法时结束；Scheduler被创建后，可以增加、删除和列举Job和Trigger，以及执行其它与调度相关的操作（如暂停Trigger）。\
但是，Scheduler只有在调用start()方法后，才会真正地触发trigger（即执行job）


### Cron-Expressions
用于配置CronTrigger的实例。Cron Expressions是由七个子表达式组成的字符串，用于描述日程表的各个细节。这些子表达式用空格分隔，并表示：
    
    Seconds
    Minutes
    Hours
    Day-of-Month
    Month
    Day-of-Week
    Year (optional field)


### quartz自带的建表sql文件目录
quartz-2.3.0.jar!\org\quartz\impl\jdbcjobstore\

### 文档
https://www.w3cschool.cn/quartz_doc/quartz_doc-kixe2cq3.html

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)