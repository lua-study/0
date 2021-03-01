## 消息队列
> 边学习rocketmq,边动手写的。 MASTER-SLAVE模式已经完成，但是主节点 向从节点 的数据复制 还没有完全测试，可能存在BUG. 

因为业务爱好，所以只能闲暇时间完善，因此有些地方不太好，比如功能模块化，最开始只是学习，也没想到会做出来，因此好多功能全都放一起了，但几乎每个文件都有注释。

#### yaojin_mq.zip
  该包下面是一些快速启动的快捷方式，其中nameSrv 是服务节点；broker 是存储节点；client是消费节点

#### namesrv运行入口
     com.cn.broker.BrokerStart

#### broker运行入口
     com.cn.namesrv.NameSrvStart

#### yaojin_mq.zip 是运行包，解压开后，就可以运行了
 ###### 1. bin目录下程序的运行入口
 ###### 2. conf 目录下是配置文件
 ###### 3. lib 是需要的jar
 `运行服务节点： nameSrv.cmd -c ../conf/config.cfg`
 `运行broker节点：broker.cmd -c ../conf/config.cfg`
     
#### springMVC环境集成 DEMO
     https://gitee.com/cn_yaojin/mq_demo.git

#### spring Boot 环境集成 DEMO


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)