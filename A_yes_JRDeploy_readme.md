#JavaWeb项目远程一键部署平台

##功能：
- 可以将 **git** 或 **svn** 服务器上的JavaWeb代码自动拉到本地并打包部署

##用法：
- 进入项目根目录执行一下命令部署到本地
> mvn clean tomcat7:run

- 默认用户名密码  ztc ztc

- 默认项目url
> http://localhost:8080/test

##说明：
- 服务器要求
	- 需要远程服务器为linux系统，
	- 远程服务器需要有  **git ，svn ,git ,mvn ,wget **命令
	- 远程服务器需要有  **jetty-distribution**
- 项目要求
	- 项目必须为maven 项目
	- maven的   必须与git的 项目名称一致
	- 项目必须能用 mvn package 命令生成 可发布的 war包
- 用户名密码
	- 在 src/main/resource/config/config.properties 里配置


---

- 2016-12-01
	- 新建远程部署完成
- 2016-12-05
	- 基本完成
- problem
	- ganymed打开的shell，自己配置的mvn 命令无法使用
		- 直接在/etc/environment添加maven的bin路径
	- 用sh *.sh 执行，nohup 后台进程未显示
		- sh里漏了一个参数，气死我了

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)