# EliteQuant_Cpp
C/C++高频量化投资交易平台

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

EliteQuant_Cpp是基于C/C++ 11的多线程并发式高频交易平台。它遵循现代设计模式，例如事件驱动，服务器/客户端架构，依赖注入和松散耦合的强大稳定的分布式系统。它可以独立运行和直接使用。同时，它也作为其他EliteQuant项目的服务器端。

## 参与开发

我们欢迎任何形式的贡献，包括发现问题，发送代码块，或创建拉请求。通过共享代码架构，这还会帮助使用其他语言的交易者。

## 项目安装

不需要安装，直接下载代码并使用。

最简单的方法是从项目根目录下载并编译compiled.zip。然后运行名为eqsever.exe的程序。在运行此可执行文件之前，需要修改几个配置设置。默认情况下，程序从相同的目录中读取config.xml。因此打开配置文件
1. 如果要使用盈透证券，请打开盈透证券交易平台（TWS），进入菜单File / Global Configuration / API / Settings，勾选“Enable ActiveX and Socket Client”，取消选中“Read-Only API”
2. 在配置文件中，将帐户ID更改为您自己的; 盈透证券账户ID通常可以在TWS窗口的右上方找到。
3. 如果您使用CTP，请相应地更改您的经纪账户信息和ctp地址。
4. 分别为log_dir 和 data_dir创建文件夹。前者记录运行日志，而后者保存分时数据

**盈透证券**
是零售交易商中最受欢迎的经纪商。 Quantopian，Quantconnect等许多零售交易平台都是支持IB的。如果您没有IB账户，但想要试用，他们提供模拟账户edemo与密码demouser。只需下载TWS交易者工作站并使用此演示帐户登录。请注意，每次使用模拟账户登录交易平台时，账户ID都会发生变化，因此您必须相应地更改EliteQuant配置文件。

**CTP**
是中国期货市场的实际标准，包括商品期货和金融期货。他们还提供免费模拟账户[SimNow](http://simnow.com.cn)。注册后，您将获得帐户，密码，brokerid，以及市场数据和交易经纪地址。将其替换EliteQuant配置文件相应位置。

## 开发环境

以下是我们正在使用的环境

* Windows上的Visual Studio 2017社区版
* Linux上的CodeLite 11.0.6

Visual C ++是Windows上流行的IDE。 CodeLite是一个免费的Linux IDE，在用户体验方面非常接近Visual Studio。其他的选择是CLION，CMake等。

### Linux 下的开发环境

您可以按照以下步骤安装必要的第三方库，并使用cmake在最新的64位Ubuntu系统上构建此项目。

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install aptitude git cmake 
sudo aptitude install zlib1g-dev rapidjson-dev python3-dev libboost-all-dev libsodium-dev \
                      libyaml-cpp-dev libwebsocketpp-dev libnanomsg-dev libzmq3-dev

# 下载 SimNow CTP tradeapi Linux 版本
cd ~          # 或者您选择的目录 
wget http://simnow.sfit.com.cn/download/api/v6.3.5_20150803_tradeapi_linux64.tar
tar xvf v6.3.5_20150803_tradeapi_linux64.tar
cd v6.3.5_20150803_api_tradeapi_linux64/
sudo cp thostmduserapi.so /usr/lib/libthostmduserapi.so
sudo cp thosttraderapi.so /usr/lib/libthosttraderapi.so
cd ~        # 或者您选择的目录        
git clone https://github.com/EliteQuant/EliteQuant_Cpp.git
cd EliteQuant_Cpp/source
mkdir build
cd build
cmake ..
make -j2

# 运行程序
cd eqserver
cp ../../eqserver/config.yaml .
mkdir log data
./eqserver             # 在这之前要改动 config.yaml
```

在Linux上，按Ctrl + C终止eqserver时，可能会遇到**double free or corruption（！prev）**错误。抑制此警告的一种方法是将**MALLOC_CHECK_ = 0**变量添加到您的环境中。
```bash
sudo vim ~/.bashrc          # 编辑系统配置文件
export MALLOC_CHECK_=0      # 把这一行加到文件最后
source ~/.bashrc            # 重新加载配置
```

## 项目结构

### 微服务
| 服务        | 协议     | 端口  | 捆绑还是连接 |
| ------------- |:-------------:| -----:| -----:|
| MarketData      | PUB | 55555 | Y |
| Brokerage      | PAIR | 55556 | Y |
| DataManager/BarAggregator      | PUB | 55557 | Y |
| TickRecording      | SUB      |   55555 | N |
| DataBoard | SUB      |   55555 | N |
| ApiServer | PAIR      |   55556 | N |
| ApiServer | SUB      |   55557 | N |
| ApiServer | PAIR      |   55558 | Y |

### 消息协议

消息由字符“|”来分割。例如

* 新市场单: o|账号|API|客户单号|MKT|AAPL STK SMART|100[|order_flag]
* 新限价单: o|账号|API|客户单号|LMT|AAPL STK SMART|100|170.00[|order_flag]
* 交易指令状态: s|账号|API|服务单号|客户单号|券商单号|下单状态
* 成交: f|账号|API|服务单号|客户单号|券商单号|成交编号|成交时间|股票代码|成交价格|成交数量
* 取消指令：c|账号|API|服务单号|客户单号|券商单号
* 分时数据：AAPL STK SMAR|时间|数据类型|价格|大小|深度
* 分时全数据: AAPL STK SMART|时间|3|价格|大小|1|买一|买一量|卖一|卖一量|未平仓量|开|高|低|昨收|涨停价|跌停价

以下是消息类型：

* k：分时数据
* p：最后的价格
* z：最后交易量
* o：新订单
* c：取消订单
* s：订单状态
* n：持仓查询
* m：一般信息
* b：K线
* h：历史数据
* e：测试消息

### 交易品代码

在EliteQuant中，一个交易品通过其完整代码**Full Symbol**来识别，完整代码由空格隔开的字符组成。一般模式是“本地代码 交易品类别 交易所 乘数”

* 股票：SPY STK SMART
* 期货：ESZ7 FUT GLOBEX 50
* 外汇：EUR.USD CASH IDEALPRO
* 外汇期货：6BU1 FUT GLOBELX
* 期权：GOOGL_140920P00535000 OPT SMART 100
* 期货期权：EWQ4_C1730 FOP GLOBEX 50

### 下单状态
``` cpp
enum OrderStatus {
		OS_NewBorn = 0,			// NewBorn
		OS_PendingSubmit = 1,
		OS_PendingCancel =2 ,
		OS_Submitted = 3,			// submitted
		OS_Acknowledged = 4,		// acknowledged
		OS_Canceled = 5,			// Canceled
		OS_Filled = 6,				// Filled
		OS_Inactive = 7,
		OS_PartiallyFilled = 8		// PartiallyFilled
	};

	enum OrderFlag {			// for CTP offset flag
		OF_OpenPosition = 0,
		OF_ClosePosition = 1,
		OF_CloseToday = 2,
		OF_CloseYesterday = 3
	};
```

### 代码结构

![代码结构](/resource/code_structure_cn.png?raw=true "代码结构")

## 开发计划

* QT 图形界面: 现在暂时是命令端执行；计划加入用户界面支持。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)