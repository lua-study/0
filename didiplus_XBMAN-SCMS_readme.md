#欢迎使用XBMAN-SCMS
XBMAN-SCMS 是使用django框架，基于ansible开发的配置文件管理、下发的工具，基于ssh协议来管理，客户端无需安装agent。

支持常见系统:CentOS, RedHat, Fedora, Amazon Linux

###截图：
登陆

![登陆](http://git.oschina.net/weihaoxuan/images/raw/master/xbman_scms/login.jpg "登陆")

首页

![首页](http://git.oschina.net/weihaoxuan/images/raw/master/xbman_scms/index.jpg "首页")

命令执行

![命令执行](http://git.oschina.net/weihaoxuan/images/raw/master/xbman_scms/cmd.jpg "命令执行")

任务列表

![任务列表](http://git.oschina.net/weihaoxuan/images/raw/master/xbman_scms/task.jpg "任务列表")

部署方法：

    1、执行 pip install -r requirements.txt 安装基础环境
    2、执行echo "export C_FORCE_ROOT="true"" >>/etc/profile
           source /etc/profile
           这一步是为了在root用户下启动异步程序
    3、初始化数据库
            python manage.py makemigrations
            python manage.py migrate
    4、建立管理员账号（登录页面的用户名密码）
            python manage.py syncdb
    5、启动项目
            python manage.py runserver 0.0.0.0:8000
            系统访问路径为 您的http://您的ip:8000
    6、异步启动
            nohup python manage.py celery worker -c 5 --loglevel=info >> logs/celery.log
    7、以上方式仅限于测试、查看站点、开发使用，如生产环境部署，请参照如下链接进行。
            http://www.xbman.cn/article/14

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)