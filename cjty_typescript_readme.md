# typescript

### 介绍

typescript 学习
TypeScript最大的一个特点就是变量是强类型的，也就是说，在声明变量的时候，我们必须给他一个类型。比如：字符串、数字、布尔，枚举........ 
#### TypeScript中的数据类型有：

Undefined :
Number：数值类型;
string: 字符串类型;
Boolean: 布尔类型；
enum：枚举类型；
any: 任意类型，一个牛X的类型；
void：空类型；
Array: 数组类型;
Tuple: 元祖类型；
Null：空类型。

#### 开始骚操作

1. 安装 Node.js
    ```
    node -v
    npm -v
    ```
2. 安装 TypeScript 包
    ```
    npm install typescript -g
    tsc --version
    ```
3. 编写 HelloWorld 程序
> -  初始化项目：进入你的编程文件夹后，可以使用
    npm init -y
    来初始化项目，生成 package.json 文件。

> -   创建 tsconfig.json 文件，用代码创建在终端中输入
    tsc --init
    它是一个 TypeScript 项目的配置文件，可以通过读取它来设置 TypeScript 编译器的编译参数。

> -   安装@types/node,使用
    npm install @types/node --dev-save
    进行安装。这个主要是解决模块的声明文件问题。

> -   编写 HelloWorld.ts 文件，然后进行保存，代码如下
    var a:string = "HelloWorld"
    console.log(a)

> - 在Vscode的任务菜单(Terminal)下，打开运行生成任务(Run Build Task)，然后选择tsc：构建-tsconfig.json，这时候就会生成一个helloWorld.js文件

> PS：此处如果遇到  tsc: 无法加载文件 tsc.ps1，因为在此系统上禁止运行脚本。可参考链接：https://blog.csdn.net/weixin_41986726/article/details/103031141
---
解决方法：
> 以管理员方式打开powershell（https://jingyan.baidu.com/article/09ea3ede40cc2dc0aede392c.html）
运行命令：set-ExecutionPolicy RemoteSigned
出现：
执行策略更改
执行策略可帮助你防止执行不信任的脚本。更改执行策略可能会产生安全风险，如 https:/go.microsoft.com/fwlink/?LinkID=135170
中的 about_Execution_Policies 帮助主题所述。是否要更改执行策略?
[Y] 是(Y) [A] 全是(A) [N] 否(N) [L] 全否(L) [S] 暂停(S) [?] 帮助 (默认值为“N”): Y
即可

> - 在终端中输入node helloWorld.js就可以看到结果了。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)