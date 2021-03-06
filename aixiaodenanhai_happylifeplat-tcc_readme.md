happylifeplat-tcc
================

碧桂园旺生活平台解决分布式事务方案之tcc开源框架。基于java语言来开发（JDK1.8），支持dubbo，springcloud等rpc框架进行分布式事务.
#####   因为文件名太长，大家在拉取代码的时候执git命令：git config core.longpaths true

 # Features

 * **框架特性**

     * 支持dubbo，springcloud等rpc框架进行分布式事务。

     * 采用Aspect AOP 切面思想与Spring无缝集成，天然支持集群。

     * 配置简单，集成简单，源码简洁，稳定性高，已在生产环境使用。

     * 内置经典的分布式事务场景demo工程，并有swagger-ui可视化界面可以快速体验。


 * **SPI扩展**
     * 本地事务存储，支持redis，mogondb，zookeeper，file，mysql等关系型数据库
     * 序列化方式，支持java，hessian，kryo，protostuff


# TCC原理介绍
  ####  [原理介绍](https://github.com/yu199195/happylifeplat-tcc/wiki/TCC%E5%8E%9F%E7%90%86%E4%BB%8B%E7%B4%B9)

#   Configuration

  ####  [配置详解](https://github.com/yu199195/happylifeplat-tcc/wiki/%E9%85%8D%E7%BD%AE%E8%AF%A6%E8%A7%A3)

# Usage

   ### [快速体检(dubbo)](https://github.com/yu199195/happylifeplat-tcc/wiki/%E5%BF%AB%E9%80%9F%E4%BD%93%E9%AA%8C%EF%BC%88dubbo%EF%BC%89)

   ### [快速体检(springcloud)](https://github.com/yu199195/happylifeplat-tcc/wiki/%E5%BF%AB%E9%80%9F%E4%BD%93%E9%AA%8C%EF%BC%88springcloud%EF%BC%89)


 # Support
   ##### 如有任何问题欢迎加入QQ群：162614487 进行讨论


 # Contribution


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)