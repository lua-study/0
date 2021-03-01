Codis 安装说明
==========

一、安装java 与配置环境变量(参考下面)
    export JAVA_HOME=/usr/java/jdk1.7.0_51
    export PATH=$JAVA_HOME/bin:$PATH
    export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

二、安装go与配置环境变量(参考下面)
    export GOPATH=/opt/go/bin
    export GOROOT=/opt/go
    export PATH=$GOPATH:$GOROOT/bin:$PATH
    注意修改权限(chmod +x 文件名)

三、安装zookeeper,并启动(bin/zkServder.sh start)

四、cd到codis文件夹执行./bootstrap.sh

五、cd到codis文件夹下面的sample文件夹，修改config.ini的配置zk=localhost:4180(与zookeeper的启动端口一致)

六、start zookeeper(如果前面已经启动了zookeeper，这部忽略)

七、./start_dashboard.sh

八、./start_redis.sh(如果需要修改redis的服务配置,请修该sh文件,对应的redis服务实例,在redis_conf文件夹下面)

九、./add_group.sh(可以修改该sh里面的信息)

十、./initslot.sh(初始化slot)

十一、./start_proxy.sh

十二、./set_proxy_online.sh


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)