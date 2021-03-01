# sklearn_he

#### 项目介绍
https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.Ridge.html#sklearn.linear_model.Ridge 学习使用

#### 软件架构
软件架构说明


#### 安装教程

1. xxxx
2. xxxx
3. xxxx

#### 使用说明

1. xxxx
2. xxxx
3. xxxx

#### 参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


#### 码云特技

1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

#### 一、__init__.py文件

原来在python模块的每一个包中，都有一个__init__.py文件（这个文件定义了包的属性和方法）然后是一些模块文件和子目录，假如子目录中也有 __init__.py 那么它就是这个包的子包了。当你将一个包作为模块导入（比如从 xml 导入 dom ）的时候，实际上导入了它的 __init__.py 文件。

一个包是一个带有特殊文件 __init__.py 的目录。__init__.py 文件定义了包的属性和方法。其实它可以什么也不定义；可以只是一个空文件，但是必须存在。如果 __init__.py 不存在，这个目录就仅仅是一个目录，而不是一个包，它就不能被导入或者包含其它的模块和嵌套包。

在python中， module(也即python的模块)是一个单独的文件来实现的，要吧是py文件，或者pyc文件，甚至是C扩展的dll文件。而对于package, Python使用了文件夹来实现它，可以说，一个文件夹就是一个package,里面容纳了一些py、pyc或dll文件，这种方式就是把module聚合成一个package的具体实现

发现在引入package的过程中，init.py会运行，因此，如果某些变量或方法需要常驻内存，可以将它们写入init.py文件中。

__init__.py 中还有一个重要的变量，叫做 __all__。我们有时会使出一招“全部导入”，也就是这样：

from PackageName import *
这时 import 就会把注册在包 __init__.py 文件中 __all__ 列表中的子模块和子包导入到当前作用域中来。比如：

#####文件 __init__.py

__all__ = ["Module1", "Module2", "subPackage1", "subPackage2"]

#### 二、__init__函数

父类A
```
1 class A(object):
2     def __init__(self, name):
3         self.name=name
4         print "name:", self.name
5     def getName(self):
6         return 'A ' + self.name
```

    1.子类不重写__init__，实例化子类时，会自动调用父类定义的__init__子类B继承父类A

```
1 class B(A):
2     def getName(self):
3         return 'B '+self.name
4  
5 if __name__=='__main__':
6     b=B('hello')
7     print b.getName()
```
输入结果为：
```
name: hello
B hello
```

     2.子类重写了__init__时，实例化子类，就不会调用父类已经定义的__init__方法
     3.子类为了能使用或扩展父类的行为，最好显示调用父类的__init__方法

 class 子类：

     def __init__(self,参数) :

            super(子类,self).__init__(参数)  #执行父类的__init__方法

```
 1 class A(object):
 2     def __init__(self, name):
 3         self.name=name
 4         print "name:", self.name
 5     def getName(self):
 6         return 'A ' + self.name
 7 
 8 class B(A):
 9     def __init__(self, name):
10         super(B, self).__init__(name)
11         print "hi"
12         self.name =  name
13     def getName(self):
14         return 'B '+self.name
15 
16 if __name__=='__main__':
17     b=B('hello')
18     print b.getName()
```
输出结果：
```
name: hello
hi
B hello
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)