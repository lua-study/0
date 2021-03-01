# LoadJS 

> LoadJS 是一个能够逐步加载JS的工具,方便声明依赖

当前稳定版本为1.1版本 master 分支为当前稳定版本

1.1版本的说明
动态加载JS文件
使用方法如下:
1.初始化为全局变量
```
G_LoadJS=new LoadJS({'base':'/assets/js/'});

```
2.加载所需文件
```
        let list=[
                'Extend/jquery/2.2.4/jquery.min.js',
                'Start.js'
        ];
        //先加载 jquery Start 方法
        G_RequireJS.all(list);

```
list 是所需加载文件列表 
G_RequireJS.all();
方法为加载所有文件,两个参数 
第一个为文件列表 
第二个为本次加载操作的名字,可以为空,为空时不能为本次加载设置后置操作!
3.设置加载后置操作
```
let list2=[

    'Extend/Events.js',
    'Extend/WSocket.js',
    'Function/function.js',
    'Function/setInterval.js',
    'Service/Ping.js',
    'Service/Receipt.js'
];
G_RequireJS.all(list2,'Start');
G_RequireJS.ready.Start=function(){
    //这是书写你的后置操作业务代码!
}

```

G_RequireJS.ready这个是后置操作储存属性
.Start 为本次加载的名字



 **初始化配置格式:** 

```
let $config={
    'base':'/assets/js/',
    'modules':{
        'jquery':{
            'Require_base':false,//从base路径加载 默认为 true
            'src':'//cdn.bootcss.com/jquery/3.1.1/jquery.min.js'
        },
        'jquery1':{
            'src':'/jquery/1.9/jquery.min.js'
        },
    }

};

```
如以上代码 
base为js文件的相对URL路径 可以为'http://XX'的类型,不进行检测

modules为模块定义
    Require_base 为是否前加base路径 
    src 就是路径

如果模块没有定义 也可以使用G_RequireJS.all(list);进行加载 但是要传入相对于 base 的路径





 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)