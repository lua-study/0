#ExcelUtil

ExcelUtil借助反射和POI对Excel读取,省略了以往读取Excel的繁琐步骤,调用ExcelUtil只需要2步,对,你没有看错,2步足以读取到Excel的内容.兼容03/07版Excel.
```
 
 
     net.oschina.likaixuan 
     excelutil 
     1.5.2 
 
```
```
调用步骤:   
1.定义需要读取的表头字段和表头对应的属性字段 
String keyValue ="手机名称:phoneName,颜色:color,售价:price";  
2.读取数据 
List  list =  ExcelUtil.readXls("C://test.xlsx",ExcelUtil.getMap(keyValue),"com.lkx.model.PhoneModel");
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)