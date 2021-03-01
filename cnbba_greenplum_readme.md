# 基于 Ansible-Playbook 自动化部署 GreenPlum 数据仓库
> 本项目是通过 Ansible-Playbook 剧本,自动化部署安装 GreenPlum 数据仓库。
> 版本是：v1.1
> This project uses ansible-playbook script to perform automated deployment and installation of greenplus data warehouse.
> version: v1.1

# 第1部分 项目部署
## 1.1 软件版本说明
|软件名称|软件版本|
|:----------------|:-------------|
|greenplum-db     | db   v5.10.0 |
|greenplum-cc-web | gpcc v4.3.0  |

## 1.2 部署环境
|序号|ip地址|主机名|内存|系统版本|内核版本|
|:---|:-------------|:-----------|:---|:--------------|:------------------------|
|1   |192.168.61.61 |gpmaster61  |16Gb|CentOS 7.5.1804|3.10.0-862.9.1.el7.x86_64|
|2   |192.168.61.62 |gpsegment62 |16Gb|CentOS 7.5.1804|3.10.0-862.9.1.el7.x86_64|
|3   |192.168.61.63 |gpsegment63 |16Gb|CentOS 7.5.1804|3.10.0-862.9.1.el7.x86_64|
|4   |192.168.61.64 |gpsegment64 |16Gb|CentOS 7.5.1804|3.10.0-862.9.1.el7.x86_64|

## 1.3 基础环境(需要重启)
```
/usr/bin/bash 01_base_gpdb.yml
```

## 1.4 初始化安装
```
/usr/bin/bash 02_deploy_gpdb.yml
```

## 1.5 web监控访问地址
```
http://192.168.61.61:28080
# 用户/密码：gpmon/gpmon
```

## 1.6 项目结构
```
/playbook/greenplum/
├── 01_base_gpdb.yml                                   # 基础环境部署脚本(需要重启)
├── 02_deploy_gpdb.yml                                 # 部署 GreenPlum 脚本
├── ansible.cfg                                        # GreenPlum Ansible 配置文件 
├── hosts                                              # 部署主机列表
├── LICENSE                                            
├── README.md
├── remove_gpdb.yml                                    # 清理 GreenPlum 脚本
└── roles
    ├── base_gpdb
    │   ├── files
    │   │   ├── 20-nproc.conf
    │   │   ├── create_hosts.sh
    │   │   ├── gpdb_env.sh
    │   │   ├── hosts                                  # 根据需求修改 
    │   │   ├── limits.conf
    │   │   ├── sysctl.conf
    │   │   └── update_hosts.sh
    │   ├── meta
    │   │   └── main.yml
    │   ├── tasks
    │   │   └── main.yml
    │   └── templates
    │       ├── blockdev-setra-sdb
    │       ├── blockdev-setra-sdb.service
    │       ├── disable-thp.service
    │       └── disable-transparent-hugepages
    ├── greenplum
    │   ├── defaults
    │   │   └── main.yml
    │   ├── files
    │   │   ├── all_nodes                              # 根据需求修改
    │   │   ├── create_all.sh
    │   │   ├── greenplum-cc-web.tar.gz
    │   │   ├── greenplum-db.tar.gz
    │   │   ├── init_gpdb.sh
    │   │   ├── key.tar.gz
    │   │   ├── seg_nodes                              # 根据需求修改
    │   │   └── upgrade_seg.sh
    │   ├── meta
    │   │   └── main.yml
    │   ├── tasks
    │   │   └── main.yml
    │   ├── templates
    │   │   ├── bash_profile.j2
    │   │   └── gpinitsystem_config.j2
    │   └── vars
    │       └── main.yml
    └── system_env
        ├── files
        │   ├── audit_shell.sh
        │   ├── bashrc
        │   ├── centos7-ali.repo
        │   ├── epel-release-latest-7.noarch.rpm
        │   ├── hosts                                  # 根据需求修改
        │   ├── resolv.conf
        │   └── sshd_config
        └── tasks
            └── main.yml

16 directories, 41 files
```

# 第2部分 GreenPlum 常用命令
## 2.1 gpstart
|命令 参数| 作用 |
|:----------|:--------|
|gpstart -a | 快速启动|
|gpstart -d | 指定数据目录（默认值：$MASTER_DATA_DIRECTORY）
|gpstart -q | 在安静模式下运行。命令输出不显示在屏幕，但仍然写入日志文件。
|gpstart -m | 以维护模式连接到Master进行目录维护。例如：$ PGOPTIONS='-c gp_session_role=utility' psql postgres
|gpstart -R | 管理员连接
|gpstart -v | 显示详细启动信息

## 2.2 gpstop
|命令参数  | 作用 |
|:---------|:-----|
|gpstop -a | 快速停止
|gpstop -d | 指定数据目录（默认值：$MASTER_DATA_DIRECTORY）
|gpstop -m | 维护模式
|gpstop -q | 在安静模式下运行。命令输出不显示在屏幕，但仍然写入日志文件。
|gpstop -r | 停止所有实例，然后重启系统
|gpstop -u | 重新加载配置文件 postgresql.conf 和 pg_hba.conf
|gpstop -v | 显示详细启动信息
|gpstop -M fast      | 快速关闭。正在进行的任何事务都被中断。然后滚回去。
|gpstop -M immediate | 立即关闭。正在进行的任何事务都被中止。不推荐这种关闭模式，并且在某些情况下可能导致数据库损坏需要手动恢复。
|gpstop -M smart     | 智能关闭。如果存在活动连接，则此命令在警告时失败。这是默认的关机模式。
|gpstop --host hostname | 停用segments数据节点，不能与-m、-r、-u、-y同时使用 

## 2.3 gpstate
|命令 参数  | 作用 |
|:----------|:-----|
|gpstate -b | 显示简要状态
|gpstate -c | 显示主镜像映射
|gpstart -d | 指定数据目录（默认值：$MASTER_DATA_DIRECTORY）
|gpstate -e | 显示具有镜像状态问题的片段
|gpstate -f | 显示备用主机详细信息
|gpstate -i | 显示GRIPLUM数据库版本
|gpstate -m | 显示镜像实例同步状态
|gpstate -p | 显示使用端口
|gpstate -Q | 快速检查主机状态
|gpstate -s | 显示集群详细信息
|gpstate -v | 显示详细信息

## 2.4 激活备库流程
|命令参数| 作用 |
|:-------|:-----|
|gpactivatestandby -d 路径 | 使用数据目录绝对路径，默认：$MASTER_DATA_DIRECTORY
|gpactivatestandby -f | 强制激活备份主机
|gpactivatestandby -v | 显示此版本信息


## 2.5 在新主库上，初始化一个后备Master
|命令参数| 作用 |
|:-------|:-----|
|gpinitstandby -s 备库名称 | 指定新备库
|gpinitstandby -D | debug 模式
|gpinitstandby -r | 移除备用机

## 2.6 集群恢复
|命令参数| 作用 |
|:-------|:-----|
|gprecoverseg -a | 快速恢复
|gprecoverseg -i | 指定恢复文件
|gprecoverseg -d | 指定数据目录
|gprecoverseg -l | 指定日志文件
|gprecoverseg -r | 平衡数据
|gprecoverseg -s | 指定配置空间文件
|gprecoverseg -o | 指定恢复配置文件
|gprecoverseg -p | 指定额外的备用机
|gprecoverseg -S | 指定输出配置空间文件


## 2.7 备份/恢复
### 使用pg_dump和pg_restore实现数据库的备份与恢复
### 使用dump格式备份和恢复
```
pg_dump -U gpadmin -Fc chinadaas > chinadaas.dump
pg_restore -U gpadmin -d chinadaas chinadaas.dump > chinadaas_dump.txt 2>&1
```

### 使用tar格式备份和恢复
```
pg_dump -U gpadmin -Ft chinadaas >chinadaas.tar
pg_restore -U gpadmin -d chinadaas chinadaas.tar > chinadaas_tar.txt 2>&1
```

# 第3部分 数据库访问
### 表 1. 最常用的客户端应用
|命令名称|用法|
|:-------|:---|
|createdb  |创建一个新数据库
|createlang|定义一种新的过程语言
|createuser|定义一个新的数据库角色
|dropdb|移除一个数据库
|droplang|移除一种过程语言
|dropuser|移除一个角色
|psql|PostgreSQL交互式终端
|reindexdb|对一个数据库重建索引
|vacuumdb|对一个数据库进行垃圾收集和分析

## 3.1 创建用户
```
CREATE USER 用户名 WITH PASSWORD '密码'
alter user gpadmin encrypted password 'gpadmin';
```

## 3.2 创建模式
```
CREATE SCHEMA myschema;
```

## 3.3 删除模式
```
DROP SCHEMA myschema;
```

## 3.4 查询当前连接
```
psql -c "select * from pg_stat_activity;"
select pg_cancel_backend(客户端进程ID);
如果无法杀掉则使用
select pg_terminate_backend(客户端进程ID);
```

## 3.5 查看数据库
```
psql -c "select pg_size_pretty(pg_database_size('test'));"
```

## 3.6 表占用空间
```
psql -c "select pg_size_pretty(pg_relation_size('schema.test'));"
```

## 3.7 表统计
```
select relname from pg_class t where t.relname like 'ods%';
select relname from pg_class t where t.relname like 'kn%';
```

## 3.8 统计资源
```
select gp_segment_id,count(*) from test group by 1 ;
```

## 3.9 查询集群状态
```
SELECT dbid, content, address, port, replication_port, fselocation as datadir FROM gp_segment_configuration, pg_filespace_entry WHERE dbid=fsedbid ORDER BY dbid;
```

## 3.10 查看实例配置和状态
```
select * from gp_segment_configuration order by 1;
```

# 第4部分 系统优化
## 4.1 收集统计信息，回收空间
```
# 定期使用回收垃圾和收集统计信息，尤其在大数据量删除，导入以后，非常重要
Vacuum analyze tablename
```
## 4.2 进程监控：
```
select * from pg_stat_activity  where waiting ='t' ORDER BY current_query;    select * from pg_stat_activity  where waiting ='t' ORDER BY sess_id;
select * from pg_stat_activity  where waiting ='f' ORDER BY current_query;    select * from pg_stat_activity  where waiting ='f' ORDER BY sess_id;
select * from pg_tablespace;
select * from pg_filespace;
```

## 4.3 查看数据分布
```
select * from pg_filespace_entry;
SELECT spcname, fsname,fsedbid,fselocation FROM pg_tablespace pgts, pg_filespace pgfs,pg_filespace_entry pgfse WHERE pgts.spcfsoid=pgfse.fsefsoid AND pgfse.fsefsoid=pgfs.oid ORDER BY 1,3;
```

## 4.4 查看日志级别
```
# 控制写到服务器日志里的信息的详细程度。有效值是 DEBUG5， DEBUG4，DEBUG3，DEBUG2， DEBUG1，INFO，NOTICE， WARNING ，ERROR，LOG， FATAL，和 PANIC。 每个级别都包含它后面的级别。越靠后的数值发往服务器日志的信息越少。 缺省是 NOTICE。请注意 LOG 和 client_min_messages 里面的同名级别优先级不同。 只有超级用户可以修改这个设置。[]()
show log_min_messages;

# 这个选项控制那些信息发送到客户端。 有效的数值是 DEBUG5，DEBUG4， DEBUG3，DEBUG2， DEBUG1，LOG，NOTICE， WARNING 和 ERROR。 每个级别包含所有它后面的级别，级别越靠后，发送的信息越少。 缺省是 NOTICE。这里的 LOG 和 log_min_messages 里面的有不同的级别。
show client_min_messages;
```

## 4.5 查看数据库备份
```
select pg_start_backup('backup baseline');
select pg_stop_backup();
```

## 4.6 常看数据库.conf配置
```
show all
```

## 4.7 查看当前日期属于一年中第几周
```
select EXTRACT(week from TIMESTAMP '2018-05-11');
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)