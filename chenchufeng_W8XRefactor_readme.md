# 简介

    系统的逻辑处理层主要通过javaparse库来进行生成抽象语法树，然后对抽象语法树进行分析和收集问题代码数据，
    最后发到对应的问题代码重构类进行重构。服务端用sprinboot来写的，导出jar即可运行。
#目录介绍

    core:代码处理模块
        |—————analysis代码分析模块
        |—————api接口
        |—————form
        |—————io 读取路径模块
        |—————model数据类模块
        |—————refactor代码重构模块
        |—————refer 引用重构模块
        |—————utils 工具模块
    web:web展示模块
        |—————Controller控制层（接收请求并处理）
        |—————Service服务层（处理请求的逻辑层）
        |—————Model数据类
        |—————WebApplication启动文件
     
#快速开始

    环境要求：JDK1.8
    windows系统的运行：    
    在jar包所在目录中，shift+鼠标右键，选择在此处打开窗口。
    在命令行中输入 java -jar web-0.0.1-SNAPSHOT.jar
    然后在浏览器中的地址中输入 http://localhost:8089/route/nofollow
    然后把项目的路径复制进文本框中，点击扫描项目代码就行了
#测试

    我们的测试用例对项目进行测试，然后有些代码的源码预览中会出现unfined.并带有红色下划线，
    但不会影响重构，只是界面展示有bug

#开发者

      github上的名字为 :
      Sodarose 
      bassnsmq
#讨论

     (1)考虑使用编译原理中的token流对jdt库进行替换
     （2）未来优化会进行局部多线程的优化，加快重构
     （3）现在的功能都是一个流程进行下来，考虑以后会把功能自主交闭开启，进行多样化的组合。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)