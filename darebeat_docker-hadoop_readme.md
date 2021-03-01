# docker-hadoop

## 准备软件包
1. [jdk1.7.0_60下载](http://119.254.110.32:8081/download/jdk1.7.0_60.tar.gz)
2. [hadoop-2.7.2下载](http://mirrors.cnnic.cn/apache/hadoop/common/hadoop-2.7.2/hadoop-2.7.2.tar.gz)


## 生成镜像
```sh
cd .
# 如果上面文件下载到工程目录，使用本地源生成镜像
# 本地源生成镜像
bin/build.sh local

# 在线生成镜像
bin/build.sh
```

## 部署容器
```sh
# 启动hadoop集群
bin/hadoop-cluster.sh start 3

# 卸载hadoop集群
bin/hadoop-cluster.sh stop 3
```

## 启动/关闭hadoop集群
```sh
$HADOOP_HOME/sbin/start-all.sh -y
$HADOOP_HOME/sbin/stop-all.sh

# 验证服务是否启动
$JAVA_HOME/bin/jps -l
```

## 网页管理地址
+ NameNode: [http://localhost:8088](http://localhost:8088)
+ ResourceManager: [http://localhost:50070](http://localhost:50070)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)