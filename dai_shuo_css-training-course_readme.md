# 开发工具下载

| 名称              | 版本         | 下载                                                         | 其他                                                         |
| ----------------- | ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Java JDK**      | 8u221        | [下载](https://download.oracle.com/otn/java/jdk/8u221-b11/230deb18db3e4014bb8e3e8324f81b43/jdk-8u221-windows-x64.exe?AuthParam=1564030461_f407c975dedfd557ee0e0cb748c160ff) | 无法下载请先注册Oracle账号，[Oracle JDK1.8下载专题网页](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) 。 |
| **Maven**         | 3.6.1        | [下载](http://mirror.bit.edu.cn/apache/maven/maven-3/3.6.1/binaries/apache-maven-3.6.1-bin.zip) | Maven[下载专题网页](https://maven.apache.org/download.cgi)   |
| **Mysql**         | 8.0          | [下载](https://dev.mysql.com/get/Downloads/MySQLInstaller/mysql-installer-community-8.0.17.0.msi) | 如果8.0版本无法安装可以 [下载Mysql5.5](https://dev.mysql.com/downloads/mysql/5.5.html#downloads) [Visual Studio 2015 x64 Redistributable](https://download.microsoft.com/download/9/3/F/93FCF1E7-E6A4-478B-96E7-D4B285925B00/vc_redist.x64.exe) 需要其他VS安装包请到[微软下载中心](https://www.microsoft.com/zh-cn/download/default.aspx) |
| **IntelliJ IDEA** | 2019.2       | [下载](https://download.jetbrains.8686c.com/idea/ideaIU-2019.2.exe) | [大学生免费版](https://blog.csdn.net/liangllhahaha/article/details/88703890)、[IntelliJ IDEA官方旗舰版和社区版](https://www.jetbrains.com/idea/?fromMenu) 其他途径： - 某度：搜索IntelliJ IDEA激活码  - 某宝：IntelliJ IDEA全家桶激活码 |
| **Spring Tools**  | 4.0          |    [下载](https://spring.io/tools)                                                          | Spring官方工具： -Spring Tools 4  for Eclipse -Spring Tools 4  for Visual Studio Code -Spring Tools 4  for Theia) |
| **vscode**        | Version 1.37 | [下载](https://vscode.cdn.azure.cn/stable/f06011ac164ae4dc8e753a3fe7f9549844d15e35/VSCodeUserSetup-x64-1.37.1.exe) |                                                              |
| Notepad++         | v7.7.1.      | [下载](https://notepad-plus-plus.org/repository/7.x/7.7.1/npp.7.7.1.Installer.exe) |                                                              |

**Node.js** 版本V10.16.3

| 系统平台                  | 32位                                                         | 64位                                                         |                                                              |
| :------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Windows Installer（.msi） | [32位](https://nodejs.org/dist/v10.16.3/node-v10.16.3-x86.msi) | [64位](https://nodejs.org/dist/v10.16.3/node-v10.16.3-x64.msi) |                                                              |
| Windows二进制文件（.zip） | [32位](https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x86.zip) | [64位](https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip) |                                                              |
| macOS安装程序（.pkg）     |                                                              | [64位](https://nodejs.org/dist/v10.16.3/node-v10.16.3.pkg)   |                                                              |
| macOS Binary（.tar.gz）   |                                                              | [64位](https://nodejs.org/dist/v10.16.3/node-v10.16.3-darwin-x64.tar.gz) |                                                              |
| Linux二进制文件（x64）    |                                                              | [64位](https://nodejs.org/dist/v10.16.3/node-v10.16.3-linux-x64.tar.xz) |                                                              |
| Linux二进制文件（ARM）    | [ARMv6](https://nodejs.org/dist/v10.16.3/node-v10.16.3-linux-armv6l.tar.xz) | [ARMv7](https://nodejs.org/dist/v10.16.3/node-v10.16.3-linux-armv7l.tar.xz) | [ARMv8](https://nodejs.org/dist/v10.16.3/node-v10.16.3-linux-arm64.tar.xz) |
| 源代码                    | [节点v10.16.3.tar.gz](https://nodejs.org/dist/v10.16.3/node-v10.16.3.tar.gz) |                                                              |                                                              |



注意：

- 32位系统不可以安装64位软件、64位系统可以兼容安装32位软件。
- 部分软件自动识别32位和64位(例如Mysql)。
- Mysql安装时需要先安装Visual Studio的支持包，如果无法安装Mysql Server 安装工具会提示具体信息。



# 工具安装及设置

**安装Java JDK**

安装JDK完成后设置环境变量：我的电脑—>属性—>高级系统设置—>高级—>环境变量—>系统变量

| 变量名    | 变量值(JDK默认安装路径为C:\Program Files\Java\jdk1.8.0_221) | 操作 |
| --------- | ----------------------------------------------------------- | ---- |
| JAVA_HOME | C:\Program Files\Java\jdk1.8.0_221                          | 新建 |
| CLASSPATH | .;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar                 | 新建 |
| Path      | %JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;                        | 编辑 |

**注意：**

- 不要设置在**用户变量**
- **变量名**与**变量值**不要包含**空格**和**中文符号**
- **编辑变量值**尽量增加在最前面以分号结束，放在最后面有可能导致**变量无法生效**
- 有些时候需要重启系统,环境变量才生效
- MySQL、Maven、IDEA、Eclipse等等开发工具需要先安装Java jdk才可以正常安装使用
- 如果**环境变量**还是无法生效请重新设置一遍。

**检验：**运行—>cmd—>java  -version

C:\Users\Sx>java -version
**java version "1.8.0_221"**
Java(TM) SE Runtime Environment (build 1.8.0_221-b11)
Java HotSpot(TM) **64-Bit Server VM** (build 25.221-b11, mixed mode)

------

注意：见到版本信息即配置成功？

- 不一定，例如看到版本信息，但是依赖jdk环境的tomcat服务启动时发生闪退，这也是JDK环境变量没有设置好导致的。

------



**Maven安装**

**尽量解压Maven到非系统盘[避免重装系统导致重新下载所有的依赖包 ]  (—_—!!!）。**

设置环境变量：我的电脑—>属性—>高级系统设置—>高级—>环境变量—>系统变量

| 变量名     | 变量值(假设Maven安装路径 F:\apache-maven-3.6.1) | 操作 |
| ---------- | ----------------------------------------------- | ---- |
| MAVEN_HOME | F:\apache-maven-3.6.1                           | 新建 |
| Path       | %MAVEN_HOME%\bin;                               | 编辑 |

**检验**：运行—>cmd—>mvn -v

C:\Users\Sx>mvn -v
**Apache Maven 3.6.1** (d66c9c0b3152b2e69ee9bac180bb8fcc8e6af555; 2019-04-05T03:00:29+08:00)
**Maven home: F:\apache-maven-3.6.1\bin\..**
**Java version: 1.8.0_221**, vendor: Oracle Corporation, runtime: **C:\Program Files\Java\jdk1.8.0_221\jre**
Default locale: zh_CN, platform encoding: GBK
OS name: "windows 10", version: "10.0", arch: "amd64", family: "windows"

- 见版本信息即成功

  

**Maven配置**

（例如安装路径位为：  F:\apache-maven-3.6.1\conf\settings.xml）

| 设置下载路径               |
| -------------------------- |
| 增加到settings.xml文件55行 |

```xml
 ${env.MAVEN_HOME}/repository 
```



| 设置下载加速                  |
| ----------------------------- |
| 替换settings.xml文件146-159行 |

```xml
 
   
     alimaven 
     aliyun maven 
     http://maven.aliyun.com/nexus/content/groups/public/ 
     central 
   
 
```



| 设置Maven默认的JDK版本                                       |
| ------------------------------------------------------------ |
| 添加到settings.xml文件161行以后的  标签中间 |

```xml
 
	 jdk-1.8 
	 
		 true 
		 1.8 
	 
	 
		 1.8 
		 1.8 
		 1.8 
	 
 
```

**后续还需要在开发工具Eclipse或IDEA中配置Maven。**



------



**Mysql 安装和设置**

- 安装请看官方文档或者搜索某度即可

- 账号密码 **root/root**(开发阶段使用简弱密码即可，部署环境请使用复杂密码)

- 新建数据库**一定要**设置编码**UTF-8**

  

------



**IntelliJ IDEA 安装和设置**

- 安装请看官方文档或者搜索某度即可

  

**IntelliJ IDEA 常用设置**

| 设置           | Ctrl+Alt+S(Settings)                                         | 操作  |
| -------------- | ------------------------------------------------------------ | ----- |
| 界面主题及字体 | Appearance & Behavior > Appearance > Size                    | Apply |
| 代码编辑区字体 | Editor > Font > Size                                         | Apply |
| 文件编码       | Editor > File Encodings > UTF-8                              | Apply |
| 代码提示快捷键 | KeyMap>Main menu>Code>Completion >  Basic设置(Alt+/) Cycle Expand Word 设置(Alt+空格) | Apply |



------



**Platform Settings SDKs设置**

| 设置          | Ctrl+Alt+Shift+S > **Platform Settings > SDKs** | 操作  |
| ------------- | ----------------------------------------------- | ----- |
| JDK home path | C:\Program Files\Java\jdk1.8.0_221              | Apply |



**Project 和 Modules SDK设置(可选)**

| 设置        | Ctrl+Alt+Shift+S > **Project Settings** | 操作  |
| ----------- | --------------------------------------- | ----- |
| Project SDK | 1.8                                     | Apply |
| Modules     | Sources>8 Dependencies > 1.8         | Apply |

注意：需要新建项目和Modules以后设置。



------



**IntelliJ IDEA JAVA 编译设置(可选)**

| 设置                     | Ctrl+Alt+S > Build, Execution, Deployment >  Compiler > Java Compiler | 操作  |
| ------------------------ | ------------------------------------------------------------ | ----- |
| Project bytecode version | 8                                                            | Apply |
| Target bytecode version  | 1.8                                                          | Apply |

注意：需要新建项目和Modules以后设置。



------



**IntelliJ IDEA Maven设置**

| 设置                 | Ctrl+Alt+S>Build, Execution, Deployment>Build Tools>Maven    | 操作  |
| -------------------- | ------------------------------------------------------------ | ----- |
| Maven home directory | F:\apache-maven-3.6.1                                        | Apply |
| User settings file   | Override>选择配置好的F:\apache-maven-3.6.1\conf\settings.xml文件 | Apply |
| Local Repository     | 根据setting.xml文件自动更新                                  | Apply |



------



**IntelliJ IDEA 安装Spring Assistant插件**

安装Spring Assistant插件为IDEA新建项目的时候增加spring initializr选项，用于创建spring boot项目：

| 设置        | Ctrl+Alt+S > Plugins | 操作    |
| ----------- | -------------------- | ------- |
| Marketplace | 搜索Spring Assistant | Install |



------



**Nodejs使用淘宝 NPM 镜像**

大家都知道国内直接使用 npm 的官方镜像是非常慢的，这里推荐使用淘宝 NPM 镜像。

淘宝 NPM 镜像是一个完整 npmjs.org 镜像，你可以用此代替官方版本(只读)，同步频率目前为 10分钟 一次以保证尽量与官方服务同步。

你可以使用淘宝定制的 cnpm (gzip 压缩支持) 命令行工具代替默认的 npm:

```
$ npm install -g cnpm --registry=https://registry.npm.taobao.org
```

这样就可以使用 **cnpm** 命令来安装模块了：

```
$ cnpm install [name]
```

更多信息可以查阅：http://npm.taobao.org/。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)