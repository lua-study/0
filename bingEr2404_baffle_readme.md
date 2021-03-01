# 简化版的项目

##  項目説明：
agent: http挡板
```
    运行AgentApplication
```
app: 后台应用 （dubbo动态注册服务）
```
    1. 先起个zookeeper，
    2. 运行DubboRegistry的main方法注册服务端，
    3. 运行dubboConsumer模块中ConsumerTest的main方法调用。
```
dubboConsumer: dubbo消费者测试用例
```
    使用参考app中第3步
```
dubboConsumer2: dubbo消费者springboot测试用例
socket: Socket服务器与客户端
```
    Server ： 运行main启动
    Client：  运行main测试
```
test: 测试代码,无用.

## 参考
```
http://ju.outofmemory.cn/entry/356692
https://testerhome.com/topics/7908
https://blog.csdn.net/qq_30051265/article/details/82776395
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)