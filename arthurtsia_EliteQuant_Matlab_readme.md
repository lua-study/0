# EliteQuant_Matlab
Matlab量化投资交易平台

* [平台介绍](#平台介绍)
* [项目纲要](#项目纲要)
* [参与开发](#参与开发)
* [项目安装](#项目安装)
* [开发环境](#开发环境)
* [项目结构](#项目结构)
* [开发计划](#开发计划)

---

## 平台介绍

EliteQuant 是一个开源并永久免费的统一量化交易平台，由量化投资者所写并为量化投资者服务。它同时在[github](https://github.com/EliteQuant) 和 [码云](https://gitee.com/EliteQuant)上开源。

统一这个词有两层意思
- 首先是统一的回测和实盘交易。只需将数据源在回测和实盘间切换即可，最大限度保持策略稳定性和真实性
- 其次，多语言编写的平台在交易结构和绩效评估上是一致的。所以在与其他交易员就策略，想法和绩效方面进行复制和交流就变得非常容易和方便。

EliteQuant 相关项目包括
- [量化投资交易资源汇总](https://gitee.com/EliteQuant/EliteQuant)
- [C++](https://gitee.com/EliteQuant/EliteQuant_Cpp)
- [Python](https://gitee.com/EliteQuant/EliteQuant_Python)
- [Matlab](https://gitee.com/EliteQuant/EliteQuant_Matlab)
- [R]()
- [C#]()
- [Excel](https://gitee.com/EliteQuant/EliteQuant_Excel)
- [Java]()
- [Scala]()
- [Go]()
- [Julia]()

## 项目纲要

EliteQuant_Matlab 是全球首个基于Matlab的回测和实盘交易开源平台。 它提供一致的回测及实时交易解决方案。它遵循现代设计模式，例如事件驱动，多线程并发式， 服务器/客户端架构和松散耦合的强大稳定的分布式系统。它遵循与其他EliteQuant产品线相同的结构和绩效评估值，这使得与使用其他语言的交易者分享变得更容易。

如需更多信息，请观看[优酷视频](http://v.youku.com/v_show/id_XMzE5MDE2MzU2MA==.html?spm=a2h3j.8428770.3416059.1)。

## 参与开发

我们欢迎任何形式的贡献，包括发现问题，发送代码块，或创建拉请求。通过共享代码架构，这还会帮助使用其他语言的交易者。

## 项目安装

不需要安装，直接下载代码并使用。

您需要将路径添加到Matlab中。假设它被下载到d：\ workspace \ elitequant_matlab中，在Matlab中运行以下命令

```matlab
javaaddpath('D:\Workspace\EliteQuant_Matlab\source\other\jnacl-0.1.0.jar')
javaaddpath('D:\Workspace\EliteQuant_Matlab\source\other\jeromq-0.4.3.jar')
javaaddpath('D:\Workspace\EliteQuant_Matlab\source\EliteQuant\+yaml\external\snakeyaml-1.9.jar')
addpath('D:\Workspace\EliteQuant_Matlab\source\EliteQuant')
```

当然，您可以将它们永久添加到你的Matlab搜索路径中，这样您不必在每次开启新的Matlab时手动添加它。但是这是可选的。

### 回测

配置 strategy 目录下的 config_backtest.yaml

* ticker: 为您感兴趣的股票期货等
* datasource: 历史数据来源
* hist_dir: 为本地历史数据目录
* output_dir： 回测结果输出目录

其中回测现有数据来源接口为

* Quandl
* 本地CSV

更多的数据源将在稍后添加。要运行回测示例，请在Matlab中导航到strategy文件夹，然后执行

```matlab
mystrat = MovingAverageCrossStrategy({'AMZN'});
engine = BacktestEngine(mystrat);
engine.run();
```

### 实盘

配置 server 目录下的 config.yaml

1. 如果要使用盈透证券，请打开盈透证券交易平台（TWS），进入菜单File / Global Configuration / API / Settings，勾选“Enable ActiveX and Socket Client”，取消选中“Read-Only API”
2. 在配置文件中，将帐户ID更改为您自己的; 盈透证券账户ID通常可以在TWS窗口的右上方找到。
3. 如果您使用CTP，请相应地更改您的经纪账户信息和ctp地址。
4. 分别为log_dir 和 data_dir创建文件夹。前者记录运行日志，而后者保存分时数据
5. 运行eqserver.exe

最后，在Matlab中执行以下命令进入实盘

```matlab
LiveEngine
```

**盈透证券**
是零售交易商中最受欢迎的经纪商。 Quantopian，Quantconnect等许多零售交易平台都是支持IB的。如果您没有IB账户，但想要试用，他们提供模拟账户edemo与密码demouser。只需下载TWS交易者工作站并使用此演示帐户登录。请注意，每次使用模拟账户登录交易平台时，账户ID都会发生变化，因此您必须相应地更改EliteQuant配置文件。

**CTP**
是中国期货市场的实际标准，包括商品期货和金融期货。他们还提供免费模拟账户[SimNow](http://simnow.com.cn)。注册后，您将获得帐户，密码，brokerid，以及市场数据和交易经纪地址。将其替换EliteQuant配置文件相应位置。

## 开发环境

以下是我们正在使用的环境
* Windows 10
* Matlab 2017a

## 项目结构

回测框架

![回测框架](/resource/Backtest_Diagram.PNG?raw=true "回测框架")

实盘框架

![实盘框架](/resource/Live_Trading_Diagram.PNG?raw=true "实盘框架")

代码结构

![代码结构](/resource/code_structure_cn.PNG?raw=true "代码结构")

## 开发计划

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)