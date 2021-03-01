MyBatis Log Plugin
==============================
![MyBatisLogPlugin.gif](https://raw.githubusercontent.com/kookob/mybatis-log-plugin/master/snapshot/MyBatisLogPlugin.gif)

**English Introduction**
---
This is a plugin for IntelliJ IDEA that restore the mybatis generate sql to original whole sql. 
It will generate sql statements with replace ? to the really param value. 
Through the "Tools -> MyBatis Log Plugin" menu you can tail the sql log. 
You can selected the "Filter" button on the left to filter the contents don't wanna display. 
You can selected the "Format Sql" button on the left to format the generate sql statements. 
**Prerequisite: sql log must contain "Preparing:" and "Parameters:"** 

The left buttons function: 

* Filter: Filter setting
* Rerun: Rerun this plugin
* Stop: Stop output the sql log
* Format Sql: Format the **subsequent** sql statements
* Close: Close this plugin window

**Support Format**
---
Support the mybatis's output format below: 


`2016-11-11 16:46:29.316 DEBUG selectSql1 -  ==>  Preparing: select * from t_table where name = ?`
`2016-11-11 16:46:29.343 DEBUG selectSql1 -  ==> Parameters: hello(String)`

Use "Preparing:" and "Parameters:" characters to split the log sql. 
And it will output the whole sql: 
`select * from t_table where name = 'hello';` 

**Download Plugin**
---
[mybatis-log-plugin.jar](https://plugins.jetbrains.com/plugin/10065-mybatis-log-plugin "Download Plugin")


---


**中文介绍**
---
这是一个Intellij的插件，主要作用是把mybatis生成的PreparedStatement语句恢复成原始完整的sql语句。 
它将用真实的参数值替换PreparedStatement语句的问号占位符。 
通过 "Tools -> MyBatis Log Plugin" 这个菜单可以实时输出sql日志。 
点击窗口左边的 "Filter" 按钮，可以过滤不想要输出的sql语句。 
点击窗口左边的 "Format Sql" 按钮，可以格式化输出的sql语句。 
**前提条件：输出的sql日志必须包含"Preparing:"和"Parameters:"才能正常解析。** 

左边几个按钮的作用： 

* Filter: 过滤语句配置
* Rerun: 重新启动
* Stop: 停止输出
* Format Sql: 格式化**后续**输出的Sql语句
* Close: 关闭该窗口

**支持格式**
---
支持mybatis的输出格式如下： 

`2016-11-11 16:46:29.316 DEBUG selectSql1 -  ==>  Preparing: select * from t_table where name = ?`
`2016-11-11 16:46:29.343 DEBUG selectSql1 -  ==> Parameters: hello(String)`

以 "Preparing:" 和 "Parameters:" 作为分割符进行解析。 
接着输出的完成sql语句如下： 
`select * from t_table where name = 'hello';` 

**插件下载**
---
[mybatis-log-plugin.jar](https://plugins.jetbrains.com/plugin/10065-mybatis-log-plugin "插件下载")

**项目地址**
---
 

**参考列表**
---
Reference and copy some code from below list: 
   
  
  



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)