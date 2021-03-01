# TBScheduleConsole #
TBScheduleConsole是基于淘宝的开源调度框架TBSchedule做的控制台  
最近公司有在使用TBSchedule作为任务调度框架,由于原生的控制台对于多应用切换的使用场景比较麻烦,所以自己开发了一个简单控制台  

- 用户维护； 
- 应用维护； 
- 任务调度维护。  

## 使用方法 ##
1.git clone git@git.oschina.net:02/tbscheduleconsole.git 
2.cd tbscheduleconsole 
3.导入sql脚本到mysql 
4.修改application.yml 中数据库连接串 
5.修改application.yml 中zookeeper地址为 TBSchedule对应的zookeeper地址 
6.mvn spring-boot:run 
7.打开127.0.0.1:8080 
用户名密码 admin  SQL脚本中可自行修改 
   部分截图   
   
   
   
   


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)