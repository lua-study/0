gJSON
======
gJSON是方便解析和生成json数据的golang包  
------
使用示例

```golang
obj0 := gJSON.ParseObject(`{"k0":"string","k1":true,"k2":false,"k3":null,"k4":123,"k5":1.1314,"k6":{},"k7":[]}`)
log.Println(obj0.AsString())
log.Println(obj0.GetString("k0"))
log.Println(obj0.GetBool("k1"))
log.Println(obj0.GetBool("k2"))
log.Println(obj0.GetString("k3"))
log.Println(obj0.GetInt("k4"))
log.Println(obj0.GetDouble("k5"))
log.Println(obj0.GetObject("k6").AsString())
log.Println(obj0.GetArray("k7").AsString())
```

```golang
arr0 := gJSON.ParseArray(`["string",true,false,null,123,1.1314,{},[]]`)
log.Println(arr0.AsString())
log.Println(arr0.GetString(0))
log.Println(arr0.GetBool(1))
log.Println(arr0.GetBool(2))
log.Println(arr0.GetString(3))
log.Println(arr0.GetInt(4))
log.Println(arr0.GetDouble(5))
log.Println(arr0.GetObject(6).AsString())
log.Println(arr0.GetArray(7).AsString())
```

```golang
obj0 := gJSON.NewObject()
obj0.SetString(`k0`, `string`)
obj0.SetBool(`k1`, true)
obj0.SetBool(`k2`, false)
obj0.SetNull(`k3`)
obj0.SetInt(`k4`, 123)
obj0.SetDouble(`k5`, 1.1314)
obj1 := gJSON.NewObject()
obj0.SetObject(`k6`, obj1)
arr1 := gJSON.NewArray()
obj0.SetArray(`k7`, arr1)
obj1.SetNull(`k00`)
arr1.AddBool(true)
log.Println(obj0.AsString())
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)