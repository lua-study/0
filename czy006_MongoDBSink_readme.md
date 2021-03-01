# MongoDBSink

#### 介绍
实现​Java写日志到Flume，Flume最终把日志写到MongoDB

#### 安装教程

1. 前往Flume官方地址下载Flume1.8.0
2. 前往MongoDB下载4.0版本MongoDB
3. 线上使用需在flume/lib下添加一下几个jar包
- mongodb-driver-3.8.2.jar
- mongodb-driver-core-3.8.2.jar
- bson-3.8.2.jar

#### 使用说明

1. 下载本项目后打JAR包放入flume/lib下
2. 在Flume的conf目录配置MongoDBFlume.conf （仓库有案例配置文件）
3. 运行：bin/flume-ng agent --conf conf --conf-file conf/MongoDBFlume.conf --name a1 -Dflume.root.logger=info,console
4. 本地测试：telnet localhost 44444
5. 在telnet插入JSON数据测试

#### 使用注意
- 如果没有密码和用户名 就不需要user password authentication_enabled这3个参数
- 如果有密码，请设置authentication_enabled = True

#### 参与贡献

1. Fork 本仓库
2. 新建分支
3. 提交代码
4. 新建 Pull Request

#### 联系作者
1. 红警专家 [blog.gzczy.top](https://blog.gzczy.top)
2. 关注微信公众号：JAVA大咖说

![Image discription](http://image.gzczy.top/2018/12/qrcode_for_gh_c464884a70ff_258.jpg)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)