# demoncat-bus

公共服务：整合消息中心、文件中心、数据字典管理、报表统计管理、地理管理、门户管理等公共服务

## 部署

demoncat-bus-web需要连接外网，来请求外部API

## 邮件

1、通过管理后台，创建邮件发送站点（门户站点），必须有默认的 100 站点

2、客户端请求时，可以附带appId，或者通过服务ID映射站点ID

## 短信

1、通过管理后台，创建短信发送站点（门户站点），必须有默认的 100 站点

2、客户端请求时，可以附带appId，或者通过服务ID映射站点ID

3、通过管理后台，创建短信模板，验证码模板必须是 100000

# 模块介绍

demoncat-bus-common		基础依赖

demoncat-bus-mapper		数据库DAO层

demoncat-bus-service		公共服务的业务层

demoncat-bus-file-service		公共服务的业务层 - 文件管理（前台依赖，管理后台不依赖）

demoncat-bus-service-common		公共服务的公共业务层。其它项目依赖本模块来调用公共服务

demoncat-bus-admin-web	管理后台

demoncat-bus-web			用户前台、REST服务

### 注意事项

1、需要创建项目中的定时任务，并在项目初始化时执行，来缓存字典数据。

	地理缓存：areaInitHandler
	字典缓存：dictInitHandler

2、创建Kafka主题

	定时任务：demoncat-bus-job
	

3、图片验证码

	由于Linux上字体库少，验证码可能乱码，需要安装字体
	
## 门户中心

橱窗

新闻

公告

常见问题

友情链接

关于我们

留言板

	用户向平台留言，平台回复
	
站内信
	
	系统向用户发送通知

## 文件中心
 
1、FastDFS文件上传下载

2、FTP文件上传下载

3、SpringMVC文件上传下载

4、LayEditor

5、KindEditor

6、UEditor

## 消息中心

1、发送和校验图片验证码

2、发送和校验短信验证码

3、发送和校验邮件验证码

注：验证码默认字体  Blod ，如果出现图片验证码乱码，说明服务器上没有字体，需要安装字体库。

## 数据字典管理

统一管理和维护数据字典的分类及数据。

### 使用

注：建站时需要执行初始字典缓存的定时任务

1、管理员 - 通过页面维护 “数据管理 - 字典分类 - 字典”

2、前端查询字典

	通过前端直接请求BUS服务，来查询字典
	
3、后台查询的服务 - 依赖 Bus Service Common，然后进行数据字典查询

	1、使用常量记录 “字典分类的ID”、“字典的ID”
	
	2、通过“DictService”直接查询字典（缓存在Redis中）
	
4、后台变更的服务 - 依赖 Bus Service Common，然后进行数据字典的增删改

	1、使用常量记录 “字典分类的ID”、“字典的ID”
	
	2、通过“DictFeign”进行字典的增删改(由BUS系统进行缓存维护)

## 报表统计管理


统一管理和维护报表统计的分类及数据。

报表分为两种：

	固定统计：1个分类，对应1个统计项；1个父分类，对应多个子分类，关联多个子统计项
	
	动态统计：1个分类，对应多个统计项，通过统计数据的ID区分；父分类与统计项没有关联
	
### 使用

1、管理员 - 通过页面维护 “数据管理 - 报表分类”

2、统计和查询报表的服务 - 依赖 Bus Service Common，然后进行报表的创建和查询
	
	1、使用常量记录 “报表分类的ID”
	
	2、调用 “ReportFeign” 来创建和查询 报表统计数据，并自已处理缓存和整合。

## 邮件

1、自定义标题和内容

2、使用FreeMarker模板（email_template）渲染
	
	# 邮件服务器
	email.server=smtp.163.com
	# 邮件发送者
	email.username=18500321103@163.com
	# 邮件发送者授权码/密码
	email.password=yxl1234

## 短信配置

	# 阿里云API密钥
	sms.aliyun.access-key-id=
	sms.aliyun.access-key-secret=
	# 容联云通讯授权账户
	sms.yuntongxun.account=
	sms.yuntongxun.auth=
	sms.yuntongxun.app=
	
	# 是否发送短信：true(正式环境)，false(模拟发送，验证码111111)
	sms.status=false
	# 短信渠道
	sms.channel=2
	
### 短信运维
	
1、通过数据字典（公共服务>短信），设置发送渠道

2、设置发送站点

3、设置短信模板，设置模板与渠道的编码关系

## 文件上传配置

1、默认后台图片限制100M，文件限制1G，可以通过application.properties配置
2、上传大文件会导致OOM，应合理调整JVM内存、文件大小配置、前端文件上传限制


	#--------------------------file

	# 文件最大值，默认1MB
	spring.servlet.multipart.max-file-size=2001MB
	# 每次请求的最大值，默认为10MB
	spring.servlet.multipart.max-request-size=2001MB
	
	#--------------------------fastdfs
	
	# 服务端Tracker（多个用,分隔，必须）
	fastdfs.url=192.168.1.250:22122
	
	# 大文件分块上传阀值（byte，默认20M）
	fastdfs.limit=20971520
	
	# 读取时间(毫秒；超时读取不到数据时中断；默认1分钟)
	fastdfs.so-timeout=60000
	# 连接超时(毫秒；超时创建不了连接时中断；默认1分钟)
	fastdfs.connect-timeout=60000
	
	# 连接池最小的空闲对象个数（默认0）
	fastdfs.min-idle=1
	# 连接池最大的空闲对象个数（默认5）
	fastdfs.max-idle=10
	# 连接池最多对象个数（超过时将阻塞等待释放，默认20）
	fastdfs.max-total=50
	# 连接池空闲对象检测周期毫秒（毫秒，-1表示不检测，默认10分钟）
	fastdfs.time-between-eviction-runs-millis=600000
	# 连接池每次检测空闲对象的数量（默认3）
	fastdfs.num-tests-per-eviction-run=3
	
	#--------------------------ftp
		
	# 服务端URL（必须）
	ftp.url=192.168.1.250:21
	# FTP登录账号（必须）
	ftp.username=ftp
	# FTP登录密码（必须）
	ftp.password=vsftp111
	
	# FTP根目录：FTP安装路径，格式为/xx/xx（连接池必须）
	ftp.root=/data/ftp
	# 上传目录是否前缀profile：混合管理多环境文件时设置为1，将为上传路径前缀profile
	ftp.profile=1
	# FTP缓冲区
	ftp.buff=102400
	# FTP连接模式：1被动，0主动
	ftp.mode=1
	
	# 连接池最小的空闲对象个数（默认0）
	ftp.min-idle=1
	# 连接池最大的空闲对象个数（默认5）
	ftp.max-idle=10
	# 连接池最多对象个数（超过时将阻塞等待释放，默认20）
	ftp.max-total=50
	# 连接池空闲对象检测周期毫秒（毫秒，-1表示不检测，默认10分钟）
	ftp.time-between-eviction-runs-millis=600000
	# 连接池每次检测空闲对象的数量（默认3）
	ftp.num-tests-per-eviction-run=3
	
	#--------------------------demoncat-img
		
	# 图服URL（必须）：后缀非/
	demoncat.img.url=http://dev.img.ys360.net
	# 文件最大限制(byte，默认2000M)
	demoncat.img.file-max=2097152000
	# 图片最大限制(byte，默认100M)
	demoncat.img.img-max=104857600
	
	


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)