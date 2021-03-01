#基于Docker构建Hadoop高可用集群
#NameNode HA架构图
![NameNode HA架构图](http://git.oschina.net/uploads/images/2016/0710/010437_70227c20_769879.png "NameNode HA架构图")
![NameNode HA架构图](http://git.oschina.net/uploads/images/2016/0715/235200_db3c025e_769879.png "NameNode HA架构图")
#ResourceManager HA架构图
![ResourceManager HA架构图](http://git.oschina.net/uploads/images/2016/0715/235249_0be85c97_769879.png "ResourceManager HA架构图")
#快速开始(Getting Started)
##1.初始化配置(initialize configuration)
```
python initialize.py
```
##2.创建Docker镜像(docker build image)
```
python build-image.py
```
##3.启动容器(docker run container)
```
python run-container.py
```
##* 4~9.步骤可直接启动如下Python脚本
```
python run-cluster.py
```
##4.配置和启动Zookeeper集群
```
docker exec -it hadoop-zookeeper1 bash
echo 1 >> ~/zookeeper/myid
zkServer.sh start
exit
docker exec -it hadoop-zookeeper2 bash
echo 2 >> ~/zookeeper/myid
zkServer.sh start
exit
docker exec -it hadoop-zookeeper3 bash
echo 3 >> ~/zookeeper/myid
zkServer.sh start
exit
```
##5.启动Journalnode
```
docker exec -it hadoop-journalnode1 bash
hadoop-daemon.sh start journalnode
exit
docker exec -it hadoop-journalnode2 bash
hadoop-daemon.sh start journalnode
exit
docker exec -it hadoop-journalnode3 bash
hadoop-daemon.sh start journalnode
exit
```
##6.初始化namenode
```
docker exec -it hadoop-namenode1 bash
hdfs namenode -format
hadoop-daemon.sh start namenode
exit
docker exec -it hadoop-namenode2 bash
hdfs namenode -bootstrapStandby
hadoop-daemon.sh start namenode
exit
```
##7.初始化zkfc
```
docker exec -it hadoop-namenode1 bash
hdfs zkfc -formatZK
exit
```
##8.启动hdfs集群
```
docker exec -it hadoop-journalnode1 bash
hadoop-daemon.sh stop journalnode
exit
docker exec -it hadoop-journalnode2 bash
hadoop-daemon.sh stop journalnode
exit
docker exec -it hadoop-journalnode3 bash
hadoop-daemon.sh stop journalnode
exit
docker exec -it hadoop-namenode2 bash
hadoop-daemon.sh stop namenode
hadoop-daemon.sh start zkfc
exit
docker exec -it hadoop-namenode1 bash
hadoop-daemon.sh stop namenode
start-dfs.sh
hadoop-daemon.sh start zkfc
exit
```
##9.启动yarn集群
```
docker exec -it hadoop-resourcemanager1 bash
start-yarn.sh
exit

docker exec -it hadoop-resourcemanager2 bash
yarn-daemon.sh start resourcemanager
exit
```
##10.运行wordcount实例
```
docker exec -it hadoop-resourcemanager1 bash
./run-wordcount.sh
exit
```
#关闭Hadoop HA集群
##1. 关闭所有Docker容器
```
python stop-container.py
```
#重新启动Hadoop HA集群
##1. 开启所有已关闭的容器
```
python start-container.py
```
##* 2~4.步骤可直接启动如下Python脚本
```
python start-cluster.py
```
##2.启动Zookeeper集群
```
docker exec -it hadoop-zookeeper1 bash
zkServer.sh start
exit
docker exec -it hadoop-zookeeper2 bash
zkServer.sh start
exit
docker exec -it hadoop-zookeeper3 bash
zkServer.sh start
exit
```
##3.启动hdfs集群
```
docker exec -it hadoop-namenode1 bash
start-dfs.sh
hadoop-daemon.sh start zkfc
exit
docker exec -it hadoop-namenode2 bash
hadoop-daemon.sh start zkfc
exit
```
##4.启动yarn集群
```
docker exec -it hadoop-resourcemanager1 bash
start-yarn.sh
exit

docker exec -it hadoop-resourcemanager2 bash
yarn-daemon.sh start resourcemanager
exit
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)