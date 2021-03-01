# CDH安装脚本

#### 介绍

- CDH安装 集群/单机 安装脚本
- 系统： CentOS-7.7 最小化安装
- 脚本依赖软件包 perl, expect psmisc(需要联网安装或挂载完整光盘镜像配置本地安装源)
- JDK MySQL 为二进制方式安装

#### 单机安装教程

1.配置主机信息 host:主机名 ip:安装集群节点IP 一一对应

    host=node01
    ip=192.168.0.71

2.配置 hosts 解析

    echo "$ip    $host"  >> /etc/hosts

3.更改主机名

    hostnamectl set-hostname $host

4.配置秘钥登录(替换 $root_pass 为节点root密码)

    bash  > /etc/hosts
        for ((i=0;i > /etc/hosts
        done
    fi

3.更改主机名

    for ((i=0;i  cloudera-scm-server

```shell
source /etc/profile
cat > /usr/lib/systemd/system/cloudera-scm-server.service    cloudera-scm-agent

```shell
source /etc/profile
cat > /usr/lib/systemd/system/cloudera-scm-agent.service  <<EOF
[Unit]
Description=cloudera-scm-agent
After=network.target

[Service]
TimeoutSec=10
Type=forking
ExecStart=/opt/cloudera-manager/cm-5.16.1/etc/init.d/cloudera-scm-agent start
Environment="JAVA_HOME=$JAVA_HOME" "JRE_HOME=$JRE_HOME"
ExecStop=/opt/cloudera-manager/cm-5.16.1/etc/init.d/cloudera-scm-agent stop

[Install]
WantedBy=multi-user.target
EOF

# 跟随系统启动
systemctl daemon-reload
systemctl enable cloudera-scm-agent.service
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)