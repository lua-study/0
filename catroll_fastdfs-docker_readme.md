# docker-fastdfs-allinone

#### 介绍
fastdfs5.11的dockerfile  
fastdfs:5.11、nginx、fastdfs-nginx-module整合到一个docker镜像中  
fastdfs tracker_server、storage_server都只有一个  
适用于需要fastdfs文件服务但又不需要集群部署，或者快速开始  
包含一个java的测试脚本  
之所以有这个项目，是停止更新的fastdfs又开始更新了，没有时间测试新版本，只能重新构建旧版本

#### 基础环境
需要安装docker,在19.03.1、18.09.0 上测试通过

#### 使用说明
##### docker方式构建
只需要 Dockerfile
1.  构建镜像
	`docker build -t fastdfs:5.11 .`
2.  构建容器并启动  
	`docker run -d --name fastdfs:5.11 -v /usr/local/data/fastdfs:/var/local/fdfs -e "IP=宿主机ip" -e "WEB_PORT=8888" --net="host" fastdfs:5.11`  
	说明:  
		-v /usr/local/data/fastdfs:/var/local/fdfs 为文件目录映射，文件最终保存在宿主机/usr/local/data/fastdfs目录中  
		-e "IP=宿主机ip" 为宿主机局域网ip  
		-e "WEB_PORT=8888"  自定义web端口，还支持FDFS_PORT（实际为tracker_server的port，当初起名没起好，懒得改了）、STORAGE_PORT  
		***--net="host"*** 必须为host模式
	

##### docker-compose 方式构建  
1.  安装compose  
	`./install_docker-compose.sh`
2.  构建并运行容器  
	`./build_fastdfs_docker_use_compose.sh`

##### 测试

	测试是否成功（需要jdk 1.8以上）   
```
	cd test
	sh test_install_result.sh
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)