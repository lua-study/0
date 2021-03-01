
安装完tidb集群环境后，我就需要编写一个客户端来访问tidb，使用tispark来编写相应的业务需求功能。不过坑太多了，当中我碰到各种问题，在此文中我会先把相应的过程记录下来，再告诉大家我碰到的几个坑和解决方案。并提供我的代码示例在文后

# 准备

## 最方便的做法

在项目的doc目录下，将tispark-0.1.0-SNAPSHOT.jar
按照如下格式

```
 
        com.pingcap.tispark 
        tispark 
        0.1.0-SNAPSHOT 
 
```

上传到你自己的maven私服即可

## 比较麻烦的做法

访问github，按照下列步骤打包编译tispark-0.1.0-SNAPSHOT.jar

首先你要打包编译tikv-client

项目路径

https://github.com/pingcap/tikv-client-lib-java/tree/c050a3f69e2a2ed15b6358a37a52f05b314b795e

打包tikv-client项目
```
git clone https://github.com/pingcap/tikv-client-lib-java.git
mvn clean install -DskipTests -Dmaven.test.skip=true
```
接着打包编译tispark

项目路径

https://github.com/pingcap/tispark

打包tispark项目

```
git clone https://github.com/pingcap/tispark.git
mvn clean install -DskipTests -Dmaven.test.skip=true
```

在target目录下找到tispark-0.1.0-SNAPSHOT.jar，按照前面所述上传到自己的maven私服即可

# 项目编译

```
mvn clean install -DskipTests -Dmaven.test.skip=true
```

# 解释

见SparkConfig.java文件，如下

![图1.png](http://upload-images.jianshu.io/upload_images/3901033-0885c68b4b3c0a91.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



通过Builder模式创建SparkSession实例（相应的application名字，tidb的PD Server地址以及spark服务主节点地址通过SparkProperties从属性文件中读取），然后初始化TiContext上下文对象，映射的数据库名就是前文
[《TiDB初体验》](http://www.jianshu.com/p/7bd05b55b182) 中搭建的mysql数据库名。返回的TiContext对象可通过依赖注入在需要的地方引用。比如DemoServiceImpl类中，读取customer数据库表的数据

![图2.png](http://upload-images.jianshu.io/upload_images/3901033-aced4ea62dfde3e6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 问题

## 版本问题

我的tidb集群环境其中集成的spark是2.1.1版本，因此自身的springboot项目的pom文件中的spark依赖包版本要与之对应，见下图

![图3.png](http://upload-images.jianshu.io/upload_images/3901033-5805bfa7b1be069e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 依赖包缺失

SparkConfig中需要设定pd server的ip和端口，这样执行TisparkDemoApplication类时不会报错，否则会报找不到spark.tispark.pd.addresses错误，如下图
![图4.png](http://upload-images.jianshu.io/upload_images/3901033-0a4603a1381ca18a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## TiKV-client的依赖声明要显式声明

也就说下面这段pom文件里必须要有
```
 
      com.pingcap.tikv 
      tikv-client 
      0.1.0-SNAPSHOT 
 
```
否则会报下图红框中的错误

![图5.png](http://upload-images.jianshu.io/upload_images/3901033-473447bd104cf4ce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## TiKV端口随机生成

因为tidb集群中tikv节点的端口，在启动时都是随机生成的，这就带来一个问题。开发用的电脑是外网，要访问tidb集群必须要做端口映射，但是每次启动TisparkDemoApplication类时需要访问的tikv节点端口都是随机生成的，无法提前预知端口号来进行映射，从而造成每次都连接不到tikv节点。tidb的PD Server就会不停重试连接，到达一定次数会报exhaust错误。见下图红框


![图6.png](http://upload-images.jianshu.io/upload_images/3901033-b0d3dcb99e7e36be.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这个问题困扰了我很久，后来我终于下定决心直接在本机打包，把jar包上传到tidb集群的PD Server，执行springboot的fat jar模式命令运行。毕竟在集群环境不需要做外网端口映射啊~
附上命令
```
java -jar /usr/local/tispark-demo-0.1.jar
```

# 参考链接

[1][tikv-client](https://github.com/pingcap/tikv-client-lib-java/tree/c050a3f69e2a2ed15b6358a37a52f05b314b795e)

[2][tispark](https://github.com/pingcap/tispark)

[3][我的代码示例(码云)](https://gitee.com/darkranger/tispark-demo)

[4][我的代码示例(github)](https://github.com/wujunshen/tispark-demo)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)