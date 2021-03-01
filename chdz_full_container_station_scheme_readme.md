# 全容器站方案

#### 1.交付docker环境(centos7.2-ucloud)

###### //修改时区为上海
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

###### //禁用seliunx
vi /etc/selinux/config
###### //将SELINUX=enforcing改为SELINUX=disabled 重启机器即可

###### //修改服务器hostName,这里修改成内网IP便于理解 xxx-xxx-xxx-xxx 不可以用"."
hostnamectl --static set-hostname  

###### //关闭firewall
###### //停止firewall
systemctl stop firewalld.service

###### //禁止firewall开机启动
systemctl disable firewalld.service

###### //查看默认防火墙状态（关闭后显示notrunning，开启后显示running）
firewall-cmd --state

###### //创建docker软链接,映射数据盘,系统默认空间是不足的。
cd /data/

mkdir docker

ln -s /data/docker /var/lib/docker

###### //安装依赖
yum -y install policycoreutils-python selinux-policy-base selinux-policy-targeted libseccomp libtool-ltdl device-mapper-libs

###### //安装docker,这里以rmp包方式安装
rpm -ivh docker-engine-selinux-1.12.6-1.el7.centos.noarch.rpm

###### //会出现如下错误,可以忽略,至今没有对线上docker环境有任何影响
###### //setsebool:  SELinux is disabled.
###### //Re-declaration of type docker_t
###### //Failed to create node
###### //Bad type declaration at /etc/selinux/targeted/tmp/modules/400/docker/cil:1
###### ///usr/sbin/semodule:  Failed!

###### //安装docker主程序
rpm -ivh docker-engine-1.12.6-1.el7.centos.x86_64.rpm

###### //启动docker
service docker start

###### //查看docker信息系
docker info

###### //增加docker国内镜像加速站点与私有镜像库地址
###### //备注: /etc/docker/daemon.json是json格式{}
vi /etc/docker/daemon.json
###### //增加"registry-mirrors": ["https://registry.docker-cn.com"]

###### //增加http方式镜像库
vi /etc/docker/daemon.json
###### //增加"insecure-registries":["你镜像库的IP:你镜像库的端口"],这里为了演示方便就使用当前主机的内网IP
###### //添加完成如下,重启docker生效
###### //{"registry-mirrors": ["https://registry.docker-cn.com"],"insecure-registries":["10.23.187.165:5000"]}

service docker restart

###### //至此,docker环境交付完毕

#### 2.交付私有镜像库

docker run -d -p 5000:5000 --name registry registry:2

###### //拉取一个nginx镜像测试推送至私有镜像库
docker pull nginx

###### //docker tag 地址:端口/名称:版本
docker tag nginx 10.23.187.165:5000/nginx:test

docker push 10.23.187.165:5000/nginx:test
###### //推送完毕代表镜像库已经交付
###### //至此,docker环境交付完毕

#### 3.交付rancher,生产环境需要数据库外挂方式部署,参照官方文档
sudo docker run -d --restart=unless-stopped -v /etc/localtime:/etc/localtime:ro -p 8080:8080 rancher/server:v1.6.28
###### //若干分钟就可以通过8080端口访问rancher后台
###### //添加自己的管理员账号密码
###### //在系统设置增加自定义应用商店
###### //名称:library
###### //地址:https://git.oschina.net/rancher/rancher-catalog.git
###### //分支:k8s-v1.6-release
# rancher文档:
https://rancher.com/docs/rancher/v1.6/zh/kubernetes/

# JAVA(Jetty+JFinal)例子项目:
https://gitee.com/aisao/k8s_java_project_demo.git

# PHP(ngx+php5.6+yaf)例子项目:
https://gitee.com/aisao/k8s_php_project_demo.git

# dotnet core 例子项目:
https://gitee.com/aisao/k8s_dnet_project_demo.git

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)