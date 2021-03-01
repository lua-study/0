# HC小区物联网平台是前后端完全开源并免费商用的物联网平台，前段采用主流vue+elementui+admin 后端采用spring boot，项目是特别简单架构容易上手对接自己的硬件，欢饮加群827669685交流


## 代码说明

   back 为后端项目 建议用idea打开（maven项目）

   front 为前段项目 需要安装nodejs 

## 如何安装

### 前段

	1、安装nodejs

	2、进入到 front 目录下 执行 npm install 安装依赖

	3、启动 npm run dev

	4、浏览器访问 http://localhost:8080

### 后端

	1、idea 用maven的方式打开back项目

	2、maven 导入包，可以在命令行中执行 mvn clean install

	3、打开src\main\java\com.java110.things.ThingsApplicationStart.java 

	4、运行main方法

### 相关视频

[https://www.bilibili.com/video/BV1pK4y1t7re](https://www.bilibili.com/video/BV1pK4y1t7re)

### 功能列表

#### 已完成功能

1、设备门禁管理，开门和重启

2、人脸下发，可以通过HC小区管理系统 或者HC业主版小程序下发管理

3、门禁人脸管理

4、开门记录，开门上报HC小区管理系统和开门实时监控，实时显示业主物业费情况 方便保安催缴功能

5、门禁协议选择，此系统非常适合做二次开发对接自己的门禁，通过门禁协议切换来切换不通的门禁使用

6、硬件交互日志记录，实时监控和硬件的通信情况

7、系统配置 

8、设置当前系统使用的小区

9、云端交互日志记录，实时查看和云端HC小区管理系统通信是否正常

#### 计划功能

1、道闸对接

2、监控对接

3、考勤设备对接（目前正在对接中）


### 演示

	以下效果图

![image](docs/img/login.png)
![image](docs/img/menjing.png)
![image](docs/img/menjingxiyi.png)
![image](docs/img/settings.png)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)