

------

环境：

[jkd8+]()

[mysql5.6+]()



## 一、原理

​	计时器事件是由定义的计时器触发的事件。它们可以用作[开始事件](https://www.flowable.org/docs/userguide/index.html#bpmnTimerStartEvent)，[中间事件](https://www.flowable.org/docs/userguide/index.html#bpmnIntermediateCatchingEvent)或[边界事件](https://www.flowable.org/docs/userguide/index.html#bpmnTimerBoundaryEvent)。时间事件的行为取决于使用的业务日历。每个计时器事件都有一个默认的业务日历，但业务日历也可以作为计时器事件定义的一部分给出。

​	本例中定义了定时开始启动事件，并且在人工任务2处定义了定时边界事件，定时触发对应服务任务执行，如果定义了边界事件触发时取消操作cancelActivity="true"，当边界事件触发时，那么此边界事件所在的节点任务将会被删除，默认为cancelActivity="false"。

​	人工任务2后面也定义一个中间定时事件。

​	定时事件会启动的时候在ACT_RU_TIMER_JOB表中插入定时job,定时执行完毕后，会删除此表的数据。

​	**注意：定时事件，已定义要开始定时开关：**

```
 
 
```

　当人工任务2在定时边界事件触发之前手动完成，那么人工任务2处的定时事件将会删除(ACT_RU_TIMER_JOB表中数据将会被删除)。

## 二、流程图

![./images/timereventprocess.png](./images/timereventprocess.png)



## 三、实践测试

- 部署流程定义，运行deploy()方法
- 查看数据库表

```
SELECT * FROM ACT_RU_TIMER_JOB;//定时任务表
```

- 依次完成任务



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)