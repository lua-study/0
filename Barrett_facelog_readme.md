# facelog

facelog 是一个用于人脸识别验证的跨平台跨语言的开发框架，其核心是一个基于 thrift 技术的 RPC 服务，为人脸识别应用提供数据管理、安全认证、前端设备管理、数据下发等基本核心的服务。

facelog 只是一个针对人脸识别应用的开发框架，并不针对特定的应用场景,也不针对特定的人脸识别算法，应用项目在 facelog 的基础上根据facelog 提供的服务接口结合具体的人脸识别算法实现具体应用场景下的业务逻辑。

![系统结构图](https://i.imgur.com/S5lt7NO.png)

关于 facelog 更详细的说明参见 [《facelog 开发手册》](manual/MANUAL.md)


# 编译说明

## 下载代码	

	git clone --recursive https://gitee.com/l0km/facelog.git	
	#--recursive参数用于下载sql2java子项目，如果不需要修改表结构，可不加--recursive参数
## 数据库初始化

参照 [db/README.md](db/README.md)完成数据库建表，并生成数据库操作代码。

	# 数据库建表
	mvn -f gen-sql.xml sql:execute -Ddb.url=jdbc:mysql://localhost:3306/test?characterEncoding=utf8
	# 生成数据库操作代码,如果没有修改表结构可省略此步
	# gen-mysql.bat
	# gen-mysql-g.bat

## 编译

在facelog根目录下执行`mvn install`完成所有项目编译及本地安装

## 生成FatJar

在[facelog-service](facelog-service)下执行`mvn package -Pshade-package`可以生成FatJar(uber-jar):`facelog-service-${project.version}-standalone.jar`

# 初始测试

facelog本身并不是一个实际应用项目，但可以通过运行facelog提供的测试程序了解facelog的运行机制。

## 启动facelog 服务

facelog服务可以手工启动，也提供docker快速部署。参见[《facelog 开发手册》](manual/MANUAL.md) `facelog service 启动`一节

>另请参见 [facelog-service/start_facelog_server.bat](facelog-service/start_facelog_server.bat), [facelog-service/start_facelog_server_debug.bat](facelog-service/start_facelog_server_debug.bat)

## 执行JUnit测试

facelog服务正常启动后，就可以执行[facelog-client/src/test/java/net/gdface/facelog/client](facelog-client/src/test/java/net/gdface/facelog/client)下的测试程序(如`ClientTest`，`HeartbeatTest`，`TokenTest`)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)