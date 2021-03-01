# Video_Server

## 开发进度

请在Release版本发布前 不要将此项目用于生产环境 我们将在功能完善 测试通过后发布Release版本 请耐心等待

## 运行环境

系统要求:Windows 64Bit

运行库要求:VC2015(PHP要求)

## 使用教程

生产环境请下载Release版本

Step.1 安装MariaDB

>>Tip:安装时请设置自己的ROOT密码 并开启全局使用UTF-8编码

Step.2 修改设置

>>配置文件位于config/config.php 可修改Mysql,Redis等设置

Step.3 运行Run.cmd 即可启动服务

### 输出乱码

如低于Windows 10/Server 2016的版本运行发生乱码(无法正常显示颜色代码) 请用管理员命令行(cmd) 进入ANSION文件夹 使用此命令
```
ansicon.exe -I
```
然后关闭所有打开的命令行 并重新运行Run.cmd 即可解决

### 安全关闭服务

运行Stop.cmd后 将自动结束Nginx与CGI 但由于CGI保活机制 可能CGI会自动重启 直接关闭CGI窗口即可

等待Worker工作完毕后 可自行将主线程与Worker线程结束

>>Tip:结束机制还有待完善

## 整体架构

当用户将转码文件放入upload文件夹中后 可通过网页管理或其他方式 向Redis中添加一个为Main_Start的Key 主进程检测到后将扫描全部待转码文件后将自动检测MD5 是否以前有重复文件 然后将文件信息添加到数据库 同时进程管理器会自动检测未转码的文件 并分发给空闲线程转码

## 加入我们

此项目QQ群:674511398

PackTeam官方讨论群:296114195 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)