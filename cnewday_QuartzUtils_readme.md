##依赖
依赖jar quartz-2.2.1.jar
下载地址：http://www.quartz-scheduler.org/

##过期策略
* withMisfireHandlingInstructionDoNothing

不触发立即执行

等待下次Cron触发频率到达时刻开始按照Cron频率依次执行



* withMisfireHandlingInstructionIgnoreMisfires

以错过的第一个频率时间立刻开始执行

重做错过的所有频率周期后

当下一次触发频率发生时间大于当前时间后，再按照正常的Cron频率依次执行



* withMisfireHandlingInstructionFireAndProceed

以当前时间为触发频率立刻触发一次执行

然后按照Cron频率依次执行

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)