阅读目录：
1. 简介   
2. 下载mybatis plugin插件   
3. 安装mybatis plugin插件   
4. 启动并验证   
5. 说明   
---
1. 简介   
    mybatis plugin作为一款优秀的mybatis跳转插件，比起free mybatis plugin插件，显示更为好看，使用也方便，此次使用的mybatis plugin v2.9.2，完美兼容** IDEA 2017，2018.2（在这之后的版本未做测试） ** 亲测mac和windows皆有效，顺利从IDEA 2015的mybatis plugin v2.6.4过渡。   
特点：
```
    兼容IDEA终极版和社区版。   
    代码完成，语法高亮。   
    基于SQL语句上下文的智能SQL参数完成。   
    导航（跳转到符号，查找用法，重构）   
    引入自定义的“Mybatis参数”语言来支持Mybatis参数表达式。   
    生成Mapper XML，SQL语句，语句声明。   
    在IDEA中与配置的DataSource集成。   
    许多有用的代码检查与有益的快速修复。   
    许多有用的意图行动，使编写代码更容易。   
    OGNL支持。   
    注释支持。   
    Spring的支持。   
    Spring Boot支持。
```   
2. 下载mybatis plugin插件     
    地址：https://gitee.com/loubobooo/mybatis_plugin.git   
    两种方法：
    * 用git拉取   
    ``git clone https://gitee.com/loubobooo/mybatis_plugin.git``    
        * 打开``mybatis_plugin文件夹``，对``mybatis_plus文件夹``进行压缩成zip格式

    注：如果是用git拉取的话，需要用压缩工具，压缩成zip格式。   

    * 直接下载   
    ![](https://static.oschina.net/uploads/space/2017/1203/154926_s2Ue_3209432.png) 

    注：刚有人提醒，下载下来的zip是下面这种

    ![](https://static.oschina.net/uploads/space/2017/1203/164434_obuw_3209432.png)
    
    这时候文件和文件夹的路径发生了变化，会导致之后的安装不成功   

        --loubobooo-mybatis_plugin-master（这一层一定要去掉）   
            --mybatis_plus        
                --lib    
    解决办法：解压这个zip文件，找到mybatis_plus，并对mybatis_plus这个文件夹进行压缩成zip格式

3. 安装mybatis plugin插件   
    同样两种方法安装。   

    * 第一种适合windows平台（不要打开IDEA 2017）   

    第①步，打开我的电脑，找到路径C:\Users\Administrator\\.IntelliJIdea2017.2\\config\\plugins，这是我的电脑路径，你的应该是C:\\{用户}\\{USER}\\.IntelliJIdea{VERSION}\\config\\plugins   

    第②步，把下载或者拉取的mybatis_plus文件夹，是文件夹，是文件夹，重要的话说三遍！ 复制到该路径下    
 
    第③步，打开我的电脑，找到路径C:\Users\Administrator\\.IntelliJIdea2017.2\\options，这是笔者的电脑路径，你的应该是C:\\{用户}\\{USER}\\.IntelliJIdea{VERSION}\\config\\options，把刚下载的文件夹中的mybatis.xml复制到该文件夹下   
 

    * 第二种方法适合windows和mac平台   

    第①步，打开IDEA 2017，打开File -- Settings -- plugins -- install plugin from disk    
            ![](https://static.oschina.net/uploads/space/2017/1203/160437_R6Bk_3209432.png)   


     第②步，找到你刚才压缩的zip文件，是zip文件，是zip文件。名字应该是mybatis_plus.zip   

    注：据不少人反应，mac系统应该压缩成rar格式    

4. 启动并验证    
    重启IDEA 2017验证mybatis plugin插件，是否生效，如图:   

    ![](https://static.oschina.net/uploads/space/2017/1203/160756_6rTO_3209432.png)   

    效果：   

    ![](https://static.oschina.net/uploads/space/2017/1203/165246_GoUf_3209432.png)   
       

5. 说明   
    操作平台：windows 10 ，mac OS   

    mybatis plugin : v2.9.2   

针对IDEA2017以前的版本可能不适用，比如IDEA2015版本默认限制了最高版本为v2.6.x，不可安装此插件    
详情可以参照: https://my.oschina.net/u/3209432/blog/1584110

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)