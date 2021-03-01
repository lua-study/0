# nginxWebUI

#### 介绍
nginx网页配置工具


#### 功能说明
本项目是基于springBoot的web系统,数据库使用sqlite,因此服务器上不需要安装任何数据库

其中orm使用了本人自己开源的sqlHelper项目作为orm,使用sqlite作为数据库,项目启动时会释放一个.sqlite.db到系统用户文件夹中

sqlHelper是一个可以像mongodb一样使用sql数据库的orm,解放开发者对sql数据库表结构的维护工作,有兴趣的可以了解一下  https://gitee.com/cym1102/sqlHelper

本项目可以使用WebUI配置nginx的各项功能,包括端口转发,反向代理,ssl证书配置,负载均衡等,最终生成nginx.conf配置文件并覆盖目标配置文件,完成nginx的功能配置. 

nginx本身功能复杂,本项目并不能涵盖nginx所有功能,只能配置常用功能,更高级的功能配置仍然需要在最终生成的nginx.conf中进行手动编写.

#### 安装说明
以Ubuntu操作系统为例:

1.安装java运行环境

```
apt install openjdk-11-jdk
```

2.下载编译好的jar,下载地址https://gitee.com/cym1102/nginxWebUI/releases

启动命令

nohup java -jar nginxWebUI-1.0.0.jar --server.port=8000 > nginxWebUI.log &


#### 使用说明

打开http://xxx.xxx.xxx.xx:8080
默认登录名密码为admin/admin

![登录](https://images.gitee.com/uploads/images/2020/0509/105416_831df2bb_1100382.jpeg "QQ截图20200509105343.jpg")

![管理员管理](https://images.gitee.com/uploads/images/2020/0514/090146_596746a4_1100382.jpeg "QQ截图20200514090059.jpg")

进入系统后,可在管理员管理里面添加修改管理员账号

![基础配置](https://images.gitee.com/uploads/images/2020/0514/090302_ce1086d4_1100382.jpeg "QQ截图20200514090002.jpg")

在基础配置中可以配置nginx的http项目基础配置,默认会给出几个常用配置,其他需要的配置可自由增删改查

![反向代理](https://images.gitee.com/uploads/images/2020/0514/090331_a91e02bc_1100382.jpeg "QQ截图20200514090019.jpg")

在反向代理中可配置nginx的反向代理即server项功能,可开启ssl功能,直接从网页上上传pem文件和key文件,直接放到系统用户文件夹下,还可以直接开启http转跳https功能,用户直接访问http会转跳到https

![负载均衡](https://images.gitee.com/uploads/images/2020/0514/090358_5328b7d6_1100382.jpeg "QQ截图20200514090045.jpg")

在负载均衡中可配置nginx的负载均衡即upstream项功能,在反向代理中可选择代理目标为负载均衡项

![生成conf](https://images.gitee.com/uploads/images/2020/0514/090412_c3d57fa8_1100382.jpeg "QQ截图20200514090053.jpg")

最终生成conf文件,可在此进行进一步手动修改,确认修改无误后,可覆盖本机conf文件,并进行效验和重启

今后配置nginx再也不用上网各种搜索, 只需要在本项目中进行增删改查就可方便的配置nginx

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)