# 通用镜像


## 注意事项

1. docker 挂载的容器外目录和文件，其属主和属组是root.root，为确保容器内其他用户可读写，可在物理主机上设置该目录/文件权限777。

2. 容器启动脚本 docker-entrypoint 说明
    - 无参数: 初始化完成后启动(docker 中使用)
    - 参数 init: 只初始化, 不启动(k8s 中使用)
    - 参数 run: 直接启动(k8s 中使用)

3. 容器的外置挂载目录 /opt/pv, 此目录位于容器中，容器在初始化过程中会在此目录下创建数据、日志及其它永久存储的目录。


## 镜像信息

1. 10.0.16.125:5080/general/ubuntu:16.04
    - 基础镜像: docker.io/ubuntu:16.04

2. 10.0.16.125:5080/general/ubuntu-nginx:16
    - 基础镜像: 10.0.16.125:5080/general/ubuntu:16.04
    - 日志目录: /var/log/nginx
    - 服务配置文件: nginx.conf
    - 容器启动脚本: docker-entrypoint

3. 10.0.16.125:5080/general/ubuntu-tomcat:16-7
    - 基础镜像: 10.0.16.125:5080/general/ubuntu:16.04
    - 日志目录: /var/log/tomcat7
    - 应用目录: /var/lib/tomcat7/webapps
    - 服务配置文件: server.xml setenv.sh
    - 依赖包: jre8.tbz
    - 容器启动脚本: docker-entrypoint

4. 10.0.16.125:5080/general/ubuntu-mysql:16
    - 基础镜像: 10.0.16.125:5080/general/ubuntu:16.04
    - 日志目录: /var/log/mysql
    - 数据目录: /var/lib/mysql
    - 容器端口:
        - 客户端服务: 3306
    - 环境变量:
        - DB_PASSWORD: NOT_SET
        - SQL_FILE: NOT_SET
    - 业务数据库配置文件: db_init.sql
    - 服务配置文件: mysqld.cnf
    - 容器启动脚本: docker-entrypoint

5. 10.0.16.125:5080/general/ubuntu-redis:16
    - 基础镜像: 10.0.16.125:5080/general/ubuntu:16.04
    - 日志目录: /var/log/redis
    - 数据目录: /var/lib/redis  
    - 容器端口:
        - 客户端服务: 6379
    - 容器启动脚本: docker-entrypoint

6. 10.0.16.125:5080/general/ubuntu-mongodb:16-3.4
    - 基础镜像: 10.0.16.125:5080/general/ubuntu:16.04
    - 日志目录: /var/log/mongodb
    - 数据目录: /var/lib/mongodb  
    - 容器端口:
        - 客户端服务: 27017
    - 软件源: mongodb-org-3.4.lsit
    - 容器启动脚本: docker-entrypoint

7. 10.0.16.125:5080/general/ubuntu-rabbitmq:16
    - 基础镜像: 10.0.16.125:5080/general/ubuntu:16.04
    - 日志目录: /var/log/rabbitmq
    - 数据目录: /var/lib/rabbitmq/mnesia  
    - 容器端口:
        - 客户端服务: 5672
    - 容器启动脚本: docker-entrypoint

8. 10.0.16.125:5080/general/centos:7
    - 基础镜像: docker.io/centos:7

9. 10.0.16.125:5080/general/centos-mariadb:7-10.1
    - 基础镜像: 10.0.16.125:5080/general/centos:7
    - 日志目录: /var/log/mysql
    - 数据目录: /var/lib/mysql
    - 容器端口:
        - 客户端服务: 3306
    - 环境变量:
        - DB_PASSWORD: NOT_SET
        - SQL_FILE: NOT_SET
    - 业务数据库配置文件: db_init.sql
    - 服务配置文件: mysqld.cnf
    - 容器启动脚本: docker-entrypoint

10. 10.0.16.125:5080/general/centos-tomcat:7
    - 基础镜像: 10.0.16.125:5080/general/centos:7
    - 日志目录: /opt/tomcat/logs
    - 应用目录: /opt/tomcat/webapps
    - 服务配置文件: server.xml setenv.sh
    - 依赖包: jre.tbz
    - 容器启动脚本: docker-entrypoint

11. 10.0.16.125:5080/general/centos-nginx:7
    - 基础镜像: 10.0.16.125:5080/general/centos:7
    - 日志目录: /var/log/nginx
    - 应用目录: /usr/share/nginx/html
    - 服务配置文件: nginx.conf
    - 容器启动脚本: docker-entrypoint

12. 10.0.16.125:5080/other/nginx-fileindex:centos7
    - 基础镜像: 10.0.16.125:5080/general/centos-nginx:7
    - 日志目录: /var/log/nginx
    - 应用目录: /usr/share/nginx/html
    - 服务配置文件: nginx.conf
    - 容器启动脚本: docker-entrypoint

11. 10.0.16.125:5080/general/centos-gogs:7
    - 基础镜像: 10.0.16.125:5080/general/centos:7
    - 日志目录: /opt/pv/gogs_log
    - data目录: /opt/pv/gogs_data
    - repo目录: /opt/pv/gogs_repo
    - 服务配置文件: app.ini
    - gogs 安装包: linux_amd64.tar.gz
    - web文件修改: \*.tmpl \*.gif \*.png
    - 容器启动脚本: docker-entrypoint



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)