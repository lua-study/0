# mybatis-generator-xplugin
收集了很多mybatis-generator的插件，都是自己项目中用到的，为了方面使用，会上传到中心maven库，凡是用了其他人的插件，都会说明，如有冒犯，请告知，立马删除。邮箱:tryer@vip.qq.com

当初就是因为引用不方便，所以建了这个工程，集合了很多好用的插件，当前版本0.0.1
```
 
     com.trytotry 
     mybatis-generator-xplugin 
     0.0.1 
 
```
## OverIsMergeablePlugin
在生产xml文件的时候，默认会追加方法，而不会覆盖重写，找了很多方法，终于找到这个有用的，谢谢作者  
原作者地址：https://my.oschina.net/u/137785/blog/736372  
引入插件
```
 
```
## SelectByColumnPlugin
自己写的方法，会生成selectByxxx的方法，方便查询
引入插件  
```
 
```
config中配置  
```
 
     
 
```
则对应TestMapper中生产方法
```
List  selectByName(String name);
```
## ModelEqualsPlugin
自己写的插件，在model中生成equals的重载方法，方便判断
引入插件：
```
 
```
config中配置，此时，equals将会判断字段id和name是否相等，相等则return true
```
 
     
 
```
## MySqlUpsertPlugin
生成upsert方法
原作者地址：https://github.com/beihaifeiwu/dolphin
引入插件（保留原作者包名）
```
 
```
Java Sample
```
Test test = new Test().setId(2).setName("123").setPrice(123d);
mapper.upsert(test);
```
对应生产sql
```
INSERT INTO test (id, NAME, price)
    VALUES (2, '123', 123) 
ON DUPLICATE KEY 
    UPDATE id = 1,
	NAME = '123',
	price = 123
```
## MinMaxPlugin
在mapper中增加min和max方法
原作者地址：https://github.com/oceanc/mybatis3-generator-plugins
引入插件（保留原作者包名）
```
 
```
config中配置
```
 
     
     
 
```
则对应生产Java代码
```
mapper.maxIdByExample(example);
mapper.minIdByExample(example);
mapper.maxPriceByExample(example);
mapper.minPriceByExample(example);
```
## SumSelectivePlugin
sum插件
原作者地址：https://github.com/oceanc/mybatis3-generator-plugins
引入插件（保留原作者包名）
```
 
 
 
```
则对应生产Java代码
```
example.sumPrice(); //注意要添加sum的字段
mapper.sumByExample(example);
```
## WhereSqlTextPlugin
自定义sql插件
原作者地址：https://github.com/oceanc/mybatis3-generator-plugins
引入插件（保留原作者包名）
```
 
 
```
则对应生产Java代码，addConditionSql中可以自定义sql
```
example.createCriteria().andIdEqualTo(1).addConditionSql("1=1");
```
## ModelSettersChainPlugin
model层可以连续set的插件
原作者地址：https://github.com/vsl1978/mybatis-generator-pluginsplus
引入插件（保留原作者包名）
```
 
```
则对应生产Java代码，你可以这样写
```
Test test = new Test().setId(2).setName("123").setPrice(123d);
mapper.upsert(test);
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)