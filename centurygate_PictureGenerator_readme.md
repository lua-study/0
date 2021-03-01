# PictureGenerator
nodeserver-echarts-render
目录说明：
一、PictureServerProxy 属于Spring MVC 的java maven工程，在该目录中执行mvn package后将target文件夹中的PictureServerProxy.war放在tomcat的webapps目录下即可

二、PictureServer是NodeJS的工程,使用node-echarts根据接收到的echarts option数据生成png后网络返回http客户端，该工程中的环境基于node-v7.3.0，服务启动后默认监听端口为3000
使用说明如下：
假设你的PictureServer文件夹在E盘根目录，则在windows控制台中输入如下命令：

E:
cd PictureServer
cd bin
node www


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)