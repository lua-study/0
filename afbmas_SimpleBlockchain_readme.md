# SimpleBlockchain
区块链入门

## 执行
```
java -jar web-0.0.2-SNAPSHOT.jar
```

## application.yml 配置

```
server:
  port: 6060
blockchain:
  node: 47.52.157.27:6060 # 请配置为节点机器的访问地址
  node-server: 47.52.157.27:6060 # 请配置为节点注册机器的地址，只要在线的节点（任一节点）即可
```

## 说明

1、每个节点均可做为节点服务器，用于其他节点的注册功能，以便于区块数据同步

2、执行 jar 包运行 web 程序，通过访问 ```http://localhost:8080``` ，可以查看区块数据，通过配置 application.yml ，blockchain.node-server 设置节点注册服务器，用于同步区块数据

3、通过访问 ```http://localhost:8080/?data=这是数据，添加区块```

## 演示地址

> 查看数据
```http://47.52.157.27:6060/```

> 添加区块数据
```http://47.52.157.27:6060/?data=这是添加的区块数据```

您的节点注册服务器可以直接使用  ```47.52.157.27:6060```

## Todo

[x] 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)