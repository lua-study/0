# gobackstage
使用golang语言中的beego框架开发的后台管理系统

做为后台管理系统，基础搭建已经完成，后期不定期进行迭代更新功能……

欢迎一些小伙伴来开发，共同学习下golong语言

## 框架应用技术
1. beego golang语言web框架
2. h-ui  前端ui框架
![输入图片说明](https://gitee.com/uploads/images/2018/0413/200622_020812f5_387692.png "屏幕截图.png")
***

## 目录结构
~~~
code文件夹                 #放在本机的golang的src目录下
mac文件夹                  #mac下docker运行环境
linux文件夹                #linux下docker运行环境  
databasefile文件夹         #数据库存放文件夹
~~~

## 本机有go环境运行项目

~~~
1. 克隆项目到本机go运行src目录下

2. 下载beego框架和mysql扩展如下命令
go get github.com/astaxie/beego
go get github.com/go-sql-driver/mysql

3. 新建数据库golang,然后在目录databasefile中找到golang.sql文件导入到golang数据库

4. 进入gobackstage/code目录下

5. 启动项目
bee run

6. 登陆浏览器访问127.0.0.1:8080
用户名：root
密码：123456
~~~

***

## docker运行项目，需要安装docker环境

### linux docker运行项目
~~~
1. 克隆代码到/opt目录下 #大家最好放在这个目录下

2. 进入/opt/gobackstage/linux目录下

3. 启动项目命令
docker-compose up -d

4. 查看状态是否为up
docker-compose ps

5. 安装数据库
用navicate连接容器的数据库
host:127.0.0.1
root:root
pass:123456
进入新建golang数据库,添加运行文件golang.sql

6. 需要进入golang容器命令
docker exec -it id号 /bin/bash
执行如下命令
go get github.com/astaxie/beego
go get github.com/go-sql-driver/mysql
然后运行命令：nohup go run main.go &,退出容器即可

7. 用户浏览器运行http://127.0.0.1:8080
输入用户名：gewen
输入密 码： 123
最终项目已经安装成功(successful)
~~~

### mac docker运行项目
~~~
1. 克隆代码到/opt目录下 #大家最好放在这个目录下

2. 进入/opt/gobackstage/mac目录下

3. 启动项目命令
docker-compose up -d

4. 查看状态是否为up
docker-compose ps

5. 安装数据库
用navicate连接容器的数据库
host:127.0.0.1
root:root
pass:123456
进入新建golang数据库,添加运行gobackstage.sql

6. 需要进入golang容器命令
docker exec -it id号 /bin/bash
进入之后运行命令：nohup go run main.go &,然后退出容器

7. 用户浏览器运行http://127.0.0.1:8080
输入用户名：gewen
输入密 码： 123
最终项目已经安装成功(successful)
~~~

## 个人介绍
1. cameron 全栈工程师
1. qq      821263167

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)