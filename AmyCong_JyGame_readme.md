# JyGame
- ## unity 前端游戏框架！
1. 框架通过继承 MonoBehaviour 的 GameApp 启动和关闭。
2. 框架内有许多独立模块，比如：
    * 事件模块(负责事件的分发工作)
    * ui(独立的mvc构架)
    * 网络(独立的客户端tcp、http、udp连接等)
    * 数据(数据库、读表数据等)
    * 资源(热更新资源、加载、卸载等)
    * 脚本(Lua等热更新)
    * 时间(同步服务器时间)
    * 对象池(管理全局对象、视野管理等)
    * 日志(手机日志存储、上传云日志等)
    * AI(一般寻路 、 、FSM等)等。
3. 每个模块负责自己模块内的管理，模块跟随系统的生命周期。
    * 这样做的好处是：
        * 每个模块之间独立开发，更加容易维护和增加新模块。
        * 满足了程序设计的开闭原则。
4. 最后通过外观模式或者其他方法集合常用功能 。（用适配器模式适配出一套常用功能的接口，供实现时调用，这样实现时只需要调用适配器层的接口就可以了，而接口的底层实现则可以更改！）

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)