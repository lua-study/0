1、设置Go Libraries
就是设置当前的工作目录，或者理解成java的classpath也可以的
就是当前项目*.go文件所在的目录

2、
类型可以是基本类型，如：int、float、bool、string；结构化的（复合的），如：struct、array、slice、map、channel；只描述类型的行为的，如：interface。
结构化的类型没有真正的值，它使用 nil 作为默认值（在 Objective-C 中是 nil，在 Java 中是 null，在 C 和 C++ 中是NULL或 0）。值得注意的是，Go 语言中不存在类型继承。
函数也可以是一个确定的类型，就是以函数作为返回类型。这种类型的声明要写在函数名和可选的参数列表之后，例如：

func FunctionName (a typea, b typeb) typeFunc
你可以在函数体中的某处返回使用类型为 typeFunc 的变量 var：
return var
一个函数可以拥有多返回值，返回类型之间需要使用逗号分割，并使用小括号 () 将它们括起来，如：

func FunctionName (a typea, b typeb) (t1 type1, t2 type2)
示例： 函数 Atoi (第 4.7 节)：func Atoi(s string) (i int, err error)

返回的形式：

return var1, var2
这种多返回值一般用于判断某个函数是否执行成功（true/false）或与其它返回值一同返回错误消息（详见之后的并行赋值）。


3、Go 程序的执行（程序启动）顺序如下：

按顺序导入所有被 main 包引用的其它包，然后在每个包中执行如下流程：
如果该包又导入了其它的包，则从第一步开始递归执行，但是每个包只会被导入一次。
然后以相反的顺序在每个包中初始化常量和变量，如果该包含有 init 函数的话，则调用该函数。
在完成这一切之后，main 也执行同样的过程，最后调用 main 函数开始执行程序。





 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)