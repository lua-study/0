#### 介绍
zabbix agent 用户自定义 key

#### 安装
- 拷贝相应的文件到{zabbix-home}目录下
- 在 zabbix agent (被监控端) 修改 {zabbix-home}/etc/zabbix_agentd.conf
    ```
    AllowRoot=1
    UnsafeUserParameters=1
    UserParameter=UP[*],{zabbix-home}/UP.sh $1 $2 $3 $4 $5 $6 $7 $8 $9
    ```
- 重启 zabbix agent 服务

#### 监控项键值
- **UP[0,tcp,80]** 获取被监控机器的 tcp 端口 80 的连接量
- **UP[0,udp,80,443]** 获取被监控机器的 tcp 端口 80 和 443 的总连接量
- **UP[1]** 获取 mysql slave 状态，如果正常，则返回同步延迟时间(秒)
- **UP[2]** 获取 ceph 集群状态
- **UP[3]** 获取 当前机器的不明网络连接
    - 要忽略的外部 IP 需写入 white_ip.list 或 custom_ip.list
    - 要忽略的本地端口需写入 white_port.list 或 custom_port.list



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)