#systemd_startup
在CentOS7中，都是我自己用过测试正常后再放进来的，基于systemd的自启动脚本，  
前期将zookeeper/kafka/flume/hadoop，其他的用到的时候再加。  

#使用方法：
使用root用户进入 /etc/systemd/system 目录，复制对应的文件内容，再修改下成自己的环境和变量，即可用。  

#常用systemctl命令：
（以 zookeeper 为例）  
重新加载配置信息：systemctl daemon-reload  
启动zookeeper：systemctl start zookeeper.service  
关掉zookeeper：systemctl stop zookeeper.service  
查看进程状态及日志（重要）：systemctl status zookeeper.service  
开机自启动：systemctl enable zookeeper.service  
关闭自启动：systemctl disable zookeeper.service  
分析systemd运行时间：systemd-analyze time  
查看任务的启动时间：systemd-analyze blame  
显示失败的任务：systemctl --failed  
显示激活的服务：systemctl list-units -t service  
  



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)