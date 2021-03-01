# HutHelper - 工大助手
[![Build Status](https://travis-ci.com/isnine/HutHelper.svg?branch=master)](https://travis-ci.com/isnine/HutHelper)
![](https://img.shields.io/badge/lanuage-Objective--C-brightgreen.svg)
![](https://img.shields.io/badge/license-apache-green.svg)
# Description
- 工大助手是湖南工业大学计算机学院实验室为工大学子开发的一款校园App。
- 目前iOS端用户量4000人左右，Android端用户9000人左右。Web端日浏览量在3W左右。 


# Platform
```
x64 Linux
Java version 1.8 
Maven vsersion 3.6.3
Redis version 5.0.7
MySQL  8.0.13
```         

# Usage
```
[server]  
$ ./redis-server
$ mysql -u*** -p
$ setsid java -jar api.jar  
```

# Frame
```
.
	├── IService:service接口 
	├── RunnableImpl:多线程实现类
	├── ServiceImpl:service实现类    
	├── aop:aop  
	├── main：Main启动类     
 	├── cache：缓存模块      
	├── config：配置类
	├── dao：数据库连接
	├── mapper：mapper接口    
 	├── utils：相关工具类  
	├── interceptor：拦截器   
	├── entity：实体类        
	├── fly：异步文件上传服务器      
	├── templates:动态页面资源
	└── static：静态资源
	└── JSON:接口数据
```

## Features
- [x] 成绩查询
- [x] 考试查询
- [x] 电费查询
- [x] 网上作业
- [x] 二手市场
- [x] 校园说说
- [x] 实验课表
- [x] 失物招领
- [x] 视频专栏
- [x] 图书馆
- [x] 校历  
- [x] 社团活动
# Screenshot
![start-1](https://images.gitee.com/uploads/images/2019/1221/092117_cffa038d_1755294.jpeg)
![9.7](https://images.gitee.com/uploads/images/2019/1221/092117_ccdb76cb_1755294.jpeg)
![首页](https://img.wxz.name/首页.jpg?imageView2/2/w/252/h/450/interlace/0/q/41)

![IMG_2171](https://images.gitee.com/uploads/images/2019/1221/092117_52d382e3_1755294.png)
![IMG_2173](https://images.gitee.com/uploads/images/2019/1221/092117_d9598cd8_1755294.png)
![IMG_2174](https://images.gitee.com/uploads/images/2019/1221/092117_7572d787_1755294.png)

![成绩](https://images.gitee.com/uploads/images/2019/1221/092117_a5ae62c5_1755294.png)
![成绩列表](https://img.wxz.name/成绩列表.jpg?imageView2/2/w/252/h/450/interlace/0/q/41)
![实验课表](https://img.wxz.name/实验课表.jpg?imageView2/2/w/252/h/450/interlace/0/q/41)


![](https://images.gitee.com/uploads/images/2019/1221/092117_9f11b44d_1755294.png)
![课程表](https://images.gitee.com/uploads/images/2019/1221/092117_00bf6783_1755294.png)
![图书馆](https://images.gitee.com/uploads/images/2019/1221/092117_2a14694f_1755294.png)

![IMG_2170](https://images.gitee.com/uploads/images/2019/1221/092117_6e9ae7fe_1755294.png)
![](https://images.gitee.com/uploads/images/2019/1221/092117_07a71efb_1755294.png)
![](https://images.gitee.com/uploads/images/2019/1221/092117_7d450b0a_1755294.png)


# License
[LGPL](https://github.com/isnine/HutHelper-Open/blob/master/LICENSE)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)