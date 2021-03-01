jfinal-scheduler插件

基于cron4j以及ScheduledThreadPoolExecutor实现的简单任务调度插件

使用方法：
在JFinal的Config配置文件中配置（编码加载）
```
    @Override
    public void configPlugin(Plugins me) {
        SchedulerPlugin sp = new SchedulerPlugin();
        Runnable task = new TestTask();
        //每隔10秒执行一次
        //sp.fixedDelaySchedule(task, 10);
        //sp.fixedRateSchedule(task, 10);
        //每隔1分钟执行一次
        sp.cronSchedule(task, "* * * * *");
        me.add(sp);
```

在JFinal的Config配置文件中配置（通过配置文件加载）
```
    @Override
    public void configPlugin(Plugins me) {
        SchedulerPlugin sp = new SchedulerPlugin("job.properties");
        me.add(sp);
```

job.properties
```
#是否启用该任务
testJob.enable=true
#任务类名
testJob.class=com.wellbole.web.core.TestTask
#任务类型以及表达式
#testJob.type=cron
#testJob.expr=* * * * *

#每隔10秒（每分钟6次）执行一次
testJob.type=fixedRate
testJob.expr=10

#每隔5秒(任务一个接着一个)执行一次
#testJob.type=fixedDelay
#testJob.expr=5

#job1.class=x.y.z.Runnable
#...
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)