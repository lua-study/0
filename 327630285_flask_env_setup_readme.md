#flask_env_setup

由于需要搭建Flask运行环境的服务器无法正常访问外网，无法使用pip命令进行安装。所以安装前需要提前将依赖的包下载好，脚本中需要的tar包已经单独上传到百度云。

http://pan.baidu.com/s/1nuH5zG9

安装：
	设置执行权限 chmod -R 777 flask_env_setup
	执行 ./install.sh ，脚本会自动安装Nginx + Python + uWSGI + Flask + Oracle Client
	执行 ./clean.sh 清空解压目录

脚本在SuSE环境下，可正常将Flask环境搭建起来，如有问题欢迎指正！

需要注意的地方：
	脚本会安装python 3，替换原python命令
	Flask项目目录默认设置为/www/python/host


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)