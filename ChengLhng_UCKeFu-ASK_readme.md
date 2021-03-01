#UCKeFu-ASK


#优客服-问答社区
优客社区是一个基于 Spring Boot 的轻量级社区系统，设计之初是为优客服项目提供在线交流的一个社区平台。
（QQ群：555834343，目前项目正在开发过程中，尚未发布v1.0版本，加入QQ群可以了解最新开发进度和技术问题咨询。）：
[![输入图片说明](http://git.oschina.net/uploads/images/2017/0123/001823_7efad50c_1200081.png "在这里输入图片标题")](http:////shang.qq.com/wpa/qunwpa?idkey=637134af30a27220211c843d801ada14700aca69ee8f4acf13f795fe38ea7b94)

DEMO访问地址：[优客服问答社区（UCKeFu-ASK）](http://112.74.54.80/) ， 访问账号：admin，密码：123456

优客社区是一个基于 Spring Boot 的轻量级社区系统，设计之初是为优客服项目提供在线交流的一个社区平台。
游客社区演示系统访问地址：优客问答社区（UCKeFu-ASK） ，

访问账号：admin，密码：123456

项目组成：

 **1. 前端：LayUI + Freemarker**
 
 **1. 后端：Spring Boot**

 **1. 数据库：MySQL+Elasticsearch** 

项目运行方式：

### 1.  将代码拉取下来

### 1. 编译pom.xml文件，下载好jar包
本项目有两个依赖包，IP2REGION 和 UCKeFu-Core，通过以下指令加入到本地Mavenue仓库：
1、mvn install:install-file  -Dfile=src/main/resources/WEB-INF/lib/ip2region-1.2.3.jar -DgroupId=org.lionsoul.ip2region -DartifactId=ip2region -Dversion=1.2.3 -Dpackaging=jar

2、mvn install:install-file  -Dfile=src/main/resources/WEB-INF/lib/UCKeFu-Core-0.5.0-SNAPSHOT.jar -DgroupId=com.ukefu -DartifactId=UCKeFu-Core -Dversion=0.5.0-SNAPSHOT -Dpackaging=jar
 **确保两个依赖都安装成功** 

### 1. 将项目按照maven格式配置好
### 1. 将ukefu.sql脚本在mysql数据库里运行，创建数据库和表


### 1. 配置项目中的application.properties文件中的数据库连接

### 提示：项目中使用了Elasticsearch，对内存有一定要求，建议分配内存如下：
java -Xms1240m -Xmx1240m -Xmn450m -XX:PermSize=512M  -XX:MaxPermSize=512m -XX:+UseParNewGC -XX:+UseConcMarkSweepGC -XX:+UseTLAB -XX:NewSize=128m -XX:MaxNewSize=128m -XX:MaxTenuringThreshold=0 -XX:SurvivorRatio=1024 -XX:+UseCMSInitiatingOccupancyOnly -XX:CMSInitiatingOccupancyFraction=60 -Djava.awt.headless=true  -XX:+PrintGCDetails -Xloggc:gc.log -XX:+PrintGCTimeStamps -jar UCKeFu-ASK-1.0.3-SNAPSHOT.jar


至此配置就结束了，运行一下查看效果吧！


# 优客服
优客服是一个多渠道融合的客户支持服务平台，包含WebIM，微信，电话，邮件，短信等接入渠道!

 **1. WebIM在线客服** 
优客服提供WebIM功能，在线坐席能够通过工作台操作界面，接收来自WebIM的咨询请求，优客服通过整合多个渠道来源，让坐席在同一个工作界面上处理来自PC端、移动端、微信端，微博等渠道的服务请求。
 **2. 社交媒体** 
接入微信和微博渠道，将社交媒体渠道的的咨询请求接入进入 优客服 坐席工作平台，让客服统一响应和受理
 **3. 邮件、短信** 
多种邮件处理方式，能够将邮箱的消息转为坐席的待处理任务，可以将待处理任务或邮件转为工单





 **优客服将会分版本实现全部的功能，V1.0中将包含以下部分功能：** 
 **1、后台管理**
系统后台管理功能，包括系统用户管理，客服坐席管理，系统角色管理、组织机构管理，WebIM接入管理，接入设置
 **2、WebIM在线客服**
访客管理、访客邀请、WebIM网站端多风格切换，访客用户唯一身份识别与跟踪，老用户识别，IP与地理位置识别转换，访客轨迹，访客停留记录，访客实时对话，通信消息，表情包，客户消息多媒体类型消息处理；坐席与用户统一路由排队（ACD），实时提示坐席当前客户正在输入的内容，坐席状态切换、坐席绩效管理
 **3、联系人管理**
公共联系人，私有联系人，联系人贡献与分配
 **4、联络记录**
坐席与客户之间的通信记录，包含WebIM对话，微信对话（V2.0功能）等
 **5、常用语（FAQ）维护**
公共常用语维护（话术），坐席私有常用语维护


![输入图片说明](http://git.oschina.net/uploads/images/2017/0205/104057_4a8ab4e9_1200081.png "在这里输入图片标题")

![输入图片说明](http://git.oschina.net/uploads/images/2017/0205/104114_95778c4c_1200081.png "在这里输入图片标题")

![输入图片说明](http://git.oschina.net/uploads/images/2017/0205/104132_323c5211_1200081.png "在这里输入图片标题")

![输入图片说明](http://git.oschina.net/uploads/images/2017/0205/104042_ca0fd40f_1200081.png "在这里输入图片标题")

![输入图片说明](http://git.oschina.net/uploads/images/2017/0206/224016_351784fa_1200081.png "在这里输入图片标题")

![输入图片说明](http://git.oschina.net/uploads/images/2017/0206/222355_531978d6_1200081.png "在这里输入图片标题")

![输入图片说明](http://git.oschina.net/uploads/images/2017/0216/075820_b823fcdf_1200081.png "在这里输入图片标题")



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)