

# Ego-Shop-Dubbo

# 一、项目的开发环境

## 1.1 项目的版本控制

```
gitlab + git
```

## 1.2 项目的开发软件

windows10 + STS + JDK.18

# 二、技术选型

## 2.1 后端的技术选型

Spring Boot + Mybaits plus + Dubbo + ZookeeperCluster + RedisCluster + SolrCloud + ActiveMQCluster + Shiro + Swagger-UI + Orika + FST  + Hutool +  HibernateVaildator + Mycat + Nginx + FastDFS + Docker + ECS + WeChatApi + AiliPay

## 2.2 前端的技术选型

Vue + Element + Axios + js-cookie + uni-app 

## 2.3 前后端交互的方式

后端就是Restful 风格的开发

Restful： url 地址就是资源，对资源的操作，使用Http动词来完成(POST DELETE PUT GET)

前台: 使用axios(ajax) 来异步获取我们的后端的数据

# 三、项目的架构图（**）

![](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/01 项目的架构.png)

# 四、项目的搭建

采用Maven 分模块构建项目



![](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/02 项目的搭建示意图.png)

# 五、软件的准备（开发使用单机版，部署使用集群）(使用docker)

https://hub.docker.com/

## 5.0 mysql

```bash
docker run --name ego-mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.7 --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```



## 5.1 zokeeper

```bash
docker run --name ego-zk -p 2181:2181 -d zookeeper
```



## 5.2 redis

```bash
docker run --name redis -p 6379:6379 -d redis
```



## 5.3 activemq

```bash
docker run --name ego-mq -p 61616:61616 -p 8161:8161 -d rmohr/activemq
```



## 5.4 dubbo-admin

```bash
docker run --name ego-dubbo-admin -d \
-p 8080:8080 \
-e dubbo.registry.address=zookeeper://172.19.172.75:2181 \
-e dubbo.admin.root.password=root \
-e dubbo.admin.guest.password=guest \
chenchuxin/dubbo-admin 
```



## 5.5 Solr

```bash
docker run --name ego-solr -p 8983:8983 -d solr:7.7.2
```



## 5.6 nginx

```bash
docker run --name ego-nginx -p 80:80 -d nginx
```



## 5.7 Mycat

```bash
docker run --name ego-mycat -p 8066:8066 -d longhronshens/mycat-docker
```

# 六、ECS 服务器的准备和软件的安装

## 6.1 准备ecs 服务器

最好的配置 2核心8G(https://item.jd.com/56523493267.html#crumb-wrap)



![1576550278129](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576550278129.png)

![1576550369680](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576550369680.png)

![1576550390471](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576550390471.png)

## 6.2 ecs 的软件安装

### 6.2.1 连接ecs

![1576550547284](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576550547284.png)

#### Docker安装（http://get.daocloud.io/）

Docker 的 [安装资源文件 ](https://get.docker.com/)存放在Amazon S3，会间歇性连接失败。所以安装Docker的时候，会比较慢。
你可以通过执行下面的命令，高速安装Docker。

```bash
curl -sSL https://get.daocloud.io/docker | sh
```

![1576550697145](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576550697145.png)

适用于Ubuntu，Debian,Centos等大部分Linux，会3小时同步一次Docker官方资源

安装成功了：

![1576550898601](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576550898601.png)

#### Docker的镜像加速配置

在新版的docker 里面，没有docker 该文件夹

我们需要新建该文件夹，才能往里面放文件：

```bash
curl -sSL https://get.daocloud.io/daotools/set_mirror.sh | sh -s http://f1361db2.m.daocloud.io
```

该脚本可以将 --registry-mirror 加入到你的 Docker 配置文件 /etc/docker/daemon.json 中。适用于 Ubuntu14.04、Debian、CentOS6 、CentOS7、Fedora、Arch Linux、openSUSE Leap 42.1，其他版本可能有细微不同。更多详情请访问文档。

![1576551049172](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576551049172.png)

![1576551080833](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576551080833.png)

重启docker

```bash
systemctl restart docker
```

### 6.2.2 安装wget

```bash
yum -y install wget
```

![1576551184578](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576551184578.png)

### 6.2.3 telnet（ping 端口）

```bash
yum -y install telnet
```

![1576551256193](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576551256193.png)

## 6.3 使用docker 安装我们的所需要的软件

软件安装完毕后，测试一下

# 七、Gitlab的搭建和配置（你们不需要搞，了解，最少2核4G）

## 7.1  准备gitlab的文件夹

```bash
mkdir -p /usr/local/gitlab/gitlab-config
mkdir -p /usr/local/gitlab/gitlab-logs
mkdir -p /usr/local/gitlab/gitlab-data
```

## 7.2 运行gitlab的容器

```bash
docker run -d \
    --hostname 117.48.231.143 \
    -p 80:80 \
    -p 443:443 \
    -p 22:22 \
    --name 0704gitlab \
    --restart unless-stopped \
    -v /usr/local/gitlab/gitlab-config:/etc/gitlab \
    -v /usr/local/gitlab/gitlab-logs:/var/log/gitlab \
    -v /usr/local/gitlab/gitlab-data:/var/opt/gitlab \
    twang2218/gitlab-ce-zh:11.1.4
```



## 7.3 端口的说明

80 http 服务的端口

443 https的端口

22 ssh的端口

# 八、注册账号，配置密钥

## 8.1 注册账号

![1576553945738](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576553945738.png)

![1576553971563](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576553971563.png)

## 8.2 配置密钥

### 1 在windows 生产密钥

![1576554031912](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576554031912.png)

### 2 配置公钥

![1576554068749](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576554068749.png)

![1576554105176](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576554105176.png)

复制公钥：

![1576554145180](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576554145180.png)



添加完毕后：

![1576554174371](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576554174371.png)

# 九、项目的拉取和创建

## 9.1 在公司里面

项目已经创建后，并且正在开发中。

我先把项目拉取下来，看看别人的代码

```bash
git clone 项目的地址
```



## 9.2 在开发时（**每个人都要创建）

### 9.2.1 创建项目

![1576554350415](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576554350415.png)



![1576554446043](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576554446043.png)

### 9.2.2 clone 我们的项目

![1576554533664](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576554533664.png)

设置我们的基本信息：

```bash
git config --global user.name "梁天东"
git config --global user.email "liangtiandong@live.com"
```

![1576554596486](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576554596486.png)

克隆项目：

复制项目的地址：

![1576554635671](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576554635671.png)

clone：



![1576554671902](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576554671902.png)







![1576554727621](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576554727621.png)

原因：

   1 公钥没有设置成功，重新设置一遍就好了

  2 之前你设置过公钥，但是修改了，删除密钥文件夹里面：

![1576554836101](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576554836101.png)





再次clone：

![1576554899474](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576554899474.png)

 

### 9.2.3 上传项目的Readme.md  文件

复制文件到ego-shop 里面

![1576555006588](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576555006588.png)

提交该文件：

```bash
git add *
git commit -m "初始化项目"
git push
```

### 9.2.4 在gitlab 里面，图片无法显示的原因

路径不正确：

![1576555244173](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576555244173.png)



![1576555279723](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576555279723.png)

### 9.2.5 地址修改后，再次提交项目就可以了

![1576555407897](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576555407897.png)

![1576563710562](http://117.48.231.143/liangtiandong/ego-shop/raw/master/assert/1576563710562.png)



地址：http://117.48.231.143/xxx/ego-shop/raw/master/assert/

xxx 换成你的名称就可以了



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)