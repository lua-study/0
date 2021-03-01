# easyopen
一个简单易用的接口开放平台，平台封装了常用的参数校验、结果返回等功能，开发者只需实现业务代码即可。

easyopen的功能类似于[淘宝开放平台](http://open.taobao.com/docs/api.htm?spm=a219a.7629065.0.0.6cQDnQ&apiId=4)，它的所有接口只提供一个url，通过参数来区分不同业务。这样做的好处是接口url管理方便了，平台管理者只需维护好接口参数即可。由于参数的数量是可知的，这样可以在很大程度上进行封装。封装完后平台开发者只需要写业务代码，其它功能可以通过配置来完成。

得益于Java的注解功能以及Spring容器对bean的管理，我们的开放接口平台就这样产生了。

## 功能特点

- 开箱即用，写完业务代码直接启动服务即可使用，无需其它配置。
- 参数自动校验，支持国际化参数校验（JSR-303）。
- 校验功能和结果返回功能实现各自独立，方便自定义实现或扩展。
- 采用注解来定义接口，维护简单方便。
- 支持i18n国际化消息返回。
- 自动生成文档页面，类似swagger。
- 采用数字签名进行参数验证，签名算法见：easyopen\签名算法.txt。
- 采用appKey-secret形式接入平台，即需要给接入方提供一个appKey和secret。

## 结构图

![easyopen结构图](https://gitee.com/uploads/images/2018/0117/095712_1f70de95_332975.png "easyopen_arc.png")

## 文档页面

![文档](https://gitee.com/uploads/images/2018/0528/181649_50995938_332975.png "7.png")

## 示例

- 定义接口：

```
@Api(name = "goods.get")
public Goods getGoods(GoodsParam param) {
    Goods goods = new Goods();
    goods.setId(1L);
    goods.setGoods_name("苹果iPhoneX");
    goods.setPrice(new BigDecimal(8000));
    return goods;
}
```

- 请求数据：

```
{
  "name": "goods.get",
  "version": "",
  "app_key": "test",
  "data": "%7B%22goodsPrice%22%3A%22%22%2C%22goods_name%22%3A%22iphoneX%22%7D",
  "timestamp": "2018-03-22 13:48:58",
  "format": "json",
  "sign": "C946ACA5AC95B1790511764A10E675B7"
}
```

- 返回结果：

```
{
    "code":"0",
    "data":{
        "goods_name":"苹果iPhoneX",
        "id":1,
        "price":8000
    }
}
```

## 工程说明

- easyopen：easyopen核心代码
- easyopen-server：开放平台服务端（spring-boot），接口提供方
- easyopen-server2：基于springboot2,含有WebFlux例子
- easyopen-sdk：接口对应的开发包（可适用于Android），配合server使用
- easyopen-sdk-javascript：对应js的sdk
- static：文档静态资源
- index.html：文档首页，配合Pages功能使用

## 使用说明

1. 启动easyopen-server（业务代码在GoodsApi.java中）
2. 运行easyopen-sdk中的SdkTest.java

文档页面：http://localhost:8080/api/doc

## 开发文档

[easyopen开发文档](http://durcframework.gitee.io/easyopen)

离线版：浏览器打开index.html

## 实战项目

[easydoc](https://gitee.com/durcframework/easydoc):一个文档管理项目，采用markdown方式写作。

## 意见交流

Q群：328419269

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)