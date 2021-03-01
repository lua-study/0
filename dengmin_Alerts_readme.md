#Alerts
##介绍
- 基于Django 1.9.1， Python 2.7，dwebsocket
- 支持所有监控平台，只需将告警信息按照要求发送到本平台即可
- 告警收敛是基于主机维度进行收敛的
- 所有告警级别都会汇总，且告警级别为Disaster的，会立即发出
- 依赖mongoDB存储数据
- 支持发送报警至企业微信

##安装/使用
**步骤 1**: 下载代码

```
git clone https://git.oschina.net/XJGZ/Alerts.git Alerts
```

**步骤 2**: 配置

```
cd Alerts
#修改./Alerts/views.py的第21行，将mongoDB的连接信息配置上去
#修改./Alerts/views.py的第76和126行，将校验码（密码）修改为自己定义的密码
#初始mongodb数据monitor.Time={"type": "Old", "Time": str(int(time.time()))}
#初始mongodb数据monitor.Time={"type": "New", "Time": str(int(time.time()))}
```

**步骤 3**: 运行

```
./manage.py runserver 0.0.0.0 8000
#正式环境请使用其他的多进程/线程方式运行，如gunicorn
```

**步骤 3**: 使用

- 收集告警

```
任何告警通过以下格式，使用"Content-Type": "application/x-www-form-urlencoded"post以下字符串（需要转换成url编码）到这个接口
{"type": "0",
"level": "告警级别",
"item": "告警项",
"value": "当前值",
"hostname": "主机名",
"datetime": "告警时间",
"EventID": "事件id",
"ACK": "xjACK"(这个要与步骤2的校验码相同)}

{"type": "1",
"level": "告警级别",
"item": "告警项",
"value": "当前值",
"hostname": "主机名",
"datetime": "恢复时间",
"EventID": "事件id",
"ACK": "xjACK"(这个要与步骤2的校验码相同)}
```

- 分析告警(crontab定时触发，时间间隔为告警汇总的时间区间)

```
使用"Content-Type": "application/x-www-form-urlencoded"post以下字符串到这个接口
ACK=xjACK(这个要与步骤2的校验码相同)
```

##汇总告警示例

```
2016.08.03 00:40:01 至 2016.08.03 00:50:01 告警汇报 

告警对象: 192.168.1.1
汇总: 故障 2 , 恢复 1 , 剩余 1 
剩余内容: 5分钟内接口/abc/test耗时大于5秒次数:111

告警对象: 192.168.1.2
汇总: 故障 14 , 恢复 10 , 剩余 4 
剩余内容: icmppingloss qq 192.168.2.1:65
icmppingloss baidu 192.168.3.1:60

告警对象: 192.168.1.3 
汇总: 故障 2 , 恢复 0 , 剩余 2 
剩余内容: http5分钟内408次数:123
http5分钟内400次数:74
```

##websocket

![websocket](http://git.oschina.net/XJGZ/Alerts/raw/master/static/demo.jpg)


##微信报警
```
进入 http://work.weixin.qq.com/wework_admin/frame#apps/createApiApp 创建一个消息型应用
记录页面中的secret和应用ID，将来作为misc_func.PushWX中的corpsecret和agentid参数（在./Alerts/views.py文件的100、178和223行）
```
![wx](http://git.oschina.net/XJGZ/Alerts/raw/master/static/WXdemo.jpg)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)