# 系统环境
```
Ubuntu 14.04.2 LTS
MySQL 5.6.36
Keepalived 1.2.7
Master 1: 192.168.1.143
Master 2: 192.168.1.144
VIP: 192.168.1.140
```

# 安装 MySQL (Master 1、Master 2)
## 安装
```
> cd $HOME
> wget http://mirrors.sohu.com/mysql/MySQL-5.6/mysql-5.6.36.tar.gz
> tar -zxf mysql-5.6.36.tar.gz
> cd cd mysql-5.6.36
> sudo mkdir /etc/mysql
> cmake -DCMAKE_INSTALL_PREFIX=/usr/local/mysql -DMYSQL_DATADIR=/usr/local/mysql/data -DSYSCONFDIR=/etc/mysql -DWITH_MYISAM_STORAGE_ENGINE=1 -DWITH_INNOBASE_STORAGE_ENGINE=1 -DWITH_MEMORY_STORAGE_ENGINE=1 -DWITH_READLINE=1 -DMYSQL_UNIX_ADDR=/usr/local/mysql/mysql.sock -DMYSQL_TCP_PORT=3306 -DENABLED_LOCAL_INFILE=1 -DEXTRA_CHARSETS=utf8,gbk -DDEFAULT_CHARSET=utf8 -DDEFAULT_COLLATION=utf8_general_ci -DWITH_PARTITION_STORAGE_ENGINE=1
> make -j6
> sudo make install
> cd /usr/local/mysql
> sudo chown -R mysql:mysql /usr/local/mysql
> sudo scripts/mysql_install_db --user=mysql --basedir=/usr/local/mysql --datadir=/usr/local/mysql/data
```

## 配置
```
> cd /usr/local/mysql
> sudo vim my.cnf
```

Master1: /usr/local/mysql/my.cnf

```
[client]
default-character-set=utf8

[mysqld]
default-storage-engine=InnoDB
collation_server=utf8_general_ci
character_set_server=utf8
init_connect='SET NAMES utf8'
max_allowed_packet=64M
max_connections=1000
bind-address=0.0.0.0
datadir=/usr/local/mysql/data
socket=/usr/local/mysql/mysql.sock
user=mysql
# Disabling symbolic-links is recommended to prevent assorted security risks
symbolic-links=0
# master1
log-bin=mysql-bin
binlog_format=mixed
relay-log=relay-bin
relay-log-index=slave-relay-bin.index
auto-increment-increment=2
auto-increment-offset=1
server-id=1
log_slave_updates=1
read_only=0

[mysqld_safe]
log-error=/var/log/mysqld.log
pid-file=/usr/local/mysql/mysqld.pid

sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES
```

Master2: /usr/local/mysql/my.cnf

```
[client]
default-character-set=utf8

[mysqld]
default-storage-engine=InnoDB
collation_server=utf8_general_ci
character_set_server=utf8
init_connect='SET NAMES utf8'
max_allowed_packet=64M
max_connections=1000
bind-address=0.0.0.0
datadir=/usr/local/mysql/data
socket=/usr/local/mysql/mysql.sock
user=mysql
# Disabling symbolic-links is recommended to prevent assorted security risks
symbolic-links=0
# master2
log-bin=mysql-bin
binlog_format=mixed
relay-log=relay-bin
relay-log-index=slave-relay-bin.index
auto-increment-increment=2
auto-increment-offset=2
server-id=2
log_slave_updates=1
read_only=1

[mysqld_safe]
log-error=/var/log/mysqld.log
pid-file=/usr/local/mysql/mysqld.pid

sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES
```

Master 1、Master 2 复制my.cnf至`/etc/mysql/`目录下

```
> sudo cp my.cnf /etc/mysql/
```

添加环境变量: ~/.bashrc (Master 1、Master 2)

```
export MYSQL_HOME=/usr/local/mysql
export PATH=$PATH:$MYSQL_HOME/bin
```

启动MySQL (Master 1、Master 2)

```
> sudo bin/mysqld_safe --user=mysql &
```

修改root用户密码 (Master 1、Master 2)

```
> sudo bin/mysqladmin -u root password '123456'
```

登录MySQL，设置root远程连接权限 (可选)(Master 1、Master 2)

```
> mysql -uroot -p123456
> grant all privileges on *.* to 'root'@'%' identified by '123456' with grant option;
> flush privileges;
```

## 配置双主同步
### 将Master 1 设置为Master 2 的主服务器
创建同步用户 Master 1 上操作

```
> mysql -uroot -p123456
> CREATE USER 'rep'@'192.168.1.144' IDENTIFIED BY 'mysql';
> grant all privileges on *.* to rep@'192.168.1.144' identified by 'mysql';
> flush privileges;
```

创建同步用户 Master 2 上操作

```
> mysql -uroot -p123456
> CREATE USER 'rep'@'192.168.1.143' IDENTIFIED BY 'mysql';
> grant all privileges on *.* to rep@'192.168.1.143' identified by 'mysql';
> flush privileges;
```

获取全局读锁以获取二进制日志文件的位置 Master 1 上操作

```
> mysql -uroot -p123456
> FLUSH TABLES WITH READ LOCK;  #获取全局读锁以获取二进制日志文件的位置
> show master status;
+------------------+----------+--------------+------------------+-------------------+
| File             | Position | Binlog_Do_DB | Binlog_Ignore_DB | Executed_Gtid_Set |
+------------------+----------+--------------+------------------+-------------------+
| mysql-bin.000006 |     1146 |              |                  |                   |
+------------------+----------+--------------+------------------+-------------------+
1 row in set (0.00 sec)
```

获取全局读锁以获取二进制日志文件的位置 Master 2 上操作

```
> mysql -uroot -p123456
> FLUSH TABLES WITH READ LOCK;  #获取全局读锁以获取二进制日志文件的位置
> show master status;
+------------------+----------+--------------+------------------+-------------------+
| File             | Position | Binlog_Do_DB | Binlog_Ignore_DB | Executed_Gtid_Set |
+------------------+----------+--------------+------------------+-------------------+
| mysql-bin.000006 |      120 |              |                  |                   |
+------------------+----------+--------------+------------------+-------------------+
1 row in set (0.00 sec)
```

Master 1 原有数据备份 mysqldump Master 1 上操作

```
>
```

Master 2 恢复

Master 1 上操作

```
> CHANGE MASTER TO MASTER_HOST='192.168.1.144',MASTER_USER='rep',MASTER_PASSWORD='mysql',MASTER_LOG_FILE='mysql-bin.000006',MASTER_LOG_POS=120;
```

Master 2 上操作

```
> CHANGE MASTER TO MASTER_HOST='192.168.1.143',MASTER_USER='rep',MASTER_PASSWORD='mysql',MASTER_LOG_FILE='mysql-bin.000006',MASTER_LOG_POS=1146;
```

查看slave status (Master 1、Master 2)

```
> show slave status\G
# 成功标准
Slave_IO_Running: Yes
Slave_SQL_Running: Yes
```

解锁(Master 1、Master 2)

```
> UNLOCK TABLE;
> exit;
```

# 安装 keepalived (Master 1、Master 2)
## 安装
```
# ubuntu 采用apt-get安装
> sudo apt-get install -y keepalived
```

## 配置 keepalived
### Master 1
[/etc/keepalived/keepalived.conf]

```
vrrp_script chk_mysql {
    script "/etc/keepalived/check_mysql.sh"
    interval 10         #设置检查间隔时长，可根据自己的需求自行设定
}
vrrp_instance VI_1 {
    state BACKUP        #通过下面的priority来区分MASTER和BACKUP，也只有如此，底下的nopreempt才有效
    interface eth0
    virtual_router_id 51
    priority 100
    advert_int 1
    nopreempt           #防止切换到从库后，主keepalived恢复后自动切换回主库
    authentication {
        auth_type PASS
        auth_pass 123456789
    }
    track_script {
        chk_mysql
    }
     
    virtual_ipaddress {
        192.168.1.140/24
    }
}
```

[/etc/keepalived/check\_mysql.sh]

```
#!/bin/bash

###判断如果上次检查的脚本还没执行完，则退出此次执行
if [ `ps -ef|grep -w "$0"|grep -v "grep"|wc -l` -gt 2 ];then
    exit 0
fi 
mysql_con='mysql -uroot -p123456'
error_log="/etc/keepalived/logs/check_mysql.err"

###定义一个简单判断mysql是否可用的函数
function excute_query {
    ${mysql_con} -e "select 1;" 2>> ${error_log}
}
 
###定义无法执行查询，且mysql服务异常时的处理函数
function service_error {
    echo -e "`date "+%F  %H:%M:%S"`    -----mysql service error，now stop keepalived-----" >> ${error_log}
    echo "1234567890" | sudo -S service keepalived stop >> ${error_log}
    echo "DB1 keepalived 已停止" >> ${error_log}
    echo -e "\n---------------------------------------------------------\n" >> ${error_log}
}
 
###定义无法执行查询,但mysql服务正常的处理函数
function query_error {
    echo -e "`date "+%F  %H:%M:%S"`    -----query error, but mysql service ok, retry after 30s-----" >> ${error_log}
    sleep 30
    excute_query
    if [ $? -ne 0 ];then
        echo -e "`date "+%F  %H:%M:%S"`    -----still can't execute query-----" >> ${error_log}
 
        ###对DB1设置read_only属性
        echo -e "`date "+%F  %H:%M:%S"`    -----set read_only = 1 on DB1-----" >> ${error_log}
        mysql_con -e "set global read_only = 1;" 2>> ${error_log}
 
        ###kill掉当前客户端连接
        echo -e "`date "+%F  %H:%M:%S"`    -----kill current client thread-----" >> ${error_log}
        rm -f /tmp/kill.sql &>/dev/null
        ###这里其实是一个批量kill线程的小技巧
        mysql_con -e 'select concat("kill ",id,";") from  information_schema.PROCESSLIST where command="Query" or command="Execute" into outfile "/tmp/kill.sql";'
        mysql_con -e "source /tmp/kill.sql"
        sleep 2    ###给kill一个执行和缓冲时间
        ###关闭本机keepalived       
        echo -e "`date "+%F  %H:%M:%S"`    -----stop keepalived-----" >> ${error_log}
        echo "1234567890" | sudo -S service keepalived stop >> ${error_log}
        echo "DB1 keepalived 已停止" >> ${error_log}
        echo -e "\n---------------------------------------------------------\n" >> ${error_log}
    else
        echo -e "`date "+%F  %H:%M:%S"`    -----query ok after 30s-----" >> ${error_log}
        echo -e "\n---------------------------------------------------------\n" >> ${error_log}
    fi
}

###检查开始: 执行查询
excute_query
if [ $? -ne 0 ];then
    service mysqld status &>/dev/null
    if [ $? -ne 0 ];then
        service_error
    else
        query_error
    fi
fi
```

创建keepalived check\_mysql脚本执行结果目录及日志文件并授权

```
> sudo mkdir /etc/keepalived/logs
> sudo touch /etc/keepalived/logs/check_mysql.err
> sudo touch /etc/keepalived/logs/state_change.log
> sudo chmod 666 /etc/keepalived/logs/check_mysql.err
> sudo chmod 666 /etc/keepalived/logs/state_change.log
```

Master1恢复后手动切回Master 1为keepalived主的脚本

[~/retomaster.sh]

```
#!/bin/bash
###手动执行将主库切换回DB1的操作

mysql_con='mysql -uroot -p123456'
 
echo -e "`date "+%F  %H:%M:%S"`    -----change to BACKUP manually-----" >> /etc/keepalived/logs/state_change.log
echo -e "`date "+%F  %H:%M:%S"`    -----set read_only = 1 on DB2-----" >> /etc/keepalived/logs/state_change.log
$mysql_con -e "set global read_only = 1;" 2>> /etc/keepalived/logs/state_change.log

###kill掉当前客户端连接
echo -e "`date "+%F  %H:%M:%S"`    -----kill current client thread-----" >> /etc/keepalived/logs/state_change.log
rm -f /tmp/kill.sql &>/dev/null
###这里其实是一个批量kill线程的小技巧
$mysql_con -e 'select concat("kill ",id,";") from  information_schema.PROCESSLIST where command="Query" or command="Execute" into outfile "/tmp/kill.sql";'
$mysql_con -e "source /tmp/kill.sql" 2>> /etc/keepalived/logs/state_change.log
sleep 2    ###给kill一个执行和缓冲时间
 
###确保DB1已经追上了,下面的repl为复制所用的账户，-h后跟DB1的内网IP
log_file_pos=`mysql -uatompi -p123456 -h192.168.1.143 -e "show slave status\G;"|egrep -w "Master_Log_File|Read_Master_Log_Pos|Relay_Master_Log_File|Exec_Master_Log_Pos"`
Master_Log_File=`echo $log_file_pos|awk '{print $2}'`
Read_Master_Log_Pos=`echo $log_file_pos|awk '{print $4}'`
Relay_Master_Log_File=`echo $log_file_pos|awk '{print $6}'`
Exec_Master_Log_Pos=`echo $log_file_pos|awk '{print $8}'`
until [ $Read_Master_Log_Pos = $Exec_Master_Log_Pos -a $Master_Log_File = $Relay_Master_Log_File ]
do
    echo -e "`date "+%F  %H:%M:%S"`    -----DB1 Exec_Master_Log_Pos($exec_pos) is behind Read_Master_Log_Pos($read_pos), wait......" >> /etc/keepalived/logs/state_change.log
    sleep 1
done

###然后解除DB1的read_only属性
echo -e "`date "+%F  %H:%M:%S"`    -----set read_only = 0 on DB1-----" >> /etc/keepalived/logs/state_change.log
ssh 192.168.1.143 'mysql -uroot -p123456 -e "set global read_only = 0;" && /etc/init.d/keepalived start' 2>> /etc/keepalived/logs/state_change.log
 
###重启DB2的keepalived使VIP漂移到DB1
echo -e "`date "+%F  %H:%M:%S"`    -----make VIP move to DB1-----" >> /etc/keepalived/logs/state_change.log
echo "1234567890" | sudo -S service keepalived stop >> /etc/keepalived/logs/state_change.log
 
echo "DB2 keepalived转为BACKUP状态，线上数据库切换至DB1" >> /etc/keepalived/logs/state_change.log
 
echo -e "--------------------------------------------------\n" >> /etc/keepalived/logs/state_change.log
```

赋予以上脚本可执行权限

```
> sudo chmod +x ~/retomaster.sh
> sudo chmod +x /etc/keepalived/check_mysql.sh
```

### Master 2
[/etc/keepalived/keepalived.conf]

```
! Configuration File for keepalived

vrrp_instance VI_1 {
    state BACKUP
    interface eth0
    virtual_router_id 51
    priority 90
    advert_int 1
    authentication {
        auth_type PASS
        auth_pass 123456789
    }
    notify_master /etc/keepalived/notify_master_mysql.sh    #此条指令告诉keepalived发现自己转为MASTER后执行的脚本
    virtual_ipaddress {
        192.168.1.140/24
    }
}
```

[/etc/keepalived/notify\_master\_mysql.sh]

```
#!/bin/bash
###当keepalived监测到本机转为MASTER状态时，执行该脚本

change_log=/etc/keepalived/logs/state_change.log
mysql_con='mysql -uroot -p123456'
echo -e "`date "+%F  %H:%M:%S"`   -----keepalived change to MASTER-----" >> $change_log
 
slave_info() {
    ###统一定义一个函数取得slave的position、running、和log_file等信息
    ###根据函数后面所跟参数来决定取得哪些数据
    if [ $1 = slave_status ];then
        slave_stat=`${mysql_con} -e "show slave status\G;"|egrep -w "Slave_IO_Running|Slave_SQL_Running"`
        Slave_IO_Running=`echo $slave_stat|awk '{print $2}'`
        Slave_SQL_Running=`echo $slave_stat|awk '{print $4}'`
    elif [ $1 = log_file -a $2 = pos ];then
        log_file_pos=`${mysql_con} -e "show slave status\G;"|egrep -w "Master_Log_File|Read_Master_Log_Pos|Relay_Master_Log_File|Exec_Master_Log_Pos"`
        Master_Log_File=`echo $log_file_pos|awk '{print $2}'`
        Read_Master_Log_Pos=`echo $log_file_pos|awk '{print $4}'`
        Relay_Master_Log_File=`echo $log_file_pos|awk '{print $6}'`
        Exec_Master_Log_Pos=`echo $log_file_pos|awk '{print $8}'`
    fi
}
 
action() {
    ###经判断'应该&可以'切换时执行的动作
    echo -e "`date "+%F  %H:%M:%S"`    -----set read_only = 0 on DB2-----" >> $change_log
 
    ###解除read_only属性
    ${mysql_con} -e "set global read_only = 0;" 2>> $change_log
 
    echo "DB2 keepalived转为MASTER状态，线上数据库切换至DB2" >> $change_log
 
    echo -e "---------------------------------------------------------\n" >> $change_log
}
 
slave_info slave_status
if [ $Slave_SQL_Running = Yes ];then
    i=0    #一个计数器
    slave_info log_file pos
        ###判断从master接收到的binlog是否全部在本地执行(这样仍无法完全确定从库已追上主库，因为无法完全保证io_thread没有延时(由网络传输问题导致的从库落后的概率很小)
    until [ $Master_Log_File = $Relay_Master_Log_File -a $Read_Master_Log_Pos = $Exec_Master_Log_Pos ]
     do
        if [ $i -lt 10 ];then    #将等待exec_pos追上read_pos的时间限制为10s
            echo -e "`date "+%F  %H:%M:%S"`    -----Relay_Master_Log_File=$Relay_Master_Log_File,Exec_Master_Log_Pos=$Exec_Master_Log_Pos is behind Master_Log_File=$Master_Log_File,Read_Master_Log_Pos=$Read_Master_Log_Pos, wait......" >> $change_log    #输出消息到日志，等待exec_pos=read_pos
            i=$(($i+1))
            sleep 1
            slave_info log_file pos
        else
            echo -e "The waits time is more than 10s,now force change. Master_Log_File=$Master_Log_File Read_Master_Log_Pos=$Read_Master_Log_Pos Relay_Master_Log_File=$Relay_Master_Log_File Exec_Master_Log_Pos=$Exec_Master_Log_Pos" >> $change_log
            action
            exit 0
        fi
    done
    action 
 
else
    slave_info log_file pos
    echo -e "DB2's slave status is wrong,now force change. Master_Log_File=$Master_Log_File Read_Master_Log_Pos=$Read_Master_Log_Pos Relay_Master_Log_File=$Relay_Master_Log_File Exec_Master_Log_Pos=$Exec_Master_Log_Pos" >> $change_log
    action
fi
```

创建keepalived notify\_master\_mysql.sh脚本执行结果目录及日志文件并授权

```
> sudo mkdir /etc/keepalived/logs
> sudo touch /etc/keepalived/logs/state_change.log
> sudo chmod 666 /etc/keepalived/logs/state_change.log
```

添加keepalived vip 防火墙规则

```
> sudo vim /etc/sysctl.conf
# 添加 net.ipv4.ip_nonlocal_bind = 1
> sudo sysctl -p
```

启动 keepalived

```
> sudo service keepalived start
> tail /var/log/syslog  #查看日志
```

# 测试


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)