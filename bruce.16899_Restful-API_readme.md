#Restful API

本项目由Laravel框架搭建的一个RESTful API系统，还附带一些测试api页面

如果想了解Laravel可参看[Laravel中文文档](http://www.golaravel.com/ "Laravel中文文档")

这里所下载的项目已经带有核心库，所以不用进行compser安装

如若下载请保证`app/storage`目录设置写权限，更多请参看[http://www.golaravel.com/docs/4.1/installation/#server-requirements](http://www.golaravel.com/docs/4.1/installation/#server-requirements )

##如何导入数据库

*   使用artisan命令行工具实现
*	首先在app/config/database.php进行数据库配置

*	运行artisan迁移命令(即创建表)
	`php artisan migrate` 

*   运行回滚所有迁移（删除表）
	`php artisan migrate:reset`

*   运行回滚所有迁移并重新运行所有迁移（重新创建）
	`php artisan migrate:refresh`

*   数据库填充（比如测试数据的填充）
	`php artisan db:seed`

*	运行回滚所有迁移并重新运行所有迁移，并填充
	`php artisan migrate:refresh --seed`

##如何访问网站

将项目下载之后上传到服务器根目录，解压之

配置上面所述数据库

访问`服务器目录/项目文件夹名(若有)/public` 即可，也可以自定义虚拟目录

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)