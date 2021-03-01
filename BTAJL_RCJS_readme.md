## RCJS

### 项目介绍
RepChain Client library for JavaScript，本项目是采用javascript实现的，用于DApp(Decentralized)与[RepChain](https://gitee.com/BTAJL/repchain)区块链网络之间的Connector。可作为开发DApp of RepChain的SDK。

RCJS主要对RepChain提供的Websocket API，以及Restful API进行了封装，利用RCJS可较为方便地使DApp与RepChain进行交互。

RCJS帮助DApp开发者更容易地实现以下功能：
- 与RepChain的区块链数据同步：支持订阅RepChain出块事件Event获取区块数据，以及通过Restful API主动获取区块数据；
- 构造RepChain签名交易：提供与RepChain一致的区块链交易内容的构造和签名功能;
- 提交RepChain签名交易：支持向RepChain区块链网络提交已构造的签名交易；
- 加密相关功能：
  + 生成非对称密钥对：支持RSA与ECC算法
  + 导出/导入密钥：支持生成/解析PEM格式公钥或私钥；
  + 生成X509证书；
  + 生成自签名X509证书；
  + 导出/导入X509证书:支持生成/解析PEM格式证书信息

### 使用说明
#### 安装 
```bash
yarn add rclink
``` 
或 
```bash
npm i --save rclink
```
#### API
API文档参考[这里](http://jaytsang.gitee.io/rcnodeapi/)

### 开发教程

#### 安装依赖
1. 安装node.js和yarn
2. `yarn install`

#### 使用说明
1. 本机多节点方式启动RepChain组网
2. 生成与非es6标准兼容的生产代码: `yarn build`
3. 运行测试用例：
    - `yarn test:node` node环境下运行测试用例
    - `yarn test:browser` browser环境下运行测试用例
    - `yarn test` 在node与browser环境下分别运行测试用例
>>Note: 在test/testEnvConfig.js中可修改待测试的目标代码: testEnv="dev"(表示测试位于src/下的开发代码)；testEnv="production"(表示测试位于lib/下的生产代码)
4. 支持VSCode下的test调试




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)