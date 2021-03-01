# simplewebserver-performance

> 简单对比simplewebserver和基于t-io的http-server的性能，主要是想看看t-io是想了解下是否自己搞了什么黑科技

### 准备
- ab
- jdk8 (tio使用的是1.8)
- mvn

### 测试方式
- 安装 ab
  - ubuntu: `apt-get install apache2-utils`
  - window: 自己检索如何安装 ab
- 使用unix系统可以直接使用提供的sh文件

由于电脑的性能差异，可能各项数据存在比较大的差异，但理论上不影响比较的结果

个人测试的电脑配置

![](img/ubuntu-pc.png)

并不是专业做测试的，测试结果看看就行了

![](result/200000-100.png)

**结果可以看的出来的是，每个请求的处理时间差异基本都在几百微秒内。作为互联网应用用户首次建立连接都在几十毫秒，这一点性能的差异基本忽略不计了**

### 总结
决定程序的处理性能因素比较多，常见的
- 程序员自身的水平
- 使用语言的优劣
- 计算机CPU，内存的搭配
- 程序中的线程数量是否合理
- Java里面的NIO/AIO，应用场景不同，各有各优劣
- ...

单纯的从使用了某种技术就说高性能是占不住脚的

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)