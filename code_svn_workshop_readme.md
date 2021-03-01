![Hirundapus logo](./docs/images/logo.png "Hirundapus logo") 
 
# 1.1 背景介绍
Hirundapus是一款为中小企业基于表结构生成业务代码controller、 service、 dao(mapper)、page的快速开发工具;  
对于单表的CRUD操作，不用写一行代码就能实现。 
 
基于Swagger2自动生成 RESTful 风格的API文档，生成系统操作日志；动态权限管理，基于DB的定时任务配置！
 
# 1.2 Hirundapus使用技术
- 基    础：  SpringBoot1.5.3 、Maven
- 数 据 层：  mybatis plus 2.1.6  #mybatis 增强工具包
- 权限控制：  Spring Security4
- 定时任务：  quartz-scheduler 2.3.0
- 日志处理：  logback
- 页面模板：  thymeleaf 
- 前端技术：  jQuery、layui2.3.0
- RESTful 文档生成：swagger2.7.0
  
# 1.3 工具使用文档
##  1.3.1 工程目录结构简介
![工程全貌](./docs/images/p1.png "工程全貌")
![base_common模块](./docs/images/p2.png "base_common模块")
![base_admin模块](./docs/images/p3.png "base_admin模块")

##  1.3.2 生成后台及前端页面代码
  该工具是基于数据库表设计生成后台及前端页面代码。
  
**【注意】：表结构有注释生成代码会更友好 ；** 
**【推荐】 表及表字段列名都添加注释**
```
  CREATE TABLE `t_user_leave` (
    `id` varchar(32) NOT NULL,
    `user_name` varchar(18) DEFAULT NULL COMMENT '用户名',
    `days` int(11) DEFAULT NULL,
    `status` varchar(64) DEFAULT NULL,
    PRIMARY KEY (`id`)
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='人员请假';  
```
  上面表结构： 没有注释字段列会获取字段列名作为页面显示名称;  

### 1.3.2.1 生成代码的配置文件  
  配置文件： resources/mybatis-plus-generator.properties    
  关于配置参数的说明：
```
    #Java文件输出目录
    output.dir=base_admin/src/main/java
    #mybatis mapper xml文件输出目录
    output.dir.mapper=base_admin/src/main/java/com/beone/admin/mapper/
    # page 页面文件输出目录
    output.dir.page=base_admin/src/main/resources/templates/
    #生成类文件的作者
    author=覃球球
    #数据库连接信息
    db.driverName=com.mysql.jdbc.Driver
    db.url=jdbc:mysql://localhost:3306/base_db?useUnicode=true&useSSL=false&characterEncoding=utf-8
    db.username=root
    db.password=123456
    
    #数据库前缀名
    table.prefix=t_,
    #需要生成的表，不配或为空则生成整个库中的所有表
    include.tables=t_user_leave
    #生成模块名
    module.name=admin
    #程序生成的包名(模块名的父目录)
    module.parent.pkg=com.beone
    #业务类继承的父类包名
    parent.package.name=com.base
    
    #生成页面的 UI 框架, 【暂只支持layui;】
    ui.template=layui
```  

### 1.3.2.2 基于配置生成代码
**1). 运行WorkshopMysqlGenerator类的main函数** ; 该方式页面代码生成目前仅支持隐藏域、文本框、时间控件
![生成代码效果图](./docs/images/r1.png "生成代码效果图")  
  
**2). 启动base_admin工程**
访问 : http://localhost:port/auto/config ; 选择实体类配置页面元素
![选择实体类配置页面](./docs/images/config1.png "选择实体类配置页面") 

点击 下一步  进入代码生成页面; 
~~黄色字体部分表示在生成页面中不出现的属性~~
![代码生成配置预览页面](./docs/images/config2.png "代码生成配置预览页面") 

  
## 1.3.3 工程SQL脚本
    sql脚本在工程docs/sql文件夹下
    
## 1.3.4 运行工程后，登录后台的超级管理员账号 
    账号: supervisor   密码: 123456
![后台效果图1](./docs/images/bg1.png "后台效果图1")    
![后台效果图2](./docs/images/bg2.png "后台效果图2")        
    
## 1.3.4 RESTful风格文档
   浏览器访问:   http://localhost:8080/contextPath/swagger-ui.html  

# 1.4 感谢
- 感谢[mybatis-plus](https://gitee.com/baomidou/mybatis-plus)团队
- 感谢[layui](https://www.layui.com/)团队

***
**QQ交流群**：908695401  

![支持一下](./docs/images/wx_workshop.jpg "Workshop")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)