## 工程结构
springboot、mongodb

## 工程目标
实现企业微信的openapi接口

## token
不同的模块有不同的token，需要单独调用接口获取。
## mongodb
* cd /usr/local/mongodb/bin
* ./mongod -dbpath=/Users/junzhang/data/mongo/db

## mongodb操作注意点：
* 插入重复数据
> insert: 若新增数据的主键已经存在，则会抛 org.springframework.dao.DuplicateKeyException 异常提示主键重复，不保存当前数据。
> save: 若新增数据的主键已经存在，则会对当前已经存在的数据进行修改操作。


* 批操作
> insert: 可以一次性插入一整个列表，而不用进行遍历操作，效率相对较高
> save: 需要遍历列表，进行一个个的插入


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)