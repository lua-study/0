# pyrabbitmq

#### 项目介绍
RabbitMQ简单封装, 学习demo.

#### 软件架构
软件架构说明


#### 安装教程

1. virtualbox虚拟机ubuntu16.04, 安装rabbitmq-server, 添加admin用户,配置远程访问和/vhosts权限.
2. python3.6环境, pip install pika
3. from mq import * 即可使用, (除mq.py外其他py文件都是示例)

#### 使用说明(注意按顺序启动, 消费者->生产者)

1. 点对点

消费者:
QueueChannel(MQConnection()).listening()

生产者:
QueueChannel(MQConnection()).send()

2. 一对多

消费者:
ExchangeChannel(MQConnection()).listening()

生产者:
ExchangeChannel(MQConnection()).send()

3. 还有很多没有完善: 报错处理, 大数据量调试, 配置优化, 日志, 集群...

#### 参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


#### 码云特技

1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)