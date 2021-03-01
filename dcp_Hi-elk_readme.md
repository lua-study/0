# Hi-elk

#### 项目介绍
- ![image](https://github.com/ppabc/Hi-elk/raw/master/images/Hi-elk.png)
Hi-elk 是基于Docker快速搭建elk服务镜像，Hi-elk采用Alpine Linux系统为底层,专注于打造最简洁最安全最稳定的elk镜像，实现快速搭建elk服务。


#### 功能特性
1. Hi-elk 中包含elasticsearch、kibana、logstash；

2. 可在运行在小内存云主机上，比如：1G内存，2G内存云主机；

3. 可快速接入nginx日志，方便nginx日志分析；

4. 容器上运行kibana已中文化，更友好；

5. 易于定制，只需简单编辑 Dockerfile 即可；

6. 所有镜像均从官方基础镜像扩展而来，安全可靠；

7. 易于使用环境变量安装/删除容器中的软件；

8. 简洁、结构良好的 Dockerfiles（Dockerfile）；

9. 一切都是可见的和可编辑的。


#### 软件架构

- ![image](https://github.com/ppabc/Hi-elk/raw/master/images/elk.png)

#### 安装教程

1. git clone git@github.com:ppabc/Hi-elk.git
2. cd Hi-elk/5.6.9-2g/
3. docker build --tag elk:1.1 -f Dockerfile .
4. docker run -d --name elk -ti -p 5601:5601 -p 5044:5044 elk:1.1
5. 或者采用host方式： docker run -d --name elk  -v /data:/data --net=host -it elk:1.1

#### 使用说明

1. 使用hub.docker.com上镜像，4G以上内存服务器使用命令docker pull ppabc/hi-elk
2. 使用hub.docker.com上镜像，2G以上内存服务器使用命令docker pull ppabc/hi-elk:2g
3. Elk设置nginx密码,参考： https://bbs.aqzt.com/thread-567-1-1.html
4. nginx日志格式参考： https://github.com/ppabc/Hi-elk/tree/master/nginx
5. filebeat安装参考： https://github.com/ppabc/Hi-elk/tree/master/filebeat

#### 效果图

- ![image](https://github.com/ppabc/Hi-elk/raw/master/images/elk2018.png)

#### 参与贡献

1. 如果想分享或是交流的话，请加 QQ 群： 7652650 （安全运维）
2. Email：ppabc@qq.com

#### 微信关注

![image](https://git.oschina.net/aqztcom/kjyw/raw/master/images/aqzt.jpg)





 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)