# one-deploy

#### 介绍
Tomcat WEB项目一键管理部署。可以单独、批量更新class、图片等。小公司快速部署项目更新bug必备。解决k8s、Jenkins无法单独更新class的痛苦。

> 注意事项：
1. 此版本只适用外置tomcat部署
2. 不支持jar
3. 项目核心为magger.war

#### 软件架构
项目为springboot项目,只支持放置到外置tomcat运行


#### 安装教程
1、下载war [点我下载war包](https://gitee.com/bdj/one-deploy/releases/1.2)、放入单独的tomcat启动即可
2、访问地址：http://ip:port/oneDeploy

#### 使用说明

1.  运行项目
2.  tomcat配置 >> 添加tomcat
![tomcat配置](https://images.gitee.com/uploads/images/2020/0308/204219_29936610_123301.png "tomcat配置.png")
3.  点击【部署magger项目】，这样对应的tomcat>>webapps下面会创建一台magger.war项目
![部署magger项目](https://images.gitee.com/uploads/images/2020/0308/211520_427955de_123301.png "部署magger项目.png")
4. 重启你的tomcat
5. 进入【项目列表】你可以对tomcat进行管理【启动项目、停止项目、取消部署（会删除项目）、单文件更新（压缩包也可以）】
![项目列表](https://images.gitee.com/uploads/images/2020/0308/212624_eb6b2801_123301.png "项目列表.png")
> ---下面是单文件以及压缩包更新操作---
6. 单文件更新，请选中自己需要更新的单文件
![单文件更新](https://images.gitee.com/uploads/images/2020/0308/213401_7f02d1e0_123301.png "单文件更新.png")
7. 文件夹更新，请本地打包成压缩包
![文件夹更新](https://images.gitee.com/uploads/images/2020/0308/213814_b1eb7204_123301.png "文件夹更新.png")


#### 项目招安
因为是业余时间开发，没有做前台设计，用最简陋的标签来快速达到项目，我们项目全部使用json格式，方便前端对接。
现在热忱招聘一名前端人员，帮助我们换一套漂亮的界面。让此项目越来越强大好看。

#### 参与贡献榜
1.  开源oschina（87766867@qq.com)-项目发起人
2.  KevinJava (457295821@qq.com)-项目参与人开发人员

#### 视频教程
[视频教程](http://v9-default.ixigua.com/a61456a2650d2191a96af061dca65cf0/5e7748de/video/tos/hxsy/tos-hxsy-ve-0004/f7f7a791429b42ea8c7f0e8d5ac2f2b9/?a=2011&br=0&bt=106&cr=0&cs=0&dr=0&ds=1&er=&l=2020032218102401001404008619D520B2&lr=&qs=0&rc=ajhuOmd1PG9qczMzNzczM0ApZTRkZTU4ZTw0NzxpZDw0ZGdkY3JtNGlsMmxfLS0yLS9zc181LzIxYzQxY2I0NWAtYDA6Yw%3D%3D&vl=&vr=)

### 开发者联系
- QQ：87766867 
- QQ群：881799237 
     进群备注【一键部署】不然不予通过



#### 开发版本流程图

![v1.0](https://images.gitee.com/uploads/images/2020/0301/020221_5eb0b779_123301.jpeg "1111.jpg")



![v2.0](https://images.gitee.com/uploads/images/2020/0301/020447_cbcc63ca_123301.jpeg "222.jpg")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)