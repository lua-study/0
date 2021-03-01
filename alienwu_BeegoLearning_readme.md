                                                     ### 笔记摘要
中文文档:  
https://beego.me/docs/install/bee.md  

## 1.安装beego框架

```
go get github.com/astaxie/beego
```

## 2.安装bee工具

```
go get github.com/beego/bee
```
## 3.使用bee工具
(1)若是windows系统:
- 找到bee文件的main.go，然后go build main.go 编译bee;  
- 接着设置环境变量即可使用bee工具  
(2)若是linux系统:  
设置环境变量

## 4.bee工具命令
输入bee可看到概括信息  
**new 命令:**  
ex:bee new project ----创建一个beego项目  
**api 命令:**  
ex:bee api apiproject ----创建一个api项目  
**run 命令:**  
到指定beego项目路径下执行改命令  
ex:bee run    ----监控并启动beego项目  
**pack 命令:**  
pack 目录用来发布应用的时候打包，会把项目打包成 zip 包，这样我们部署的时候直接把打包之后的项目上传，解压就可以部署了。  
ex:bee pack ----打包beego项目,打包后会生成可执行文件以及压缩文件  

还有些命令暂时不需要用到，后续需要用的时候再补充....


## 5.web名词概念:
(1)filter:  
过滤器JavaWeb三大组件之一，它与Servlet很相似！不它过滤器是用来拦截请求的，而不是处理请求的。当用户请求某个Servlet时，会先执行部署在这个请求上的Filter，如果Filter“放行”，那么会继承执行用户请求的Servlet；如果Filter不“放行”，那么就不会执行用户请求的Servlet。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)