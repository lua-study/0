# confront
这是一个基于机器学习和大数据的决策对抗系统

### 使用到了以下技术
* 前端
    * 界面
        * JQuery
        * BootStrap
    * 数据可视化
        * ECharts
        * 高德地图和百度地图（当然我使用的是自己的坐标，保存在sql文件之中）

* 后端
    * SpringMVC
    * Spring
    * Mybatis
    * Logback
    * 使用Maven构建项目

* 数据库
    * Mysql

* 算法（对打击做仿真数据存入数据库）
    * 机器学习
    * 深度学习

### 项目构建

* 数据库文件(alphaalgorithm.sql)在项目sql文件夹中
    
* 导入sql文件到mysql中，修改项目中datasource.properties文件

    ```properties
    db.url = jdbc:mysql://数据库ip:3306/库名?characterEncoding=utf-8
    db.username = 数据库账号
    db.password = 数据库密码
    ```
    
* 配置Tomcat

    * 找到Tomcat安装目录下conf文件夹下的web.xml文件，在如下位置，添加如下代码
    
    ```xml
     
       jsp 
       org.apache.jasper.servlet.JspServlet 
     
       fork 
       false 
     
     
       xpoweredBy 
       false 
     
     
       enablePooling 
       false 
     
     
       mappedfile 
       false 
     
       3 
     
    ```
    
* 项目编译命令

    ```bash
    mvn clean package -Dmaven.test.skip=true
    ```

* 部署

    * 进入target/目录
    
    * 将打包好的war放入Tomcat中的webapp下

    * 启动Tomcat

### 功能介绍
* 大数据技术

    * 大数据感知和获取：用于展示红方导弹各项参数细节、各国导弹情况，对军事信息对抗进行简要介绍。
    
    * 导弹信息:
    显示出导弹库中的所有导弹细节。
    
    * 新增导弹信息:
    向数据库中新添加导弹信息。
    
    * 智能系统面板：
    用图表的方式对比各类导弹的参数。
    
* 类人智能系统

    * 知识发现：
    用于介绍该项目中演示对抗的各类机器学习算法。
    
    * 深度学习：
    用于介绍个项目中演示对抗的各类深度学习算法。
    
    * 规则库：
    用于展示导弹打击以及防守时的准则。
    
    * 新增打击规则：
    用于新增导弹的打击细则。
    
    * 新增防御规则：
    用于新增导弹的防御细则。
    
    * 模型库：
    用于展示经过仿真计算后打击预测的结果，并与真实结果进行对比。
    
* 类人智能决策支撑技术

   * 问题处理：
   模拟收到对战命令，并转向决策方案。
   
   * 交互系统：
   显示决策方案细则，并进行方案调整（修改各阵营的导弹数量）。
   
   * 对抗军演决策：
   展示双方阵营的坐标位置、各阵营的导弹类型及数量。
   
   * 对抗军演：
   用于展示演示对抗的详细过程。
   
   * 智能系统面板：
   用于展示对抗完双方阵营的各项细则。



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)