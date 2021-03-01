1、本项目分两个工程进行部署，部署打包的模块为： supplier-deploy和portal-deploy 
2、具体依赖关系查看pom文件的dependency 
3、supplier-api对外提供供应商管理的服务的接口 
4、portal-api对外提供用户访问平台的接口 
5、platform-common提供整个项目功能的框架功能 
6、platform-pub提供公共业务功能 
7、platform-cloud提供云服务功能 

技术选型： 
采用sprintboot作为基础框架 
阿里云的oss作为存储 
短信的下发为阿里云的短信服务 
快递查询是kuai100提供服务 
idCard识别也是由阿里云提供 
系统的缓存使用了redis 



 
 
 
 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)