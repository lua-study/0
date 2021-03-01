# AdminSet
   
  
[![release](https://img.shields.io/github/release/guohongze/adminset.svg)](https://github.com/guohongze/adminset/releases)
 
Adminset基于DevOps理念开发，以整合全部运维场景为己任。Adminset是一个真正的基于运维思维而开发的全自动化运维平台。 

## v0.6 新功能
CMDB新增应用配置数据库

## 开发环境
centos 7.2(1511) django 1.9.8（兼容Django1.11） python 2.7 

## 服务端安装
生产服务器建议 4核CPU，8G内存以上. 
学习测试建议 2核CPU，2G内存以上. 
服务器操作系统版本要求 centos7.2及以上 
安装过程需要输入管理员数据库等交互信息 
```
git clone https://github.com/guohongze/adminset.git
adminset/install/server/server_install.sh
```

## 客户端安装
客户端脚本目前rhel/centos6、7,ubuntu14.04经过测试 
客户端python版本支持2.6.6及以上 
说明：为保证注册IP是管理IP（后续会被ansible等调用），客户端的IP抓取目前使用主机名解析，否则报错。 
如：主机名为cn-bj-web01 请在/etc/hosts中加入相应的解析 192.168.x.x cn-bj-web01，这样再执行adminset_agent.py 可以保证正常运行。
#### step1:
拷贝install/client/client_install.sh 到客户机上并执行:
```
install/client/client_install.sh
```
#### step2:
拷贝install/client/adminset_agent.py 到客户机上并执行:
```
python adminset_agent.py
```
后台运行请参考：
```
nohup adminset_agent.py &
```

## 访问
http://your_server_ip 
使用自己在安装过程中创建的super admin用户名密码

## 说明
使用请转到， 使用说明  
功能请转到， 功能说明  
FAQ请转到， 常见问题 

# 安全
建议不要将程序启动在有公网可以直接访问的设备上，如果需要请使用VPN。 
建议生产环境中使用https配置服务器 
由于开发方便，在django的settings中开启了DEBUG，在生产中需要关闭并指定自己的域名。

# 开发者交流
请加入开发者群，注明来自github
  


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)