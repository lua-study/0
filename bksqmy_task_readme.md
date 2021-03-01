### task介绍和使用
https://gitee.com/yuejing/task 下的文档：[doc/task介绍和使用.docx]

### task是什么？
task是一个任务调度统一管理平台。
目前主要是通过http来进行任务的调度，http支持签名算法。

一张图能更加懂它是做什么的（一个集中管理任务的平台）
![task的作用](https://static.52jingya.com/syy/blog/2019/03/26/f3811dbcfc6f4246a45693f55dd6a3c8.png "task的作用")


从上图可以清楚的知道，它是一个管理所有系统的定时任务平台
### 特点

支持集群部署
任务的分配能实现负载均衡
任务调度失败后，会发送email提醒，前提是设置了任务发邮件提醒
数据库为mysql

### 架构

服务端：springBoot、springMVC、mybatis、Quartz
前端：jquery、boostarp3


### 部署

1. 去gitee下载最新代码，然后执行maven install，打开项目的target目录可以看到部署包task-1.0.0-bin.zip，然后解压该包，windows环境下双击bin/window/start.bat即可。如果环境为linux，执行bin/start.sh即可。
源码下载地址：http://git.oschina.net/yuejing/task

2. 直接进入 https://gitee.com/yuejing/task/releases 下载最新的发行版的附件，然后解压启动即可。

3. 创建mysql数据库
默认系统会自动创建数据库(前提条件数据库为空时会自动创建)
初始化测试数据：文件在【doc】目录下的task-init.sql文件里面

4. 修改部署时的jdbc连接信息
文件所在目录为项目下的resources里面的application.properties 文件，修改对应的信息即可
当打包成war时，修改配置文件的位置为/WEB-INF/classes/application.properties 文件，修改对应的信息即可
jdbc1.driverClassName=com.mysql.jdbc.Driver
jdbc1.url=jdbc:mysql://127.0.0.1:3306/task?useUnicode=true&characterEncoding=UTF-8
jdbc1.username=root
jdbc1.password=root

5. 设置服务定时任务可使用的线程数
文件所在目录为项目下的resources里面的application.properties 文件，修改对应的信息即可
当打包成war时，修改配置文件的位置为/WEB-INF/classes/application.properties 文件，修改对应的信息即可
#任务的执行线程数,不设置默认为100
project.task.thread.num=100

6. 在eclipse或idea中run as com.ms.server.TaskApplication.java (也可以打包成可执行程序，maven install，然后在target下有个task-1.0.0-bin.zip文件，解压后，window下执行bin/window/start.bat文件。linux下执行bin/start.sh文件)

7. 打开浏览器访问对应的地址
http://127.0.0.1:8380/

### 登录

打开首页(http://127.0.0.1:8380/)
![登录页](https://static.52jingya.com/syy/blog/2019/03/26/600f991c7b1e4b2aaca884171d76e52e.png "登录页")

输入用户：admin
密码：123456
点击【登录】

### 用户管理

这里可以修改用户的资料密码等信息，也可以添加多个帐号
注意，这里建议别删除admin帐号，不然又得去数据库中添加记录了
![用户管理](https://static.52jingya.com/syy/blog/2019/03/26/bb3c22b0076f43c0aabeaf38d382be27.png "用户管理页")

### 系统配置

这里一般采用默认的形式即可
![系统配置](https://static.52jingya.com/syy/blog/2019/03/26/c6ffaeccf8994973b57ae15ac3ff37d0.png "系统配置页")


### 添加任务

比如给支付系统添加任务
系统项目配置
进入项目管理 -> 点击添加项目
![添加项目](https://static.52jingya.com/syy/blog/2019/03/26/5466f3cbaec24481aa78b92a18ce3289.png "添加项目页")


### 添加项目

加密方式解读
1. 不加密
就是该项目下调用的接口都不加密

2. md5(token)
选择后，出现如下内容
{token:"sdfsdfsfsdf",sign:"encryptionParameters"}
token代表和业务系统协商好的密钥，用户md5加密的密钥参数
sign代表token的值，采用md5加密后的值
任务发送http请求时，会增量带参数有sign

3. md5(渠道+token) 
选择后，出现如下内容
{channel:"50",token:"sdfsdfsfsdf",sign:"encryptionParameters"} 
token代表和业务系统协商好的密钥，用户md5加密的密钥参数
channel代表业务系统要求传入的参数（注意：channel的名字是可以改变的）
sign代表channel的值+token的值，采用md5加密后的值
任务发送http请求时，会增量带参数有channel、sign

4. md5(时间戳+token) 
选择后，出现如下内容
{time:"theCurrentTimestamp",token:"sdfsdfsfsdf",sign:"encryptionParameters"} 
token代表和业务系统协商好的密钥，用户md5加密的密钥参数
time代表业务系统要求传入的参数，具体值为当前请求的时间戳（注意：time的名字是可以改变的，单位是精确到ms）
sign代表time的值+token的值，采用md5加密后的值
任务发送http请求时，会增量带参数有time、sign

5. md5(渠道+时间戳+token) 
选择后，出现如下内容
{channel:"50",time:"theCurrentTimestamp",token:"sdfsdfsfsdf",sign:"encryptionParameters"} 
token代表和业务系统协商好的密钥，用户md5加密的密钥参数
channel代表业务系统要求传入的参数（注意：channel的名字是可以改变的）
time代表业务系统要求传入的参数，具体值为当前请求的时间戳（注意：time的名字是可以改变的，单位是精确到ms）
sign代表channel的值+time的值+token的值，采用md5加密后的值
任务发送http请求时，会增量带参数有channel、time、sign

邮件通知
如果选中了否，代表该项目下的所有任务调度失败的都不发送邮件通知

接收邮箱
为接收调度任务失败的邮件通知的邮箱，支持多个邮箱用,分隔（注意是英文的,）
### 项目任务配置

点击【项目管理】记录中的任务管理
![任务管理](https://static.52jingya.com/syy/blog/2019/03/26/b9ab11e6d38e48c6a9dc243534e0d74b.png "任务管理页")
在该项目下新增一个任务
 

### 新增任务

 
1. 名称
任务的名称，用于说明任务做什么

2. 描叙
用来描叙任务

3. 调用链接
执行任务时，http请求的地址（注意：如果项目设置了加密，则会带上相应的加密参数）

4. 任务规则
quartz的调度规则，具体可以参考quartz的规则语法
这里的【0/15 * * * * ?】代表每隔15秒执行一次

5. 任务执行状态
代表当前任务的状态，正常表示执行中，停止代表该任务不执行
当出现待添加的状态，代表任务还在等待添加的状态

6. 失败邮件通知
这里通知的是项目设定的邮箱

### 调度日志

点击【调度日志】进入后，可以查看到对应的调度记录
![调度日志](https://static.52jingya.com/syy/blog/2019/03/26/34f697ff23014b13bddd05e9201ef250.png "调度日志页")

### 日志列表

点击查看可以，看到具体的信息
![查看日志](https://static.52jingya.com/syy/blog/2019/03/26/154f9937bb9f4e0ea897c0c1e6a730bf.png "查看日志页")
 

### 项目图表

点击【任务管理-项目图表】，可以看到支付系统的详细任务数，其它的系统为自己加的测试系统
 

### 服务管理

点击【任务管理-服务管理】进入，可以查到看当前集群的服务，如果服务停止，则会显示已销毁
 

### 服务图表

点击【任务管理-服务图表】进入，可以查看到各个服务当前所执行的任务数
 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)