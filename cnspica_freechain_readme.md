# freechain
Freechain - 一个简单的区块链实现，包含区块链的一些基础特性，如去中心化，P2P通讯，交易， 挖矿，共识算法等

### Quick start
```
git clone https://github.com/aaronrao/freechain.git
cd freechain
mvn clean install
java -jar freechain.jar 5000
java -jar freechain.jar 5001

或直接运行启动主类Main启动两个P2P节点(5000端口和5001端口)，启动需带端口参数

```


### HTTP API

- 查询区块链

  ```
  curl http://localhost:5000/chain

  ```
- 挖矿

  ```
  curl http://localhost:5000/mine

  ```

- 交易

  ```
  curl -H "Content-type:application/json" --data 
  '{"sender": "d4e44223434sdfdgerewfd3fefe9dfe","recipient": "45adiy5grt4544sdfdg454efe54dssq5","amount": 1}' 
  http://localhost:5000/transactions/new

  ```

- 节点注册

  ```
  curl -H "Content-type:application/json" --data '{"urls" : "localhost:5000,..."}' http://localhost:5001/peers/register

  ```

- 替换共识长链

  ```
  curl http://localhost:5001/peers/resolve
  ```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)