# jfinal-dubbo-plugin

#### 项目介绍
一个jfinal的dubbo插件，使用dubbo api集成，不需要引入spring。

#### 安装教程

从https://gitee.com/YouYiGeXinShou/jfinal-dubbo-plugin/ 克隆或下载源码包
运行maven clean install

#### 使用说明
1.引入jar
```
 
	 top.yujiaxin 
	 jfinal-dubbo-plugin 
	 1.0.1 
 
```
创建配置文件jfinal.properties,参考源码的中的jfinal.properties文件（如果想用其他文件名，需要new DubboPlugin("your file name")）。

在JfinalConfig添加插件`Plugins.add(new DubboPlugin())`;

2.在需要暴露的服务上面使用`@RpcService`注解
```
    @RpcService(group="simple", version="1.0", stub="true", mock="true")
    public class MyServiceImpl implements MyService{
        //TODO 
    }

```
3.引用远程服务
```
    MyService myService=DubboRpc.receiveService(MyService.class);
```
在controller中引用远程服务可使用`@ReferenceService`注解
```
    public class MyController extends Controller{
        
            @ReferenceService(group="simple", version="1.0")
            private MyService myService;
            //TODO
    }
```
使用注解需要在JfinalConfig中配置`Constants.controllerFactory(new ReferenceServiceAutowiredControllerFactory());

4.以容器运行
大多数情况下Rpc远程服务不需要mvc层，如果部署在web容器中会比较浪费。dubbo 提供了 container去启动一个服务进程提供服务。
dubbo默认实现了spring 引导的container，这里提供了一个jfinal的实现。
在jfinal.properties里加入`configClass=com.demo.YourJfinalConfig`

使用 `java com.alibaba.dubbo.container.Main jfinalContainer`启动一个jfinalContainer

#### 参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)