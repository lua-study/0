# 分层的定时任务系统

## 使用技术
- 使用 .net Core 开发； 
- roncoo-adminlte 后台界面
- Quartz.net 做定时；
- nlog日志。

## 原理
设定需要定时触发任务的请求地址，请求的cron，处理成功判定结果，告警Email（sms方式需要自己实现）。
定时触发相应任务，判断是否处理成功，根据结果进行告警。

## 配置文件解析：
配置文件的配置说明请参考：[使用说明](http://git.oschina.net/9527y/LayersTimerTask/wikis/%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)

## nlog配置
详情见 _nlog.config_ 







 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)