Pond - 灵活，快速的web开发框架 （基于java 8)
====
Pond 由以下模块

* pond-common - 底层库，包括快速开发使用的工具和一些函数式编程特性。

```java  
Map  testMap = map.hashMap(new Object[][]{
            {1, "one"}, {2, "two"}, {3, "weee"}, {4, "weee"}
    });
_for(testMap).map((s) -> s + "_new").each((entry) -> echo(entry.getValue()));

for (int i = 0; i   (entry.getKey() > 50)).each(S::echo);
```  

* pond-core - 框架核心

> * IOC 容器。
  * 一套完整灵活的api
  * 嵌入式http服务器 (test)
  * 来自express.js的中间件设计，从此远离传统aop
  * 自带logger
  * 基于正则的路由
  * 采用SPI，方便扩展

```java  

    Pond app = Pond.init().debug();
    Router router = new Router();
    router.get("/add", (req, resp) -> resp.send("add"))
            .get("/del", (req, resp) -> resp.send("del"));

    app.get("/", (req, resp) -> {
        resp.send("root");
    }).get("/${id}",
            (req, resp) -> resp.send(req.param("id"))
    ).get("/${id}/text", (req, resp) -> {
        resp.send(S.dump(req));
    }).use("/user", router);

    app.listen(8080);
```
  
* pond-db - 数据库处理相关（默认提供mysql)

> * 简单的连接池
  * DB.fire 快速获取数据
  * Record 针对单表简单封装
  * RecordService 封装简单CURD
  
  
```java  

List  list =  DB.fire(this::createConnection,t ->
                                t.map(TestRecord.class,
                                "select * from t_crm_order"));
                                
echo(dump(_for(list).map(TestRecord::view).toList()));

```

    
###详情请参考项目内测试代码和注释
遇到坑了 ==>请联系 edwinyxc@gmail.com


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)