## gitee-ci-deploy
### 这是啥
这个项目主要是针对码云持续集成功能（下面称为码云CI）的补充。  
启动此项目之后，会有一个地址，该地址对应码云CI中的“构建完成后回调”。  
在码云CI对你的项目完成了一次成功的构建之后，此项目可以帮助你下载项目包，并且你可以对接下来的步骤进行自定义。比如说，你可以写些关于项目部署的shell命令，实现自动部署。

### 怎么用
1. 首先，在invoke/invoke.sh 中自定义项目包下载下来之后，需要执行的shell命令。
2. 启动gitee-ci-deploy 项目，命令为`sh invoke/start.sh    `。其中port，为此项目对外开放的端口号；package_name 为此项目帮你下载下来的项目包名，下载的包在gitee-ci-deploy.jar 所在路径。
3. 在码云CI中配置“构建完成后回调”参数，值为`http://{此项目对外可访问的host}:{启动时的port}/deploy`。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)