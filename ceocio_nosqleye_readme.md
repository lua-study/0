# NOSQL EYE
nosql数据库监控工具，目前实现了对Redis、MongoDB的监控功能。

## 演示地址：
http://106.14.181.95:7004 
登录用户名、密码:admin/admin
## 预览
![图片描述](http://112.74.163.112/tmp/11.png)
![图片描述](http://112.74.163.112/tmp/22.png)
![图片描述](http://112.74.163.112/tmp/33.png)
![图片描述](http://112.74.163.112/tmp/44.png)
![图片描述](http://112.74.163.112/tmp/55.png)
## 安装环境：

推荐：centos7（6.*也可以）、MySQL5.7、JDK8

## 安装步骤：

1、安装初始数据，在MySQL数据库上新建nosql_eye数据库，导入build/nosql_eye.sql文件。新建数据库账户:dev，密码：123456

2、将build/nosql-eye-1.4.jar传输到服务器，java -jar nosql-eye-1.4.jar启动应用即可。如需在后台启动请使用：nohup java -jar nosql-eye-1.4.jar > /dev/null 2>&1 &

## 该项目使用的技术：

### 前端：
* bootstrap3
* jquery1.11
* ECharts3
* vis

### 后端：
* springboot 1.5.4
* druid1.0
* mybatis3.4
* ehcache2.10
* fastjson1.2
* logback1.1

### 数据库：
* MySQL5.7


## 联系：
360841519@qq.com


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)