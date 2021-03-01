# redis_单例模式

#### 介绍
​            现在“微服务”主流的开发模式下，大量用到了“队列”，“管道”，Redis做为一款公认的高性能的数据库，在实际开发中也大量的使用Redis的列表做为“队列”，“管道”的媒介。

​			在这种情况下，在开发中很多地方要用到redis，于是我们将redis的链接池对象做成单列模式供项目的使用，即安全又高效。

#### 软件架构
只有一个redis_single.py文件


#### 安装教程

1. 放在你需要的文件夹下

2. 要安装redis模块，安装命令如下：      

   ```
   pip install redis
   ```

   

#### 使用说明

1. 就是一个普通的py文件的使用方法；
2. 配置一下文件中“Redis 数据库  全局设置”；
3. r = XzxRedis().r ,  r就是一个redis数据库的连接池对象

#### 参与贡献

1. Fork 本仓库
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