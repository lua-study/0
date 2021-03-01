### 运行于JavaScript环境下的TypeScript脚本解释器。微信小游戏代码热更新技术。
```
代码都有注释，结构也比较简单，主要目的还是学习和研究。
原理就是对字符串进行词法分析、语法分析、指令处理等。
其实就是实现了一个类似js的eval功能，只不过eval里面的参数是ts格式的代码。
超小的库，库文件经Uglify压缩后只有66kb。
QQ群：857485170
```
1. 可以直接在JavaScript的运行环境中运行TypeScript代码
2. 性能问题：一般游戏性能不会有问题。如果需要有高性能的需求，请把高性能的代码做成库文件，结尾有一个粗略的性能测试。
3. 代码体积问题，因为需要从服务器拉取代码，目前没有实现编译成字节码，暂时可以用jsmin先做简单的压缩。
4. 冷代码（原生的js代码）和热代码（可以热更新的ts代码）之间没有沙箱，可以互相任意调用、继承。
5. 不用担心字符串处理速度，因为只在第一次进行词法、语法分析。分析结束后会将ts的类生成原生的js对象（Function）。所以内存上也不用太担心。

egret_demo工程说明
1. 自带一个简单的游戏，发布插件（皮肤必须要commonjs2模式，因为exml也需要热更新）、资源包热更新（在Start.ts中zip下载、解压、缓存全部都实现了）、代码热更新（需自己部署服务器并在主文件的queryCode里面实现）等都已经实现。
2. 资源包热更新只需要使用命令egret publish --target wxgame，然后把项目目录父目录下面的带remote后缀下面的resource打包成zip即可实现资源热更新
3. 代码热更新在Main.ts里面有示例
4. 送审的时候请把热更新逻辑也编译成js，审核通过之后，当有新版本要发布的时候，服务器开关切换成热更新代码，同时资源包也打包成zip

cocos_demo工程说明
1. cocos_demo有一个最基础的动态执行代码的例子

laya引擎暂无demo

以下为未实现（即将实现16、7、15、9、1、13）：
1. lambda表达式方式的匿名函数，比如()=>{console.log(this)}
2. await/async、yield
3. 类型转换，比如``` obj```，建议用as代替
4. 泛型，比如```class A {}```
5. 正则（推荐用new RegExp）
6. 在构造函数中super之前的定义，比如var a=2;super();
7. 枚举、枚举自定义值
8. 接口
9. for of
10. 装饰器-@
11. 当父模块有多级时，获取父模块在runTIme.getContextValue中可能有问题，解决办法，尽量不用模块或者同模块内的调用写全，比如new test.Start()，而不是new Start()
12. 变量前最多只支持两个非操作，即：var a = !!"123";（一般这种写法是强制转换到布尔类型，三个及以上的非基本是不需要的）
13. 运行时的报错信息不正确
14. 编译成字节码
15. 用``（键盘1左边的那个）表示的字符串
16. import {A} from './B.ts'

示例：
```
qs.run(`
            class Start{
                public constructor() {
                    console.log('你好，世界！');
                }
            }
        `, 'Start', window);//如果把所有代码整合到一个文件中的话，则这个更加方便一点，如果代码文件碎片化，则用下面一种方式好一点
```
另一种方式：
```
var runTime = new qs.RunTime(window);//创建一个运行时对象
runTime.regedit(`class Test{public constructor(){console.log('你好，世界！')}}`);//注册Test类
runTime.regedit(`class Start{public constructor(){new Test()}}`);//注册Start类
new runTime.g.Start();//实例化Start类，部分情况下，直接new Start();也可以
```
3月26日新增只更新某方法、某类的Demo
```
具体实现在egret工程的UpdateFunction和UpdateClass里面。
```
推荐大家使用局部更新，而不是全部代码都走热更新。


性能测试对比： 
华为Mate20执行效率： 
![输入图片说明](https://images.gitee.com/uploads/images/2019/0216/204503_bd684190_326091.jpeg "移动设备执行效率.jpg") 
PC上运行Unity的三个热门热更新方案（scorpio、lua、cls）执行效率： 
![输入图片说明](https://images.gitee.com/uploads/images/2019/0216/204705_acb7cfb2_326091.jpeg "Unity热门热更新脚本执行效率.jpg") 

性能对比结果：
原生js对for循环是做了优化的，所以执行效率很高。大家可以通过循环一亿次，for循环不实现就可知道。
通过跟Unity的几个热门热更新对比来看，100万次计算在性能上是不弱的。不过仅仅是循环+计算并不能说明全部问题。性能测试也只是反映部分现象，不代表全部。
总体来说，跟Unity的热更新一样，比不上原生代码是肯定的。

写在最后：应大家的要求，仓促的先发一个先行版，说明也不完善，可能还有未知的BUG没有发现。不过满足一般的开发是没问题的。有能力的开发者可以先拿着玩玩。

因为在自主创业，公司事情太多，精力实在有限。还没特别多的时间来整合这个库。如有问题，请理解一下。等公司走上正轨，我一定会精心维护这个库的。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)