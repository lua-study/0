# QtFramework

## 介绍
积累Qt开发常用的通用代码，包括UI界面、数据库操作、权限管理、数据通信、日志管理、异常处理等常用模块的通用类及方式方法。

## 软件架构
### 软件架构说明

推荐使用Qt版本：5.4.1

建议不同功能的通用库代码建立不同的文件夹，文件夹命名：“lib_**”，如果代码库依赖第三方库，库同样放在该文件夹中。

建议通用库使用pri引入到QtFramework主工程中，并设计界面来调用及演示自己的通用库代码。如有其它必要可以单独上传自己的工程（如权限管理可能要设计较多界面来演示）。

####  通用代码库规范几点说明

#### 命名约束 

- 文件命名：文件名全部小写或下划线隔开，如mytestclass.h/my_test_class.h。

- 类命名：所有单词首字母大写，切不能包含下划线，如ClockBattery。

- 变量/函数命名：首单词小写字母开头，后续单词大写字母开头；为便于类成员变量和局部变量区分，类成员变量使用m_做前缀，如：

  ```C++
  int m_myValue；
  ```

- 枚举命名：枚举使用名词，单词都以大写开头，切第一个单词时Enum，如

  ```C++
  enum EnumMyType{
  EnumType1,
  EnumType2
  };
  ```

- 结构体命名：结构体名称每个单词大写字母开头，结构体成员首单词小写字母开头

  ```C++
  struct MyType{
    bool isMyType;
    int type;
  };
  ```

- 常量命名：全部使用大写，单词之间下划线分开，以能够明确表达语义为主。

- 总体命名规则：方法/参数/变量等使用拼音和英文结合，遵循驼峰命名法的基础上尽可能的表达出语义。


  #### 代码注释

  - 注释风格：要求代码注释量10-30%，不易理解的地方应添加注释。

  - 类注释：累的头文件顶部添加说明性注释，如

    ```
    /*******************************************
    *	Copyright(C), 2015-2025, HFDZ Technology.
    *
    *	Version:
    *
    *	Author:            
    *
    *	Date:
    *
    *	Description://类用途描述   
    *********************************************/
    ```

  - 函数注释：重要的函数应给出注释，如

    ```
    /*************************************************
    *
    *	Function:        // 函数名称
    *
    *	Description:    // 函数功能描述
    *
    *	Input:          // 输入参数说明，包括每个参数的作用、取值说明
    *
    *	Output:         // 对输出参数的说明
    *
    *	Return:         // 函数返回值的说明
    *
    *	Others:         // 其它说明
    *
    *************************************************/
    ```


  - 单行注释：变量，代码块，功能实现都可以添加单行注释。

#### 代码排版

  - 头文件包含：为增强可读性，引入头文件次序要求：C库头文件、C++库头文件、其他库头文件、项目内头文件。

- 任何二目、三目运算符左右两边都加一个空格。

- 合理使用空行，将语句适当分组，便于阅读。

- 较长语句必须分多行书写，如

  ```
  if ((taskOne   FETCH_HEAD
    * [new branch]      master     -> origin/master
   ```

8. 编码及修改工作(略)

9. 本地仓库的修改添加到暂存区，并提交 ；更新的描述请以自己姓名拼音为前缀

   ```
   92553@YW MINGW64 /e/[gitee.com] (master)
   $ git add .
   92553@YW MINGW64 /e/[gitee.com] (master)
   $ git commit -m"yw:readme.md文档更新"
   [master 818c22f] yw:readme.md文档更新
    1 file changed, 54 insertions(+), 11 deletions(-)
   ```

10. 下拉代码：用于检查更新和冲突

    ```
    92553@YW MINGW64 /e/[gitee.com] (master)
    $ git pull origin master
    From https://gitee.com/y925537341/QtFramework
     * branch            master     -> FETCH_HEAD
    Already up to date.
    ```

11. 推送代码：推送更新到远程库

    ```
    92553@YW MINGW64 /e/[gitee.com] (master)
    $ git push origin master
    Enumerating objects: 5, done.
    Counting objects: 100% (5/5), done.
    Delta compression using up to 8 threads
    Compressing objects: 100% (3/3), done.
    Writing objects: 100% (3/3), 1.13 KiB | 1.13 MiB/s, done.
    Total 3 (delta 2), reused 0 (delta 0)
    remote: Powered By Gitee.com
    To https://gitee.com/y925537341/QtFramework
       f3d88c4..818c22f  master -> master
    ```

12. 刷新代码仓库网页，可以看到内容已经同步更新。



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)