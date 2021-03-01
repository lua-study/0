# jssdk 文档

## 在jquery之后引入jssdk.js

```
  
  
```

## API
### MD5加密
```
jssdk.md5(string, key, raw)

test:
jssdk.md5('123456');

result:
e10adc3949ba59abbe56e057f20f883e

```

### signJson 对json进行签名

`secret 可选，默认是 FUt@i2017`

```
jssdk.signJson(inJson, secret)

test:
jssdk.signJson({
    name:'jay',
    age:18,
    gender:'M'
});

result:
{name: "jay", age: 18, gender: "M", signature: "722715043ED9BB3C6C3FDB30594A3274"}
```

### HTTP AJAX

### http.get 跨域JSON GET请求
* `如果发现 data.accessToken ，则会将accessToken自动存储，下次再请求会带上header`
* `如果发现 resCode 为 601-01 ，则跳转到首页`

```
var res = jssdk.http.get(url, [jsonParams])

test:
var res = jssdk.http.get(url, jsonParams);

result:
{
    resCode:200
}
```

### http.post 跨域JSON POST请求
* `如果发现 data.accessToken ，则会将accessToken自动存储，下次再请求会带上header`
* `如果发现 resCode 为 601-01 ，则跳转到首页`

```
var res = jssdk.http.post(url, [jsonParams])

test:
var res = jssdk.http.post(url, jsonParams);

result:
{
    resCode:200
}
```

## store 本地存储
```
//存储数据
jssdk.store.set(key, data[, overwrite]);

//获取数据
jssdk.store.get(key[, alt]);

//删除数据
jssdk.store.remove(key);

//清空所有数据
jssdk.store.clear();

//返回所有key的数组
jssdk.keys();

//循环遍历，返回false结束遍历
jssdk.forEach(callback);

//判断是否存在返回true/false
jssdk.has(key); 
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)