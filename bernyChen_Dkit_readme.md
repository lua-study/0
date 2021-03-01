#Dkit
自动部署工具.目前只支持linux+svn,可以管理svn仓库和服务器,方便的设置哪个svn分枝部署到哪台服务器上,并可以hook svn仓库,svn提交时自动化部署.
 
# 运行环境
* 需要python3.3及以上python版本;
* 必须安装到svn server同一台机器;
* 启动的用户最好和启动svn server是同一用户。而且确保对每个库的hooks目录有读写权限，因为设置hook时要写东西到hooks目录里。

# 下载
* 直接下载压缩包或通过git:

        git clone https://git.oschina.net/wei/Dkit.git

#安装
* 通过virtualenv安装（推荐）.比如我这里把创建的evn环境放到自己的home目录下:

        cd ~
        virtualenv -p python3 env3
        source ~/env3/bin/activate
        cd xx/xxx #跳回你下载的Dkit目录
        ./install.sh
* 直接安装

        alias python=python3
        ./install.sh
        
如果一切顺利,安装完成后你会看到初始用户名和密码(admin 12345).

#运行
* virtualenv安装后运行：

        source ~/env3/bin/activate
        python run.py
    
* 直接安装后运行：

        python3 run.py
    
默认的端口是5002,可以通过`http://你的服务器ip:5002`访问,默认用户名:admin,密码:12345.如果希望后台运行请自己编辑start.sh启动脚本,如果你用了virtualenv,需要在里改一下自己的env路径.

#使用前需要做的配置
* 1.你需要编辑一下目录下的`post-commit.temp`文件,设置一下`LC_CTYPE`变量和deploy.py路径.具体`post-commit.temp`里有注释;设置svn的hook时,将用这个文件覆盖svn的post-commit
* 2.进入系统后,请第一时间到"系统管理"->"系统设置"对svn参数进行设置.

#需要注意的几点
* 建议安装使用mysql数据库，默认用的sqlite和eventlet使用很容易出现死锁的情况:

        pip install pymysql

    然后编辑Dkit目录下的`config.py`,按下面修改mysql连接信息:

        SQLALCHEMY_DATABASE_URI='mysql+pymysql://username:password@host:port/dbname?charset=utf8'

    然后重新初始化数据库:

        python initdb.py

*启动Dkit的用户必须要和启动svnserve的用户一样，否则svn提交时，hook运行的脚本将没有读写Dkit/logs下日志文件的权限，导致无法自动部署。

#用到的其他开源项目
* flask(以及flask的一些扩展,比如flask-sqlalchemy,flask-wtf等);
* eventlet;
* paramiko;
* UI使用了bootstrap3+jeasyUI

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)