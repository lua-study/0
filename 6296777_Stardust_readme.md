#Stardust


Stardust是一个.net微服务架构的一个简单实现。


 [http://www.cnblogs.com/loogn/p/6664594.html](http://www.cnblogs.com/loogn/p/6664594.html) 

##Service:

```
public class User
{
    public string Name { get; set; }
}

//[StardustName("User")] //默认是类名，如果类名以Service结尾，会把Service去掉
public class UserService : IStardustService
{
    //[StardustName("hello")] //默认是方法名，可以StardustNameAttribute来自定义
    public string Hello(string name, int count = 1)
    {
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i   HelloAsync()
    {
        return new Task (() =>
        {
            return "Hello World";
        });
    }

    public List  UpdateUsers(List  list)
    {
        foreach (var user in list)
        {
            user.Name = "Updated:" + user.Name;
        }
        return list;
    }
}

```

##Client:
```
var client = new StardustClient("server1", "1.1");
var str = client.Invoke ("user", "hello", new { name = "Jack", count = 2 });
//var task=client.InvokeAsync ("user", "hello", new { name = "Jack", count = 2 }); // 或者异步调用

```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)