ZeroPHP是个人开发的第一款PHP框架，遵循MVC架构思想，独立视图，模块，控制器开发。
数据库DB类则引入medoo，编写D函数单例DB类来操作数据库。

正式文档和使用文档将在后续编写并上传。
如果有能力则可以自行阅读框架源代码后使用。

视图引擎输出：

使用注释标签
{# 注释内容! #}
模板最终会被解析成PHP进而运算处理，所以务必使用注释标签进行注释；

使用普通变量标签
{$content}
用于直接echo变量。如果是数组与对象，请使用打印标签。

使用打印标签
{[$arr]}
用于打印数组与对象。

使用if isset判断标签
{if $var}
    var是真 
{else}
    var是假 
{/if}
{isset $var}
    var有值 
{else}
    var没有值 
{/isset}
业务逻辑均有模块处理 最后无非输出两个结果 真(有值 或者 非0) 假(没有值 或者 0)
那么判断结果 是否真假 是否有值,两个结果选择输出即可。

使用foreach遍历数组标签
{foreach key=k1 item=i1 from=$colors}
    {@i1}-{@k1} 
{/foreach}
其中$colors为assign输出的数组 key是键 item是值 分别输出给k1和i1(输出名称可更改)

使用引入模板标签
{include file="file"}
在当前页面引入公共视图模板。
例：{include file="file"}会引入APP->当前模块(Home)->视图模板目录(Tpl)->公共视图模板目录(Public)->file.html

使用系统变量标签
{$config.webname}
系统变量以xml格式存储于APP目录下的config目录中，以变量名和值成对组成，所有模块可用。

使用外部挂件widget标签
{W 'Window',['miaohaha'=>'yiwa','content' => '喵哈哈']}
在使用挂件标签前在 APP->当前模块(Home)->外部挂件目录(Widget) 中创建 挂件名Widget.class.php的 例如：WindowWidget.class.php
并且继承于Widget类重写invoke方法。在外部挂件目录中的Tpl目录里创建相应挂件名的模板 例如：windowWidget.html;
最终在你要使用外部挂件的模板中使用{W 'Window',['miaohaha'=>'yiwa','content' => '喵哈哈']}方法。具体参详后续文档。

框架目录结构：

    ├── App                                           #业务代码目录
    │   ├── admin                                    #业务模块目录
    │   ├── home
    │   │     ├──  Controller                       #业务控制器目录
    │   │     │     └── IndexController.class.php  #对应控制器文件
    │   │     ├──  Lib                              #第三方类目录
    │   │     ├──  Log                              #日志目录
    │   │     ├──  Model                            #业务模型目录
    │   │     ├──  Tpl                              #视图模板目录
    │   │     │    └── Public                      #公共视图模板目录
    │   │     │    └── index                       #对应控制器目录
    │   │     └──  View                             #解析视图目录
    │   │     └──  Widget                           #外部挂件目录
    │   │          └── Tpl                          #外部挂件视图模板目录
    │   └── config                                   #公共配置目录
    │          └──  profile.xml                      #公共配置文件
    ├── Public                                        #公共资源目录 放置 css js images html
    │   ├── admin                                    #对应模块
    │   └── Error                                    #公共错误资源
    │         └──  404/500.html
    │   └── Home
    │         └──  Index
    │              ├──   css
    │              ├──   js
    │              └──   images
    ├── ZeroPHP                                       #框架目录
    │   ├── core                                     #框架核心类目录
    │   │    ├──  CommonCore.class.php              #公共函数库
    │   │    ├──  ControllerCore.class.php          #控制器核心
    │   │    └──  DbCore.class.php                  #DB类核心
    │   │        ├──   LogCore.class.php            #日志核心
    │   │        ├──   ModelCore.class.php          #模型核心
    │   │        └──   ViewCore.class.php           #视图核心
    │   └── ZeroPHP.class.php                        #框架总控文件
    └── index.php                                     #入口文件


更新说明：
2016/3/16;
加入halt终止函数。
halt($str,bool),第一个参数 终止内容，第二个参数为布尔值，是否显示调用栈；
halt函数运行时，会将终止内容以fatal级别存入日志文件当中。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)