# Magnet

#### 介绍
三分钟快速搭建流式处理应用！简单实用的分布式大数据处理框架，特点是零基础操作，支持批处理和流式处理。

 
 
    
    

#### 软件架构
![Magnet架构图](https://images.gitee.com/uploads/images/2020/0429/233028_cc6696d7_612479.png "Magnet架构图.png")
项目目前由core、xmlbuilder、spark1和client四个模块组成，core模块封装了各个部分的抽象组件；xmlbuilder模块是以xml解析为执行配置来源的读取模块；spark1模块为大数据引擎模块；client模块是客户端调用模块。项目可以扩展执行配置的解析方式和大数据处理引擎，良好的接口可以兼容任何大数据引擎。架构图中蓝色部分为框架的核心模块，非蓝色部分均为可扩展模块。你可以扩展配置文件的格式，可以是json配置、db配置或自定义格式；你也可以扩展大数据处理引擎，Flink、Hive、Kafka或MapReduce；你也可以扩展各种标签组件；你还可以扩展每个标签组件的包装wrapper，用于处理每个标签组件的前置和后置操作。

#### 使用说明
- [Magnet介绍](https://gitee.com/huanStephen/magnet/wikis/pages)
- [快速入门](https://gitee.com/huanStephen/magnet/wikis/pages)
- [配置文件结构](https://gitee.com/huanStephen/magnet/wikis/pages)
- [使用IDEA打包项目](https://gitee.com/huanStephen/magnet/wikis/pages)
- [parameter参数标签](https://gitee.com/huanStephen/magnet/wikis/pages)
- [fragment碎片标签](https://gitee.com/huanStephen/magnet/wikis/pages)
- [datasource数据源标签](https://gitee.com/huanStephen/magnet/wikis/pages)
- [workflow工作流标签](https://gitee.com/huanStephen/magnet/wikis/pages)
> - [SQL标签](https://gitee.com/huanStephen/magnet/wikis/pages)
> - [filter标签](https://gitee.com/huanStephen/magnet/wikis/pages)
> - [distinct标签](https://gitee.com/huanStephen/magnet/wikis/pages)
> - [output标签](https://gitee.com/huanStephen/magnet/wikis/pages)
> - [valueMappers标签](https://gitee.com/huanStephen/magnet/wikis/pages)
> - [splitFieldToRows标签](https://gitee.com/huanStephen/magnet/wikis/pages)
> - [stringCuts标签](https://gitee.com/huanStephen/magnet/wikis/pages)
> - [addFields标签](https://gitee.com/huanStephen/magnet/wikis/pages)
> - [addSequence标签](https://gitee.com/huanStephen/magnet/wikis/pages)
- [开发指南](https://gitee.com/huanStephen/magnet/wikis/pages)
> - [框架结构介绍](https://gitee.com/huanStephen/magnet/wikis/pages)
> - [扩展新处理引擎](https://gitee.com/huanStephen/magnet/wikis/pages)
> - [扩展新标签](https://gitee.com/huanStephen/magnet/wikis/pages)

#### 参与贡献
[贡献者列表](https://gitee.com/huanStephen/magnet/contributors?ref=master)

#### 加入我们
如果：

- 你对Magnet感兴趣
- 你有风骚的创意
- 你对大数据技术有兴趣
- 你想用Magnet解决工作中的问题，却发现Magnet解决不了
- 你想加入Magnet认识更多帅哥
- 未完待续...

你都可以加入我们Magnet社区，我们为你提供创造性的舞台接受你风骚的想法，或者解决实际工作中繁杂的任务。

   

#### 项目演示
示例测试文件链接: https://pan.baidu.com/s/1HSQLHD5mzDhlDe4FgQamuw 提取码: e9ip

批处理示例：

![批处理](https://images.gitee.com/uploads/images/2020/0331/214445_a5d64ad6_612479.gif "magnet-03311.gif")

流处理示例：

![流处理](https://images.gitee.com/uploads/images/2020/0514/230321_2f122ee2_612479.gif "magnet-stream.gif")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)