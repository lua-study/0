

# 多线程爬虫小框架

#### 介绍
在实际开发中，经常要用多线程来加速任务处理，尤其写爬虫中，并发下载信息更是必须会的技能，本框架十分微小，上手快，传递一种思维。

可以和我之前的“爬虫代理迷你框架”+“多线程爬虫小框架”+“微服务思维”灵活组合来实现我们的爬虫开发。

#### 软件架构
##### 架构说明：大体上分为两部分

- ##### 	“工厂”部分 ： factory.py

  - Factory类理解为一个工厂
    - 其中包含，任务管道，和工作流程
  - Factory.task_pipeline 方法
    - 任务管道,#由于本例task_pipeline是一个迭代器，所以work_task才是真正的管道
  - Factory.worker_func方法
    - 白话：工人要做的具体工作，即工作流程
    -  一般是一个循环
    - 构造该方法时，重点要包含：
      -  所有工作完成后如何退出
      - 工作中出错了如何处理
      - 一个工作完成后如何处理

- ##### “工厂”启动部分：

  1. 将我们建好的工厂启动起来，白话：招工人干活
  2. 框架中写了两种启动多线程的方法：
     1. executor_run.py     使用了线程池来做多线程
     2. thread_run.py  使用了threading模块来做多线程									

------



#### 安装教程

1. 需要安装requests模块

   ```
   pip install requests
   ```



 

#### 使用说明

- ##### 重构factory.py文件下的Factory类；

  - task_pipeline从任务管道中取出任务；
  - worker_func，要工作的内容，一般是一个循环，从task_pipeline中取任务，然后处理，在构造本函数时要包含以下重点：
    - 所有工作完成后如何退出或监听；
    - 工作中出错了如何处理；
    - 一个工作完成后如何处理；

- ##### 多线程运行方式，运行一个工厂；

   

   

   

  - executor_run.py  使用了线程池来运行factory,开启5个线程（即5个工人）,示例如下：

    - ```
      from factory import Factory#你要运行的工厂类
      
      from executor_run import ManyExecutor
      
      ManyExecutor(factory = Factory, worker_num = 5).run
      ```

  - thread_run.py  使用了threading模块来运行factory,开启5个线程（即5个工人），示例如下：

    - ```
      from factory import Factory#你要运行的工厂类
      
      from executor_run import ManyExecutor
      
      ManyExecutor(factory = Factory, worker_num = 5).run
      ```

- 可以结合[“爬虫代理迷你框架”](https://gitee.com/zhangpengju/dailiqingqiu)来构造factory.py,可以做出多线程，自动切换代理的爬虫，几个小框架十分灵活，用来组合分布式爬虫最适合;

- 还会继续更新celery的用法;

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