# JyGame
- ## 版本
unity 2017.3.1f1

- ## unity 前端游戏框架！
1. 框架通过继承 MonoBehaviour 的 GameApp 启动和关闭。
2. 框架内有许多独立模块，比如：
    * [事件模块](https://gitee.com/chenbojun/JyGame/tree/master/Assets/FrameworkCore/Modules/Event)(负责事件的分发工作) (已经完成)
    * [ui](https://gitee.com/chenbojun/JyGame/tree/master/Assets/FrameworkCore/Modules/UI)(独立的mvc构架) (基于UGUI的框架已经完成)
    * [网络](https://gitee.com/chenbojun/JyGame/tree/master/Assets/FrameworkCore/Modules/Network)(独立的客户端tcp、http、udp连接等)(基于protbuf3.6.1的网络架构已经完成)
    * [数据](https://gitee.com/chenbojun/JyGame/tree/master/Assets/FrameworkCore/Modules/Data)(数据库、读表数据等)
    * [资源](https://gitee.com/chenbojun/JyGame/tree/master/Assets/FrameworkCore/Modules/Res)(热更新资源、加载、卸载等) (assetbundle生成、加载、管理已经完成)
    * [脚本](https://gitee.com/chenbojun/JyGame/tree/master/Assets/FrameworkCore/Modules/Script)(Lua等热更新)
    * [时间](https://gitee.com/chenbojun/JyGame/tree/master/Assets/FrameworkCore/Modules/Time)(同步服务器时间)
    * [对象池](https://gitee.com/chenbojun/JyGame/tree/master/Assets/FrameworkCore/Modules/Object)(管理全局对象、视野管理等) (有限池、无限池已经完成)
    * [日志](https://gitee.com/chenbojun/JyGame/tree/master/Assets/FrameworkCore/Modules/Log)(手机日志存储、上传云日志等) (日志打印管理功能已经完成,存储和上传服务器还未完成)
    * [AI](https://gitee.com/chenbojun/JyGame/tree/master/Assets/FrameworkCore/Modules/AI)(一般寻路 、 、FSM等)等。
    * [战斗]新增模块，负责战斗整个模块的实现，基于MMORPG系统设计战斗模块，后续会把AI系统融到战斗模块中。(通过分层设计战斗模块的整体实现，战斗分为4-5个层。从上到下依次分为：
        * 1.世界环境信息层 
        * 2.更新决策层  
        * 3.更新请求层  
        * 4.行为层  
        * 5.补充层 )。
3. 每个模块负责自己模块内的管理，模块跟随系统的生命周期。
    * 这样做的好处是：
        * 每个模块之间独立开发，更加容易维护和增加新模块。
        * 满足程序设计的开闭原则。
        * 满足程序设计的单一职责。
        * 满足程序设计的接口隔离原则。
        * 满足程序设计的迪米特原则。
4. 最后通过外观模式或者其他方法集合常用功能 。
5. 希望有朋友一起开发这个项目，有想法的联系 QQ : 316231662。
6. 这个项目一直在维护，有问题的可以[Issue](https://gitee.com/chenbojun/JyGame/issues)，我会仔细查看，并且修改的。

7.重构中

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)