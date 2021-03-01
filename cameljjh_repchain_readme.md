# RepChain
[RepChain文档](https://gitee.com/BTAJL/repchain/attach_files)   [单机多节点部署](https://iscas1-my.sharepoint.cn/:v:/g/personal/zhengls_iscas1_partner_onmschina_cn/EaghaEdYxndOm1f7H01RNVoBRqWm7v5kCFXUZ4QwVVP7Wg?e=fIa58e)   [多机多节点部署](https://iscas1-my.sharepoint.cn/:v:/g/personal/zhengls_iscas1_partner_onmschina_cn/Ebk4-kDPg25KjE-9oSBKTuEBwD9pTJeQAgal_AYquLPHzg?e=D9tQNF)

## 参考阅读
- [akka](https://akka.io/) ——系统内部模块采用akka actor实现
- [akka remoting security](http://doc.akka.io/docs/akka/current/scala/remoting.html) ——节点之间安全通信采用akka Remote支持的TLS
- [akka serialization](http://doc.akka.io/docs/akka/current/scala/serialization.html)——节点之间消息交互采用protobuf序列化
- [scalaPB](https://scalapb.github.io/)——从proto定义生成Scala类的工具
- [protobufjs](https://github.com/dcodeIO/ProtoBuf.js/)——在web端根据proto定义，反序列化protobuf字节流
- [swagger-scala](https://github.com/swagger-api/swagger-scala-module)——API支持Swagger UI
- [json4s](https://github.com/json4s/json4s)——在API层提供输入对象的json反序列化，返回结果的json序列化
- [d3.js-force layout](https://github.com/d3/d3-3.x-api-reference/blob/master/Force-Layout.md)——入／离网节点的自动布局
- [leveldb for java](https://github.com/dain/leveldb)——存取Blocks、Transactions索引
- [java security](http://docs.oracle.com/javase/8/docs/technotes/guides/security/index.html)——hash、签名、密钥对及证书管理均采用jdk内置方法

## 安装
- install [jdk8+](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
- install [Python](http://www.python.org/downloads/)
- install [Scala](https://www.scala-lang.org/download/)
- install [SBT](http://www.scala-sbt.org/release/docs/Setup.html)
- install [Scala IDE](http://scala-ide.org/)
- install [keystore-explorer](http://keystore-explorer.org/) ——用于生成密钥对的工具,非必须
- install [protobuf editor](https://github.com/Enide/polyglot-maven-editors)——编辑protobuf定义工具，非必须

## 分层架构
![RepChain分层架构图](https://images.gitee.com/uploads/images/2020/0115/170029_4e469133_1598833.png "分层架构图.png")
- 数据层：负责数据格式定义，数据结构采用Protocol Buffers定义文件，并以此为基础实现数据的交换、验证、存储、读取及检索
- 网络层：采用JDK内置的TLS实现，支持入网许可验证，在此基础上进行去中心化的gossip组网，网络传播支持P2P和Pub/Sub两种方式
- 共识层：完成区块的输入共识和输出共识。采用兼顾实时性和安全性的CFRD算法，既照顾到交易的实时性要求，又能在一定程度防止节点串通作弊；输入共识对入块的交易顺序达成一致，输出共识对交易顺序执行的结果达成一致
- 合约层：为合约执行提供上下文环境，支持合约的动态部署、运行时加载和编译执行
- API层：提供外部接口，允许第三方应用以Restful的形式与系统交互，并允许开发者通过Swagger UI进行在线测试。API层提供交易签名提交、区块和交易检索等基本功能
- 监控层：在区块链网络中收集事件/日志,并将其以Protocol Buffers的格式推送至Web端,以H5图形技术进行实时状态的可视化展示和日志回放

## 运行
- `git clone https://gitee.com/BTAJL/repchain.git`
下载项目到本地
- `sbt` 
在项目的根目录下下载项目依赖项，可以配置仓库或者使用阿里镜像
- `compile` 
编译成Protocol Buffer Scala类
- `eclipse` 
生成eclipse工程文件
- 打开 Scala IDE, File->Import->Existing Projects,导入项目
- 右键单击 rep.app.Repchain.scala,Run As->Scala Application(单机组网4个节点)
- 运行配置VM参数 -Dlogback.configurationFile=conf/logback.xml (使logback配置生效)
- 查看实时图 http://localhost:8081/web/g1.html
![实时状态图](https://images.gitee.com/uploads/images/2020/0114/174424_b02748a4_1598833.gif) 
- 查看API  http://localhost:8081/swagger/index.html
![Swagger-UI](https://images.gitee.com/uploads/images/2020/0114/165836_553469bc_1598833.png "swagger-ui.png")

## 修改配置
- 生成RepChain节点密钥对及信任证书列表（见[《RepChain开发者指南》](https://gitee.com/BTAJL/repchain/attach_files/235993/download) 2.1.5）
- 制作创世区块（见[《RepChain开发者指南》](https://gitee.com/BTAJL/repchain/attach_files/235993/download) 2.1.6）
- 调整系统配置参数（见[《RepChain开发者指南》](https://gitee.com/BTAJL/repchain/attach_files/235993/download) 2.1.7）

## 打包
- assembly 
打包成jar包，进行分布式部署 

## 示范应用
- [BAR](https://gitee.com/linkel/bar)(Base App of RepChain)：提供了通用的基础功能实现，区块链应用实施者既可以直接复用其提供的功能， 也可以在其源代码的基础上进行开发，快速开发自己的DAppp
- [SBR](https://gitee.com/JayTsang/bar)(Storage Based on RepChain)：基于BAR开发的可举证云存储应用示例
- [CRBB](https://gitee.com/linkel/CRBBV1.0)(Copyright Register Based on Blockchain)：基于RepChain的数字版权登记保护应用示例


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)