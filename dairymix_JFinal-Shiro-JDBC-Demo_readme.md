#JFinal-Shiro-JDBC-Demo
简单实现JFinal与Shiro整合例子
1、工程通过Eclipse直接导入，部署到tomcat中；  
2、新建jfinal_shiro数据库，执行jfinal_shiro.sql;  
3、修改配置文件中数据库用户名和密码  
	~/jfinal_shiro/resource/jfinal.properties  
	~/jfinal_shiro/resource/shiro.ini  
4、运行。	  

例子中有3个用户xiaoming、xiaohong、xiaohuang密码分别是用户名（木有进行加密存储）  

roles：admin和user  
permissions：addUser、showUser、editUser、deleteUser  


使用到的插件：  
jfinalshiroplugin：在JFinal可以采用shiro注释  
	源码 http://git.oschina.net/myaniu/jfinalshiroplugin  
	使用 http://my.oschina.net/myaniu/blog/137205  


Beetl 模板引擎  
	http://www.oschina.net/p/beetl  
	页面中使用Shiro http://my.oschina.net/u/567839/blog/143109  

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)