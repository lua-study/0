###项目简介：
基于StackExchange.Redis封装的RedisHelper.cs，包括String、List、Hash和ZSet等数据类型的增删改查等操作

`String`
```csharp
RedisHelper.StringSet("string", "hello world", 6, RedisFolderEnum.Folder1);
```
![String](http://git.oschina.net/uploads/images/2017/0210/160230_3b979feb_582292.png "String")

`List`
```csharp
RedisHelper.ListRightPush("list", student1, RedisFolderEnum.Folder2);
RedisHelper.ListRightPush("list", student2, RedisFolderEnum.Folder2);
RedisHelper.ListRightPush("list", student3, RedisFolderEnum.Folder2);
```
![List](http://git.oschina.net/uploads/images/2017/0210/160258_c018048d_582292.png "List")

`Hash`
```csharp
RedisHelper.HashSet ("hash", "h1", student1, RedisFolderEnum.Folder3, RedisDBEnum.One);
RedisHelper.HashSet ("hash", "h2", student2, RedisFolderEnum.Folder3, RedisDBEnum.One);
```
![Hash](http://git.oschina.net/uploads/images/2017/0210/160314_d5d970d8_582292.png "Hash")

`ZSet`
```csharp
RedisHelper.SortedSetAdd ("zsort", student1, 111, RedisFolderEnum.Folder3, RedisDBEnum.One);
RedisHelper.SortedSetAdd ("zsort", student2, 99, RedisFolderEnum.Folder3, RedisDBEnum.One);
RedisHelper.SortedSetAdd ("zsort", student3, 100, RedisFolderEnum.Folder3, RedisDBEnum.One);
RedisHelper.SortedSetAdd ("zsort", student4, 1, RedisFolderEnum.Folder3, RedisDBEnum.One);
```
![ZSet](http://git.oschina.net/uploads/images/2017/0210/160328_58ca3a42_582292.png "ZSet")

###其他：
`详细使用教程`：http://www.cnblogs.com/oppoic/p/6165581.html

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)