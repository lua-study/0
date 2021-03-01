autoload规则 

1.1 支持自定义的autoload，定义一个接口函数 

1.2 autoload规则如下 LIB包的autoload规则，PFinal_Autoload_A_B_C,驼峰式命名 set_include_path()设置autoload的查找路径
 
1)controller 自动加载 www.baidu.com/a/b/c/p1-p2-p3?p4=v4 采用深度优先规则，搜索controller,搜到则停止,后面的作为action,如果没有action，则默认为index controller的类自动寻找功能,APPLICATION.Controller.a.b.c.php
 
2)插件化的autoloader机制 autoload机制，可以注册 比方说 这样子可以支持自定义的目录结构和自定义的命名方式 

3) 默认的autoloader实现 提供一个默认的Autoloader实现，按照A_B_C的方式去加载类

route机制

 2.1 PFinal和PFinalConfig是要require进来的 首先的PFinal->init->PFinalConfig->init(注册各种参数) 
 
 2.2 系统启动的时候自动去application目录下搜索**Config类
 
 2.3 route机制，做成组件的形式
 	route采用route链的形式,模拟apache的.htacess文件
 	a/b/c/d/p1-p2-p3?p4=v4
 	可以有几种路由机制，系统可插拔的方式加载，系统默认加载了default router
 	有一个stack来保存route的机制，可调整优先级,一层层往下route，找到既终止
 	优先级
 		1.	regexRouter 正则表达式router 如 匹配
 		2.  prefixRouter 完全前缀匹配router 如 匹配 a/b/c/d..任何url
 		3.	matchRouter 完全匹配 只能匹配a/b/c
 		4.	defaultRouter 深度优先，默认的router
 	default-router:
 		深度优先查找controller
 
 AOP机制,Interceptor机制
 	Pfinal_Interceptor_Builder负责根据controllerInstance反射出这个controller的Interceptor集合
 	支持两种模式,一种是controller继承自InterceptorInterface,一种是mock的annotation的方式
 	目前支持三种方式的interceptor吧，一种是before，一种是after，一种是around
 	支持controller级别的和action级别的以及application级别的interceptor
 
 validator机制:
 	
 
 plugin机制
 	3.1 cachePlugin,实现action方法的拦截
 	

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)