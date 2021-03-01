# thinkphp5-layui-GatewayWorker开源多客服系统

#### 介绍
thinkphp5+layui+GatewayWorker开源多客服系统,
支持多客服
权限管理
![客户端](https://images.gitee.com/uploads/images/2019/0321/111548_c81fdcbb_1547089.jpeg "1.jpg")
![后台](https://images.gitee.com/uploads/images/2019/0321/111314_ab26f0f5_1547089.jpeg "2.jpg")
![客服端](https://images.gitee.com/uploads/images/2019/0321/111402_83ff02cd_1547089.jpeg "3.jpg")

#### 软件架构
thinkphp5+layui+GatewayWorker


#### 安装教程

1. a>windows用户需要配置下php环境变量。[php环境变量设置参见这里。](https://www.workerman.net/windows)   
   b>Linux系统可以使用以下脚本测试本机PHP环境是否满足WorkerMan运行要求。  
     curl -Ss http://www.workerman.net/check.php | php 
	 上面脚本如果全部显示ok，则代表满足WorkerMan要求。 
	 如果不是全部ok，则参考下面文档安装缺失的扩展即可。 
	 已有PHP环境安装缺失扩展 
	 安装pcntl和posix扩展： 
	 centos系统 
	 如果php是通过yum安装的，则命令行运行 yum install php-process即可安装pcntl和posix扩展。 
	 具体教程请移步这里.[http://doc.workerman.net/install/install.html](workerman说明文档)。 
	 
2. 下载源码 下载后把vendor\topthink路面下topthink.rar解压下
3. 恢复数据库

#### 使用说明

1. a>windows用户直接运行根目录下“start_for_win.bat”文件 

   b>Linux系统进入源码根目录 

   启动

   以debug（调试）方式启动

   php start.php start

   以daemon（守护进程）方式启动

   php start.php start -d

   停止

   php start.php stop

   重启

   php start.php restart
   
   Linux不会的请移步[workerman说明文档](http://doc.workerman.net/install/install.html)。
   或加QQ群：326842206
2. 目录指向public 
   后台： 
   http://127.0.0.1/admin.php 
   账号密码 admin 123456 
   客户窗口： 
   http://127.0.0.1/chat.php/index/index.html?toid=2 
   这里的toid 是后台添加客服的ID 
   客服后台： 
   http://127.0.0.1/kefu.php 
   账户密码自己在后台添加。 

3.注意！！！！
如果安装后出现class org\auth not found 错误
会tp5的 直接按个权限类，不会的加群，下群里文件
#### 如有疑问请加QQ群：326842206



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)