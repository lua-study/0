#### 项目介绍
spring boot mybatis整合. 监听mysql binlog日志, 并通过rabbitMQ消息, 同步redis

#### 软件架构
SpringBoot、MyBatis、Shiro、Canal、rabbit


#### 安装教程

项目中使用的canal, rabbit的安装
1. canal部署
    1.1 开启MySQL的binlog功能，并配置binlog模式为row
        修改my.cnf为:
        [mysqld]
        log-bin=mysql-bin #添加这一行就ok
        binlog-format=ROW #选择row模式
        server_id=1 #配置mysql replaction需要定义，不能和canal的slaveId重复
    1.2 在mysql中 配置canal数据库管理用户，配置相应权限（repication权限）
        CREATE USER canal IDENTIFIED BY 'canal';
        GRANT SELECT, REPLICATION SLAVE, REPLICATION CLIENT ON *.* TO 'canal'@'%';
        FLUSH PRIVILEGES;
    2.1 下载canal
        mkdir /usr/local/canal
        wget https://github.com/alibaba/canal/releases/download/canal-1.0.24/canal.deployer-1.0.24.tar.gz
        tar -zxvf canal.deployer-1.0.24.tar.gz

        vi conf/example/instance.properties
        修改为自己的IP和帐号, 以及数据库名称
        # position info
        canal.instance.master.address = 192.168.175.131:3306
        canal.instance.master.journal.name =
        canal.instance.master.position =
        canal.instance.master.timestamp =

        #canal.instance.standby.address =
        #canal.instance.standby.journal.name =
        #canal.instance.standby.position =
        #canal.instance.standby.timestamp =

        # username/password
        canal.instance.dbUsername = canal
        canal.instance.dbPassword = canal
        canal.instance.defaultDatabaseName = gosling
        canal.instance.connectionCharset = UTF-8
    2.2 然后cd到bin目录  启动和停止canal-server
        启动  sh startup.sh   停止  sh stop.sh
        启动成功后查看canal.log日志
        显示:
            com.alibaba.otter.canal.deployer.CanalLauncher - ## the canal server is running now ......
        启动canal成功

2. 安装rabbitMQ
    2.1 安装erlang
        安装依赖环境:
        mkdir /usr/local/erlang
        yum -y install make gcc gcc-c++ kernel-devel m4 ncurses-devel openssl-devel unixODBC-devel
        wget http://erlang.org/download/otp_src_19.3.tar.gz
        tar -zxvf otp_src_19.3.tar.gz
        配置
        ./configure --prefix=/usr/local/erlang --with-ssl -enable-threads -enable-smmp-support -enable-kernel-poll --enable-hipe --without-javac
        编译
        make && make install
        配置/etc/profile
        ERLANG_HOME=/usr/local/erlang
        PATH=$PATH:$JAVA_HOME/bin:$ERLANG_HOME/bin
        使其生效
        source /etc/profile
        echo $PATH
        检验erl
    2.2 安装 rabbitMQ
        mkdir /usr/local/rabbitmq
        wget http://www.rabbitmq.com/releases/rabbitmq-server/v3.6.9/rabbitmq-server-generic-unix-3.6.9.tar.xz
        xz -d rabbitmq-server-generic-unix-3.6.9.tar.xz
        tar -xvf rabbitmq-server-generic-unix-3.6.9.tar
        cd /rabbitmq_server-3.6.3/sbin
        启用web管理界面
        ./rabbitmq-plugins enable rabbitmq_management
        启动
        ./rabbitmq-server -detached
        添加用户
        ./rabbitmqctl add_user admin 111111
        设置权限
        ./rabbitmqctl set_user_tags admin administrator

        浏览器访问 IP:15672
        通过admin登录后, 在admin下修改admin帐号的Can access virtual hosts为/
        不然在java代码中通过该帐号访问会报IO错误

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)