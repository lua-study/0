
# Mini CUnitTest

## 简介

### mini单元测试框架主要用于C语言单元测试
>* **便捷性** ：本框架主要关联文件只有一个TEST.c所以文件更加轻便，搭建框架更加快速
>* **多功能** ：且支持功能繁多，可以测试函数性能，展示覆盖率，对于内存泄漏也有侦查
>* **易展示** ：分析结果是基于网页展示，相对于其他的的单元测试框架，这个更加直观，也易于理解
>* **易使用** ：使用便捷， UnitTest.py文件放入到待测试源码的下，简单的设置就可以完成



### 功能
>* 支持侦查测试的模块是否出现内存泄漏，并展示出来（仅支持linux，不支持mac）
>* 支持编译时候段错误侦查定位
>* 每个suite展示基本的 测试数 测试错误数，测试的时间
>* 每个suite里展示成功或者失败的结果 以及出错时候出错的所在case
>* 支持展示覆盖率 语句覆盖率 分支覆盖率 条件覆盖率 函数覆盖率
>* 支持通过代码形式查看覆盖率已经函数调用次数等
>* 支持函数性能，包括函数执行所需时间，函数被调用次数等性能(仅支持linux)
>* 支持环境 linux 嵌入式 mac(mac函数性能的功能和内存泄漏功能仍暂未支持)



### UintTest.py命令
>* **-h** 展示所有支持的命令  
        ```
        [例子: python UnitTest.py -h ]
        ```
>* **-a** 配置好UnitTest.py后，自动编译出test文件 
        ```
        [例子: python UnitTest.py -a ]
        ```
>* **-e** 配置好UnitTest.py后，编译出ResultsFile文件，然后将UnitTest.py 和 ResultsFile 放入到嵌入式系统中执行 
        ```
        [例子: python UnitTest.py -e ResultsFile ]
        ```
>* **-m** 配置好UnitTest.py后，使用Makefile编译出ResultsFile文件 然后执行UnitTest.py  
        ```
        [例子: python UnitTest.py -m Makefile ResultsFile ]
        ```



### 展示
#### 测试报告页面
![image](https://git.oschina.net/dcp_483/minicunittest/raw/master/png/index.gif)

#### 覆盖率页面
![image](https://git.oschina.net/dcp_483/minicunittest/raw/master/png/performance.gif)


### 函数性能页面
![image](https://git.oschina.net/dcp_483/minicunittest/raw/master/png/coverage.gif)




### 使用方法
#### 文件目录关系图
![image](https://git.oschina.net/dcp_483/minicunittest/raw/master//png/relation.png)

1.关联TEST.c文件
>* 使用-e -m 模式时候 将TEST.c文件关联到makefile里面

2.使用TEST.c的测试套件搭建测试用例

3.放置UnitTest.py
>* 将UnitTest.py放在测试模块目录下

4.配置UnitTest.py
>* 将 UnitPath="./" 修改为单元测试目录所在路径 
        ```
        [例如:UnitPath="/中间目录/src/ 以/结尾"]
        ```
>* 将 FilePath="./"  修改为待测试文件目录所在路径 
        ```
        [例如:UnitPath="/中间目录/xxx/  以/结尾"]
        ```

5.配置UnitTest.py
>* -a模式 这个模式自动进行gcc编译，将TestFile = ["TEST.c"]; 这句中添加所需要测试的文件, GccFile =["test_TEST.c"]添加编译关联程序
        ```
        (例如:TestFile =["aaa/TestingA.c", "aaa/TestingB.c", "bbb/Tmp.c"] )
        ```
>* -e模式 将TestFile = ["test_TEST.c"]; 这句中添加需要测试的文件，具体使用和-a模式一样。然后将src文件UnitTest.py，以及待测试文件，执行文件放入到嵌入式系统中，按照上面的图示关系，然后执行
        ```
        UnitTest.py -e /中间目录/xxx/Resultfile
        ```

>* -m模式 将TestFile = ["test_TEST.c"]; 这句中添加需要测试的文件，具体使用和-a模式一样。按照上面的图示关系，执行      
        ```
        UnitTest.py -m /中间目录/xxx/makefile /中间目录/xxx/Resultfile
        ```
        ```
        [makefile的gcc当中要加入编译参数 -fprofile-arcs -ftest-coverage -pg]
        ```

6.执行UnitTest.py



### 问题



### 联系
* **当出现问题以及bug时欢迎联系 邮箱:garsonzhang@foxmail.com**




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)