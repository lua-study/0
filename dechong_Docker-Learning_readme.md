# Docker Compose编排工具简介

Compose是一个用于定义和运行多容器Docker应用程序的工具，前身是Fig，它非常适合用在开发、测试、构建CI（持续集成）工作流等场景中。

Docker Compose是一个用来定义和运行复杂应用的Docker工具。一个使用Docker容器的应用，通常由多个容器组成。使用Docker Compose不再需要使用shell脚本来启动容器。 

Compose 通过一个配置文件来管理多个Docker容器，在配置文件中，所有的容器通过services来定义，然后使用docker-compose脚本来启动，停止和重启应用，和应用中的服务以及所有依赖服务的容器，非常适合组合使用多个容器进行开发的场景。

![](http://www.ruanyifeng.com/blogimg/asset/2018/bg2018021311.jpg)

[Compose](https://docs.docker.com/compose/) 是 Docker 公司推出的一个工具软件，可以管理多个 Docker 容器组成一个应用。你需要定义一个 [YAML](http://www.ruanyifeng.com/blog/2016/07/yaml.html) 格式的配置文件`docker-compose.yml`，写好多个容器之间的调用关系。然后，只要一个命令，就能同时启动/关闭这些容器。

Docker Compose将所管理的容器分为三层，分别是工程(Project)，服务(Service)以及容器(Container).Docker Compose运行目录下的所有文件(docker-compose.yml,extends文件或环境变量文件等)组成一个工程(默认为docker-compose.yml所在目录的目录名称)。一个工程可以包含多个服务，每个服务中定义了容器运行的镜像、参数和依赖，一个服务可包含多个容器实例。

```
# 启动所有服务
$ docker-compose up
# 关闭所有服务
$ docker-compose stop
```

# 学习目标

在[**Micro-service-learning**](https://github.com/TaciturnK/Micro-service-learning) 工程的学习基础之上，使用docker工具进行服务的发布，主要利用其中的6个子工程来进行学习，工程列表如下：

- microservice-consume-movie-feign-hystrix：服务消费者(整合ribbon.feign,hystrix)
- microservice-discovery-eureka：服务注册中心(Eureak)
- microservice-getway-zuul：路由网关(Zuul)
- microservice-hystrix-dashboard：hystrix可视化监控工具(独立项目，不依赖服务注册中心)
- microservice-hystrix-turbine：turbine聚合监控数据(供microservice-hystrix-dashboard调用)
- microservice-provider-user：服务提供者

**环境：**

- 虚拟机上已经搭建了docker服务，并可以进行正常的镜像拉取，上传阿里云镜像仓库操作，相关功能已经经过测试，达到了实验的条件。
- idea开发工具上面已经安装了docker开发插件，并且虚拟机的docker开启了api2375端口，远程传输的功能，并且已经单独进行了测试，达到了在idea上发布镜像到虚拟中的条件。

**学习目的：**

> 在Idea工具上编排微服务的各个服务，并使用docker插件发布到虚拟机中的docker服务中，然后进入虚拟机，在虚拟机中将镜像发布到远程阿里云docker镜像仓库，供其他主机使用时拉取。

**学习计划：**

1. docker compose快速入门：使用microservice-discovery-eureka作为学习目标，使用compose工具进行编排发布，并可进行访问；
2. 编排这6个微服务，并最终可进行访问；



# Docker Compose 的安装

两种最新的docker安装方式

## 1.从github上下载docker-compose二进制文件安装

- 下载最新版的docker-compose文件 

  ```
  curl -L https://github.com/docker/compose/releases/download/1.21.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
  ```

 ![](https://i.imgur.com/9dxSgXa.png)

  ​

- 添加可执行权限 
  `chmod +x /usr/local/bin/docker-compose`

- 测试安装结果 
  `$ docker-compose --version `

![](https://i.imgur.com/lEJfxts.png)

## 2.pip安装

`$ sudo pip install docker-compose`

# Docker Compose基本使用

- 使用Dockerfile定义应用程序环境，以便在任何地方重现该环境。

![](https://i.imgur.com/O0ZzRPl.png)

![](https://i.imgur.com/epxZl4o.png)

- 在docker-compose.yml文件中定义组成应用程序的服务，以便各个服务在一个隔离的环境中一起运行。

![](https://i.imgur.com/TuzaCdG.png)

- 运行docker-compose up命令，启动并运行整个应用程序。

![](https://i.imgur.com/SggYz0P.png)

![](https://i.imgur.com/0yvG1sx.png)

![](https://i.imgur.com/P6YWPqR.png)

# docker-compose.yml常用命令

docker-compose.yml是Compose的默认模板文件。该文件有多种写法，目前Version 2.X以及Version 3.X基本兼容，是未来的趋势。

- build

配置构建时的选项，Compose会利用它自动构建镜像。build的值可以是一个路径，例如：build: ./dir，也可以是一个对象，用于指定Dockerfile和参数，例如：



# 具体的步骤

- 使用Idea中的docker插件构建Docker镜像，发布到虚拟机中的docker服务中。

![](https://i.imgur.com/40RSnxM.png)

![](https://i.imgur.com/186vlfT.png)

- 编写docker.compose.yml编排文件

```yml
# 表示docker-compose.yml文件使用的是Version 2 file format
version: '2'
# Version 2 file format的固定写法，为project定义服务
services:
  #指定服务名称
  microservice-discovery-eureka:
    #指定服务所用的镜像
    image: microservice-discovery-eureka:latest
    #爆暴露端口信息
    ports:
      - "8761:8761"
  microservice-provider-user:
    #指定镜像
    image: microservice-provider-user
    #连接microservice-discovery-eureka服务,这里使用的是service:alias的形式
    links:
      - microservice-discovery-eureka:discovery
    #爆暴露端口信息
    ports:
      - "9000:9000"
  microservice-consume-movie-feign-hystrix:
    #指定镜像
    image: microservice-consume-movie-feign-hystrix
    #爆暴露端口信息
    ports:
      - "9103:9103"
    #连接服务
    links:
      - microservice-discovery-eureka:discovery
```

- 启动服务：

```
docker-compose up
```

![](https://i.imgur.com/X7vpiht.png)









 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)