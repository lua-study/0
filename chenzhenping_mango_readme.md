# mango

## 前端安装指南
	本系统前端使用Vue.js和Element框架搭建.

#### 1、 开发环境
	前端开发环境基于NPM环境，使用VS Code开发。
	IDE : VS Code 1.27 或 WebStorm
	NODE: Node 10.15.x
	NPM : NPM 6.4.x

#### 2、 技术选型
	前端技术主要使用Vue.js和Elment UI框架。
	前端框架：Vue 2.x
	页面组件：Element 2.x
	状态管理：Vuex 2.x
	后台交互：axios 0.18.x
	图标使用：Font Awesome 4.x

#### 3、项目结构
	前端项目结构如下。
	mango-ui
	  -- build：项目编译相关模块，项目模板自动生成
	  -- config：项目配置相关模块，项目模板自动生成
	  -- src：项目源码模块，前端开发工作集中在此目录
	     -- assets： 图标、字体、国际化信息等静态信息
	     -- components： 组件库，对常用组件进行封装
	     -- http： 后台交互模块，统一后台接口请求API
	     -- i18n： 国际化模块，使用Vue i18n进行国际化
	     -- mock： Mock模块，模拟接口调用并返回定制数据
	     -- permission： 权限控制模块，处理权限认证逻辑
	     -- router： 路由管理模块，负责页面各种路由配置
	     -- store： 状态管理模块，提供组件间状态共享
	     -- utils： 工具模块，提供一些通用的工具方法
	     -- views： 页面模块，主要放置各种页面视图组件

#### 4、 编译运行
	获取源码
		获取前端源码，整个前端只有一个工程mango-ui，将其拷贝放置到本地目录。
		https://gitee.com/ctocloud/mango.git 在mongo-ui目录

	编译源码
		在mango-ui目录下打开CMD终端，执行 npm install, 下载和安装项目依赖包。

	启动系统
		执行 npm run dev 命令，启动项目，启动之后通过 http://localhost:8080 访问。

	项目打包
		执行 npm run build 命令，进行前端项目打包，打包完成之后会生成 dist 目录。
		将生成的目录直接放置到如Tomcat之类的WEB服务器，启动服务即可访问。

	Mock 开关
		本系统采用前后端分离架构，前端若开启Mock模块，可以模拟大部分接口数据。
		通过修改src/mock/index.js中的openMock变量，可以一键开启或关闭Mock功能。

	修改配置
		如果想自定义端口（默认是8080），可以修改 config/index.js 下的 port 属性。
		后台接口和备份服务器地址配置在 src/utils/global.js，如有修改请做相应变更。


#### 后端安装指南
	本系统后端使用SpringCloud生态组件搭建.

#### 1、开发环境
	后端开发环境基于Java环境，使用Eclipse开发。
	IDE : eclipse 4.x
	JDK : JDK1.8.x
	Maven : Maven 3.5.x
	MySQL: MySQL 5.7.x
	Consul: Consul 1.4.0


#### 2、技术选型
	后端技术主要使用Spring Boot、Spring Cloud和MyBatis框架。
	核心框架：Spring Boot 2.x
	服务治理：Spring Cloud Finchley
	安全框架：Spring Security 5.x
	视图框架：Spring MVC 5.x
	持久层框架：MyBatis 3.x
	数据库连接池：Druid 1.x
	消息队里：RabbitMQ
	接口文档：Swagger 2.9.x
	日志管理：SLF4J、Log4j


#### 3、项目结构
	后端项目源码工程结构。
	mango-common： 公共代码模块，主要放置一些工具类
	mango-core： 封装业务模块，主要封装公共业务模块
	mango-admin： 后台管理模块，包含用户、角色、菜单管理等
	mango-backup： 系统数据备份还原模块，可选择独立部署
	mango-monitor： 系统监控服务端，监控Spring Boot应用
	mango-producer： 服务提供者示例，方便在此基础上搭建模块
	mango-consumer： 服务消费者示例，方便在此基础上搭建模块
	mango-hystrix： 服务熔断监控模块，收集汇总熔断统计信息
	mango-zuul： API服务网关模块，统一管理和转发外部调用请求
	mango-config： 配置中心服务端，生成GIT配置文件的访问接口
	mango-consul： 注册中心，安装说明目录，内附安装引导说明
	mango-zipkin： 链路追踪，安装说明目录，内附安装引导说明
	config-repo： 配置中心仓库，在GIT上统一存储系统配置文件
	mango-pom： 聚合模块，仅为简化打包，一键执行打包所有模块

#### 4、编译运行

	获取源码
		获取后端源码，获取上面所列所有项目结构，将其拷贝放置到本地目录。
		https://gitee.com/ctocloud/mango.git 在mongo目录

	导入工程
		使用 Eclipse导入 Maven 项目，在此之前请确认已安装 JDK 和 Maven 工具。

	编译源码
		找到 mango-pom 工程下的 pom.xml，执行 maven clean install 命令进行一键打包。
		一般来说不会有什么问题，如果还打包失败，可以按照优先级逐个编译试一试。

	导入数据库
		新建mango数据库，使用项目sql目录下的mango.sql 脚本，导入初始化数据库。
		修改 mango-admin 下 application.yml 中的数据源配置信息为自己的数据库配置。
		修改 mango-backup下 application.yml 中的数据源配置信息为自己的数据库配置。

	启动系统
	1)基础必需模块（注册中心：mango-consul，服务监控：mango-monitor，链路跟踪，配置中心总线BUS）
		找到 mango-consul 工程，根据安装说明安装注册中心，执行 consul agent -dev 启动。
		找到 mango-monitor 工程下的MangoMonitorApplication， 启动项目，开启服务监控。
		找到 mango-zipkin  工程下的MangoMonitorApplication， 启动项目，开启服务链路跟踪。
		启动RabbitMq服务，以便及时更新配置文件

	2)权限管理模块（权限管理：mango-admin，备份还原：mango-backup）
		找到 mango-admin 工程下的MangoAdminApplication， 启动项目，开启权限系统服务。
		找到 mango-backup 工程下的MangoBackupApplication.java，启动项目，开启备份服务。

	3)其他示例模块（Spring Cloud示例模块，作为开发模板和范例，根据需要启动）
		以下为Spring Cloud体系各种功能的实现范例，可以根据需要启动，后续扩展开发也可以作为参考和模板使用。
		具体使用教程请参考本书后面Spring Cloud系列教程的章节，关于Spring Cloud体系的各种功能模块都有详细的讲解和完整的案例实现。
	
	3)这些示例模块包括：
		mango-config： 配置中心服务端，演示分布式配置中心的实现（配置rabbitmq的地址）
		mango-hystrix： 服务熔断监控模块，演示熔断监控功能的实现（配置appConfig: mango-consumer）
		mango-zuul： API服务网关模块，演示API统一网关的实现
		mango-producer： 服务提供者示例，演示服务提供者的实现(两个实例）
		mango-producer2： 服务提供者示例，演示服务提供者的实现(两个实例）
		mango-consumer： 服务消费者示例，演示服务消费者的实现（配置rabbitmq的地址）
		
		

	4)注意事项：
		注册中心是基础服务，需要先安装Consul，找到mango-consul工程，根据安装说明安装Consul。
		如果需要链路追踪服务，需要安装zipkin，找到mango-zipkin 工程，根据安装说明安装zipkin。
		如果需要配置中心服务，需要安装rabbitMQ，找到mango-config 工程，根据安装说明安装rabbitMQ。

##
## 中间件安装（容器下快速安装）
	Consul Zipkin RabbitMq Mysql  

#### 安装Consul 

使用Consul提供注册和发现服务：

	什么是 Consul
	Consul 是 HashiCorp 公司推出的开源工具，用于实现分布式系统的服务发现与配置。
    与其它分布式服务注册与发现的方案，Consul 的方案更“一站式”，
    内置了服务注册与发现框架、分布一致性协议实现、健康检查、Key/Value 存储、多数据中心方案，不再需要依赖其它工具（比如 ZooKeeper 等）。
    使用起来也较为简单。Consul 使用 Go 语言编写，因此具有天然可移植性(支持Linux、windows和Mac OS X)；
    安装包仅包含一个可执行文件，方便部署，与 Docker 等轻量级容器可无缝配合。

Consul 安装：

	访问 Consul 官网 ，根据操作系统类型，选择下载 Consul 的最新版本。我这里选择windows版本。

打开CMD终端，进入consul.exe所在目录，执行如下命令启动Consul服务。
	
	cd C:\consul_1.3.0_windows_amd64　　# 进入consul.exe所在目录
	
	consul agent -dev        # 启动服务, -dev 表示开发模式运行，另外还有 -server 表示服务模式运行

启动成功之后：
	访问 http://localhost:8500 ， 可以查看 Consul 管理界面。


#### 安装Zipkin
下载镜像：
此前请先安装好docker环境，使用以下命令分别拉取zipkin和elasticsearch镜像。

	docker pull openzipkin/zipkin
	docker pull docker.elastic.co/elasticsearch/elasticsearch:6.3.0

通过 docker images 查看下载镜像。

	[root@taotao01 dockerfile]# docker images
	REPOSITORY                                      TAG                 IMAGE ID            CREATED             SIZE
	rabbitmq                                        management          db322a6c3b84        2 days ago          179MB
	openzipkin/zipkin                               latest              2787ea894ee8        12 days ago         250MB
	hello-world                                     latest              fce289e99eb9        5 months ago        1.84kB
	docker.elastic.co/elasticsearch/elasticsearch   6.3.0               56d3dc08212d        12 months ago       783MB
	
		
编写启动文件：
在本地创建如下文件夹结构， data目录用来存放elasticsearch存储的数据。

	dockerfile
	    |- elasticsearch
	    |    |- data
	    |- docker-compose.yml

编写docker-compose文件，主要作用是批量启动容器，避免在使用多个容器的时候逐个启动的繁琐。

docker-compose.yml

	version: "3"
	services:
	
	  elasticsearch:
	    image:  docker.elastic.co/elasticsearch/elasticsearch:6.3.0
	    container_name: elasticsearch
	    restart: always
	    networks:
	      - elk
	    ports:
	      - "9200:9200"
	      - "9300:9300"
	    volumes:
	       - ../elasticsearch/data:/usr/share/elasticsearch/data
	
	  zipkin:
	    image: openzipkin/zipkin:latest
	    container_name: zipkin
	    restart: always
	    networks:
	      - elk
	    ports:
	      - "9411:9411"
	    environment:
	      - STORAGE_TYPE=elasticsearch
	      - ES_HOSTS=elasticsearch
	
	networks:
	    elk:

启动服务： 命令模式进入dockerfile目录，执行启动命令如下。

	docker-compose up -d


执行完成之后： 通过 docker ps 命令查看，发现zipkin和elasticsearch确实启动起来了。

	[root@taotao01 dockerfile]# docker ps
	CONTAINER ID        IMAGE                                                 COMMAND                  CREATED             STATUS                          PORTS                                                                                                                      NAMES
	fe3051a82583        rabbitmq:management                                   "docker-entrypoint.s…"   3 hours ago         Up 3 hours                      0.0.0.0:4369->4369/tcp, 0.0.0.0:5671-5672->5671-5672/tcp, 0.0.0.0:15671-15672->15671-15672/tcp, 0.0.0.0:25672->25672/tcp   rabbitmq
	4a73394cf351        openzipkin/zipkin:latest                              "/busybox/sh run.sh"     3 hours ago         Up 3 hours                      9410/tcp, 0.0.0.0:9411->9411/tcp                                                                                           zipkin
	447bd2d0f365        docker.elastic.co/elasticsearch/elasticsearch:6.3.0   "/usr/local/bin/dock…"   3 hours ago         Restarting (1) 19 seconds ago                                                                                                                              elasticsearch



zipkin服务端已经搭建完成了：

	访问 http://localhost:9411

	效果如下，因为还没有客户端，所以还没有数据。



#### 注意：快速启动方案二：

	这里我们采用了elasticsearch作为存储方式，如果想简单通过内存方式启动，无须安装elasticsearch，直接启动一个zipkin容器即可。

	docker run -d -p 9411:9411 openzipkin/zipkin
如果想使用其他如数据库等方式存储，请查询相关配置文档。



#### 安装RabbitMq

Spring Cloud Bus

	Spring Cloud Bus，被大家称为消息总线，它通过轻量级的消息代理来连接各个分布的节点，
	可以利用像消息队列的广播机制在分布式系统中进行消息传播，通过消息总线可以实现很多业务功能，
	其中对于配置中心客户端刷新，就是一个非常典型的使用场景。

Spring Cloud Bus 进行配置更新步骤如下:

	  1、提交代码触发post请求给/actuator/bus-refresh
	
	  2、server端接收到请求并发送给Spring Cloud Bus
	
	  3、Spring Cloud bus接到消息并通知给其它客户端
	
	  4、其它客户端接收到通知，请求Server端获取最新配置
	
	  5、全部客户端均获取到最新的配置

安装RabbitMQ：

因为我们需要用到消息队列，我们这里选择RabbitMQ，使用Docker进行安装。

拉取镜像：
执行以下命令，拉取镜像。

	docker pull rabbitmq:management
完成之后执行以下命令查看下载镜像。

	docker images

创建容器：
执行以下命令，创建docker容器。

	docker run -d --name rabbitmq -p 5671:5671 -p 5672:5672 -p 4369:4369 -p 25672:25672 -p 15671:15671 -p 15672:15672 rabbitmq:management

启动成功之后： 可以执行以下命令查看启动容器。

	docker ps

登录界面：

	容器启动之后就可以访问web管理界面了，访问 http://宿主机IP:15672。

	系统提供了默认账号。 用户名：guest  密码： guest

#### Mysql

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)