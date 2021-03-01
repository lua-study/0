# JetBrains-License-Server

## 关于新版本的编辑器无法激活的问题
* 由于JetBrains公司新出的编辑器的激活制度发生了变化,导致本程序在新版本中不可用.
* 之前是下载好激活程序之后就可以获得秘钥,但是现在必须通过官方的渠道去购买证书.
* 比较值得庆祝的一件事是官网支持历史版本的下载和非强制性的升级,所以本程序对2018.2之前版本的编辑器还是可用的


#### 项目介绍
JetBrains-License-Server
IDEA,PHPStorm,WebStorm 等编辑器激活服务器源代码

#### 软件架构
框架采用Spring Boot + Spring MVC
无任何业务其他处理逻辑，代码简洁清晰
一句话概括原理就是:
激活的过程中会访问一个接口，然后这个接口返回一个XML 给这个XML使用PEM私钥签名 就完成激活。
签名证书反编译自 https://www.jetbrains.com/help/license_server/downloading.html
想挑战的童鞋可以试试，我觉得还是挺有难度的。[:滑稽]

2.0版本对程序进行了优化和简洁处理,对pom文件精简到了极致 程序的代码也变得更为的简单易懂


#### 依赖环境

1. JDK1.8
2. Maven

#### 使用说明

1. git clone https://gitee.com/Suimg/JetBrains-License-Server.git
2. cd JetBrains-License-Server
3. mvn package
4. java -Dserver.port=80 -jar target/license-server.jar suimg


#### 后台运行
##### 启动程序
1. nohup java -Dserver.port=80 -jar target/license-server.jar suimg >ls.log 2>&1 &
##### 结束程序
1. ps -def |grep target/license-server.jar|awk '{print $2}'|xargs kill -9


#### 注意事项
1. 本激活程序不适用于任何2018.2以及之后的版本
2. 本项目在2018年 9月 24日 由@Suimg 重构,之前的代码已经标记为1.0版本
3. 关于启动项目的命令 通过-Dserver.port参数可以配置项目绑定的端口 jar之后的参数为授权的用户名
4. 授权的用户名不能为中文否则将会出现授权用户为空或不显示
5. 更多详细内容和介绍请移步 https://www.suimg.cn/idea.do

##### 关于开源许可协议
* 老实说 我对这个开源协议懂得并不是很多 当初新建这个项目的时候也没在意这个,只是觉得Apache比较熟悉 所以选择了Apache 2.0 作为了开源协议
* 其实我感觉更像是BSD,Emmmm 我对这个也不是很清楚 就不要在意这个了


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)