## 安装

npm init
npm install lite-server


## token 编写及部署

安装openzeppelin-solidity
npm install openzeppelin-solidity

部署的时候进行解锁
personal.unlockAccount(eth.accounts[0],"");


truffle migrate


## 启动

因为provider 是使用的本地的geth节点，因此需要先启动geth：

```
geth --datadir testNet --dev --rpc --rpccorsdomain "http://localhost:3000" console
```

当然provider 也可以在app.js 中按自己的要求修改，参考文档 https://docs.ethers.io/ethers.js/html/api-providers.html

启动web程序：

> npm run dev


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)