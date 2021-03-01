# Plugin.NET

Plugin.NET 目标是搞一个灵活的c#插件管理器(后面统称为**管理器**)。管理器使用反射(Reflect)技术，动态地加载dll类库（即插件）。在使用管理器的时候，会要求将一个`abstract`的类作为泛型参数传入，插件需要实现这个类的接口，而应用程序通过这个类里面的接口来调用插件。

> 项目目前都是下班回家后空闲时间在搞，所以进度有点慢。欢迎朋友们一起PR。 :relieved: :relieved: :relieved: 

## 运行环境
项目使用 .net 4.0 编写，自己随便改改代码就能用到.net2.0和.netcore上。

## 接口定义规范

说是接口，准确来说，应该是一个虚类，即由`abstract`修饰的类。这个类里面，包含插件必须实现和可选实现的两类接口(方法)。其中，必须实现的接口使用`abstract`修饰，可选实现的方法使用`virtual`修饰。示例如下：
```csharp
///  
/// 插件接口
///  
public abstract class PluginInterface
{
    ///  
    /// 插件名称
    ///  
    public abstract string Name { get; }

    ///  
    /// 插件版本
    ///  
    public abstract Version Version { get; }

    ///  
    /// 插件描述
    ///  
    public virtual string Description { get; }

    ///  
    /// 加载插件后调用，使用了 abstract 修饰，所以必须实现
    ///  
    public abstract void Load();

    ///  
    /// 第一个功能方法，使用了 virtual 修饰，所以可选实现
    ///  
    ///   
    public virtual string Method1()
    {
        return null;
    }

    ///  
    /// 第二个功能方法，使用了 virtual 修饰，所以可选实现
    ///  
    ///   
    ///   
    public virtual string Method2(string from)
    {
        return from;
    }
}
```

> 这里使用`virtual`来作为可选修饰是为了方便程序的接口升级，否则每接口有变化，插件都必须进行修改。


## 插件实现规范

插件所在项目需要引用接口所在的dll文件，在发布插件时不需要发布这个接口dll，但是如果有其它依赖的dll，需要一起发布。管理器会查找插件的类继承，插件中继承接口的类会通过无参数构造创建实例，然后交给程序使用，所以在实现插件时，必须提供一下无参的构造。

> 需要注意的是，管理器只会使用在插件中找到的第一个实现了接口的类，**其它的类将被忽略**。

## 管理器使用流程

1.  编写程序的接口类，在入口项目中引用这个接口
2.  在程序中引用**Plugin.NET.dll**
3.  初始化插件管理器
4.  绑定插件管理器的事件，各种事件提供了丰富的插件加载数据
5.  调用 `Load` 方法加载已经存在的所有插件，这个方法可以传入一个过滤器函数
6.  如果希望插件可以热加载，那么再调用 `Watch` 方法，以监视插件目录是否有新的插件放进去
7.  如果要停止热加载，那么就调用 `StopWatch` 以停止监视插件目录

## 示例

```csharp
class Program
{
    static void Main(string[] args)
    {
        // 使用接口来实例化插件管理器
        // 如果要对其它接口进行插件管理，
        // 那么可以创建另一个插件管理器的实例
        var pluginManager = new PluginManager ();

        // 处理插件管理器发出的事件
        pluginManager.OnAssemblyLoading += PluginManager_OnAssemblyLoading;
        pluginManager.OnAssemblyLoaded += PluginManager_OnAssemblyLoaded;
        pluginManager.OnError += PluginManager_OnError;
        pluginManager.OnInstanceCreating += PluginManager_OnInstanceCreating;
        pluginManager.OnInstanceCreated += PluginManager_OnInstanceCreated;

        // 加载插件目录下的所有插件
        pluginManager.Load();

        // 开始监视新放进目录的插件
        pluginManager.Watch();


        Console.WriteLine("正在监视插件目录变动，按`Enter`退出");
        Console.ReadLine();
    }

    private static void PluginManager_OnAssemblyLoading(object sender, PluginAssemblyLoadingArgs e)
    {
        Console.WriteLine($"准备从文件\"{e.FileName}\"加载程序集");
    }

    private static void PluginManager_OnAssemblyLoaded(object sender, PluginAssemblyLoadedArgs e)
    {
        Console.WriteLine($"从文件\"{e.FileName}\"加载程序集\"{e.Assembly}\"成功");
    }

    private static void PluginManager_OnInstanceCreating(object sender, PluginInstanceCreatingArgs e)
    {
        Console.WriteLine($"准备从程序集\"{e.Assembly}\"加载类型\"{e.Class}\"");
    }

    private static void PluginManager_OnInstanceCreated(object sender, PluginInstanceCreatedArgs  e)
    {
        var plugin = e.Instance;
        Console.WriteLine($"从程序集\"{e.Assembly}\"加载类型\"{e.Class}\"成功");
        Console.WriteLine($"插件名称: {plugin.Name}, 版本: {plugin.Version}");
        e.Instance.Load();
        Console.WriteLine("Method1:" + plugin.Method1());
        Console.WriteLine("Method2:" + plugin.Method2("啊呀哟"));
    }

    private static void PluginManager_OnError(object sender, PluginErrorEventArgs e)
    {
        switch (e.ErrorType)
        {
            case PluginNET.error.PluginErrorTypes.None:
                break;
            case PluginNET.error.PluginErrorTypes.InvalidDll:
                Console.WriteLine($"文件\"{e.FileName}\"不是有效有dll: {e.Exception}");
                break;
            case PluginNET.error.PluginErrorTypes.CannotLoadClassTypes:
                Console.WriteLine($"无法从文件\"{e.FileName}\"中加载类型: {e.Exception}");
                break;
            case PluginNET.error.PluginErrorTypes.ImplementionClassNotFound:
                Console.WriteLine($"在文件\"{e.FileName}\"中没有找到实现了指定接口的类");
                break;
            case PluginNET.error.PluginErrorTypes.IllegalClassDefinition:
                Console.WriteLine($"在文件\"{e.FileName}\"中找到了实现指定接口的类，但是其声明不是class或声明为abstract或不是public");
                break;
            case PluginNET.error.PluginErrorTypes.DefaultConstructorNotFound:
                Console.WriteLine($"在文件\"{e.FileName}\"中找到了实现指定接口的类，但未找到默认的无参构造函数");
                break;
            case PluginNET.error.PluginErrorTypes.InstanceCreateFailed:
                Console.WriteLine($"在文件\"{e.FileName}\"中找到了实现指定接口的类\"{e.ClassType}\"，但是创建实例时抛出了异常:{e.Exception}");
                break;
            case PluginNET.error.PluginErrorTypes.Unkown:
                Console.WriteLine("未知错误");
                break;
            default:
                break;
        }
    }
}
```

示例请看解决方案中的*test*目录，测试项目为*Plugin.NETTest*

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)