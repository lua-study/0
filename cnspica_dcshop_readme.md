


## App去中心化商城（Blockchain+Java+Vue版）

* 区块链合约基于ontology公链
* 前端基于开源vue

卖家，买家，专家

基于ontid去中心化权限体系

多专家签名产品共识结果，评估产品结果

产品上链，防串改，可溯源

交易基于ontology交易模型，信任可靠，交易记录永久保存


## 技术选型
### 一、后端使用java技术
 * springboot2.1.0.RELEASE
 * mybatis3.4
 * mysql5.1

###二、区块链基于ontology公链开发
* ontology-java-sdk：https://github.com/ontio/ontology-java-sdk
* ontid生成
* wallet钱包生成
* 合约调用： https://smartx.ont.io
* 开发文档：https://dev-docs.ont.io/
        
### 三、 前端使用技术
* Vue2.5.1


## 项目结构
~~~
dcshop-demo
|--block-demo 后台java代码 （待开发）
|--platform-vue app商城（待开发）
~~~


## 商城功能

* 会员系统

* 产品管理

* 专家审核

* 社交媒体

* 其他

### 目前实现功能
* 区块链合约基于ontology公链简单接口定义
* ontid生成
* wallet钱包生成
* 产品合约调用


## block-demo启动
* 安装ontology
https://ontio.github.io/documentation/install_zh.html
* 注册smartx
https://smartx.ont.io

* 启动springboot调试

## block-vue启动

* block-vue启动
* sudo npm install -g yarn
* sudo yarn install
* sudo yarn run dev
* 浏览器输入http://127.0.0.1:8080

* 如果chromedriver报错，执行下面
npm install chromedriver --chromedriver_cdnurl=http://cdn.npm.taobao.org/dist/chromedriver



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)