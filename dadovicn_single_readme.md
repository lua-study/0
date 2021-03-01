
```shell
### 下载镜像
docker pull registry.aliyuncs.com/helowin/oracle_11g
### 查看镜像
docker images
### 启动镜像 
docker run -d --name oracle_11g -p 1521:1521 registry.aliyuncs.com/helowin/oracle_11g
### 查看容器列表
docker container  ls -a
### 启动容器
docker start 容器id
### 
sqlplus /nolog
conn /as sysdba
create user fx110 identified by fx110;
grant connect,resource,dba to fx110;


#### 导入数据库
imp fx110/fx110 file=/home/fx110-20181102.dmp grants=no full=y
```




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)