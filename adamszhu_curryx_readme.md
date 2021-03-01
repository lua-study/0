# Curryx 基于RPC的面向服务的轻量级框架 

## 项目简介

该项目是一个使用java开发的rpc框架，框架中的角色分为服务调用者、服务提供者和注册中心，其职能分别如下：

* 服务提供者负责实现具体的业务逻辑，需要向注册中心注册其所提供的服务，并将服务接口暴露给服务调用者
* 服务调用者调用服务提供者提供的服务，需要从注册中心中查找相应的服务
* 注册中心负责管理服务提供者所提供的服务集合并能够被服务调用者所发现

  ├── curryx-client   客户端 
  ├── curryx-server   服务端 
  ├── curryx-serviceRegistryAndDiscovery  业务注册和业务发现 
  ├── curryx-common   公共工具，包含请求报文格式，编码和解码器 
  ├── curryx-distributedLock 分布式锁 

## 使用说明

如果是使用maven来构建项目，请下载源码，并将源码打包成为jar包（maven install）,然后在项目的pom.xml中加入如下依赖：

```
     
     
         com.freestyledash 
         curry-server 
         x.x.x 
     
```
```
     
     
         com.freestyledash 
         curry-client 
         x.x.x 
     
```

如果是其他方式，可以下载相应的jar包并加入到项目的classpath中。

  
### 服务提供者初始化

将方法设置为服务，该服务会在服务器启动时自动注册到名字服务器中
```
@Service(name = Helloworld.class, version = "develop")
public class HelloworldImpl implements Helloworld {

    @Override
    public String hellow() {
        return "helloworld";
    }
}
```

启动服务,使用spring来组织各个组件,并启动
```
    
     
     
         
         
         -->
         -->
     

     
     
         
         
         
     

     
     
         
         
         
     

     
     
         
     
```
```
    ApplicationContext context = new ClassPathXmlApplicationContext("spring.xml");
    RPCServerBootstrap bean = context.getBean(RPCServerBootstrap.class);
    bean.launch();
```
### 服务调用者初始化

使用spring来组织服服务调用者
```
     

     
         
         
         
     

     
         
     
 ```
 使用java调用
 ```
     RPCClient client = ApplicationContextHolder.getContext().getBean(RPCClient.class);
     T t = client.create(Class  tClazz);
     t.dosth();
 ```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)