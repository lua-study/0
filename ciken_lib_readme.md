　　湖南科技大学图书馆自动续借系统
==============================================================
Autor : ciken   
E-mail: ciken@live.cn   
   
功能：   
　　　　1.根据读者相关信息（帐号、密码、邮箱）获取借阅信息   
　　　　2.设置少于特定天数帮读者续借，并将续借结果发送邮件给读者   
　　　　3.相关函数写的比较灵活，读者可根据自己的需要提取相关函数自用   
   
####PS：如果您觉得相关功能实现有更好的建议，欢迎指正 
 
 
#### 代码依赖关系
	python版本：python2.7
	代码在linux下测试上线
	python调用的非标准库：MySQLdb、BeautifulSoup
	数据库：Mysql


#### 相关模块说明
	目录结构
	dir
	├── renew_master.py 	 #主模块，负责各次模块调用
	├── api
	│   ├── __init__.py
	│   ├── CHECK.py 			    #次模块，负责借阅信息提取、字符串处理、邮件内容处理等
	│   ├── CONF-development.py 	#参数模板，请将此文件在当前目录复制一份为CONF.py
	│   ├── CONF.py 				#参数文件，项目主文件夹参数、Mysql连接参数、邮箱参数、log参数、公共调用函数、公共调用参数相关
	│   └── SERVER.py 				#次模块，负责数据库操作、邮件发送等
	├── logs				#日志文件夹
	│   └── renew
	│       └── 2014-07-30.logs 		#日志文件，以日期为文件名
	├── json				#续借信息
	│   └── *.json
	└── README.md 			#README



#### 各模块函数说明
	CHECK.py
	├── libConnect		#测试图书馆链接是否正常
	├── calcDate		#计算还剩多少天还书
	├── checkReaderPasswd	#检查读者密码是否正确
	├── collectReaderBorrowContent	#检查读者是否借书,没有的话返回False,有的话提取借书段字符串
	├── getBorrowInfo 	#以list[dict]格式返回读者借阅信息
	├── renewStu	#为该学号检查并尝试续借
	├── renewBook		#续借某书,接受list[dict]格式的参数，以list[dict]格式返回续借信息，并更新还书期限
	└── mailContentHand #邮件处理，接受字符串格式的学号、list[dict]格式的续借信息、list[dict]格式的借阅信息，返回字符串格式html形式的邮件内容

	SERVER.py
	├──	db			#数据库操作，相关接口待用。接受字符串（'GET'、'ADD'、'DEL'、'SWITCH'）格式、字符串（'GET'接收None参数、'ADD' 接收3个参数、'DEL'接收1个参数、'SWITCH'接受2个参数）
	└──	sendEmail	#发送邮件函数，接收字符串格式的（学号、邮件地址、邮件内容）

	renew_master.py
	├── libConnectTest	#测试 图书馆连接是否正常
	├── stuLibSecretFalseHand 	#密码失败处理
	├── stuLibSecretTrueHand	#密码成功处理
	└──各模块函数调用、日志记录相关



####update information
version:1.4.2.1 
1.修改CHECK.renewBook的返回形式

version:1.4.2 
1.添加CHECK.collectReaderBorrowContent模块，连接不成功发送邮件并退出 
2.将CHECK.renewStu、CHECK.renewStu从CHECK.renewBook函数中分离出来 
3.改回各函数中返回方式为python字典，最后json写入文件 
4.将renew_master中各函数分离出来 

version:1.4.1 
1.将获取登入信息函数提取出来  
2.密码错误数据库续借开关关闭并发送邮件给读者  
2014.12.17  
  
version:1.4  
1.使用json进行内容交互  
2.发送邮件成功记录进log  
2014.07.30  
  

version:1.3  
1.使用mysql作为数据库对用户信息进行存取  
2.引入BeautifulSoup库替换某些正则表达式  
3.对邮件内容进行了html格式处理  
2014.07.30  
  
version:1.2   
1.将各函数模块分类   
2.增加了配置文件一项   
3.去掉了opener和cookie模块，替换为requests模块  
  
version:1.0  
1.设置自动续借过期天数  
2.续借过后发送邮件  
3.续借过后检测未续借成功书籍并发送邮件  
2014.03.19  
  
####　　　　　　　　Copyright © 2014 Free Software Foundation, ciken


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)