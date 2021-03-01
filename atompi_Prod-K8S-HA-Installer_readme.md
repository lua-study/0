# 基于 ansible kubeadmin 一键安装 k8s HA （ stacked 模式）

stacked 模式，即 etcd 与 master 共用节点。

## 系统要求

1. CentOS 7+

2. 所有节点可以连接公网，或者内网环境存在完备的内部源，并且所有节点已配置可以通过 yum 安装以下源的 packages 。

yum 源列表

```
CentOS 7
docker-ce
kubernetes
elrepo
epel
```

## 安装命令执行端操作（ 远程控制端或者 k8s-m1 ）：

### 安装 ansible 2.7+ 版本

```
yum install -y epel-release
yum install -y ansible
```

### 修改 ssh 配置，生成 sshkey

```
ssh-keygen -t rsa -N '' -f /root/.ssh/id_rsa -q
sed -i "s/.*StrictHostKey.*/StrictHostKeyChecking no/" /etc/ssh/ssh_config
```

### 上传并解压安装包

```
tar -zxf Prod-K8S-HA-Installer.tar.gz
cd Prod-K8S-HA-Installer
```

解压后目录树：

```
Prod-K8S-HA-Installer/
├── 0_init_main_node.sh
├── 3_install_elb.sh
├── 4_install_master.sh
├── 5_add_node.sh
├── 6_install_addons.md
├── add_node
├── common_scripts
├── config.ini
├── init_host
├── install_addons
├── install_master_elb
├── install_master
├── logs
├── README.md
└── tempshell.md
```

### 修改配置文件 `config.ini`

## 开始安装

### 0 初始化节点

```
sh 0_init_main_node.sh
```

### 安装 elb

```
sh 3_install_master_elb.sh
```

### 安装 master

```
sh 4_install_master.sh
```

### 安装 system node

```
source ./config.ini
sh 5_add_node.sh $SYSNODE_IP_1 $SYSNODE_PASSWD_1 $SYSNODE_HOSTNAME_1
sh 5_add_node.sh $SYSNODE_IP_2 $SYSNODE_PASSWD_2 $SYSNODE_HOSTNAME_2
```

### 安装插件

见[6_install_addons.md](6_install_addons.md)

### 添加 work node

```
sh 5_add_node.sh IP PASSWD HOSTNAME
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)