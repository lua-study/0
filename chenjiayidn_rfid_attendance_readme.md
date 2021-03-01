![939B9F9E22694470BECF84EB82AAA0E0.png](https://likecy.oss-cn-beijing.aliyuncs.com/939B9F9E-2269-4470-BECF-84EB82AAA0E0_1574657946708.png)
# RFID考勤系统说明文档
	服务器说明：
1.	Workerman服务版本基于linux，服务器环境需要linux任意版本。
2.	Apache2.0+php7.1+mysql，其中php7.1需要开启fileinfo配置。
3.	长链接服务进程启动方式：
-  cd到程序运行根目录：
 ![图片 1.png](https://likecy.oss-cn-beijing.aliyuncs.com/%E5%9B%BE%E7%89%87%201_1574656780965.png)
- 命令运行：php start.php start 开启服务监听：
 ![图片 2.png](https://likecy.oss-cn-beijing.aliyuncs.com/%E5%9B%BE%E7%89%87%202_1574656826179.png)
- 或者执行脚步后台进程方式启动：sh ./start.sh
 ![图片 3.png](https://likecy.oss-cn-beijing.aliyuncs.com/%E5%9B%BE%E7%89%87%203_1574656834062.png)
- 关闭websocket服务：php start.php stop
- 查询websocket后台服务状态：php start.php status
- 开启服务器防火墙8282端口：
![图片 4.png](https://likecy.oss-cn-beijing.aliyuncs.com/%E5%9B%BE%E7%89%87%204_1574656862385.png)
若8282端口被其他端口占用，需要修改websoket端口，位于application/config.php 修改目前状态8282端口即可。注意sever_ip修改为服务器当今状态ip，比方说学校内网服务器内网地址为：10.11.2.17 即修改sever_ip为10.11.2.17
![图片 5.png](https://likecy.oss-cn-beijing.aliyuncs.com/%E5%9B%BE%E7%89%87%205_1574656872314.png)
 
4. Thinkphp框架数据库配置：在项目数据库文件夹目录找到数据库文件导入数据库，在application/database.php里面修改数据库ip端口及账号密码：
 ![图片 6.png](https://likecy.oss-cn-beijing.aliyuncs.com/%E5%9B%BE%E7%89%87%206_1574656885838.png)
5.	Thinkphp 框架apache伪静态服务配置。映射apache对外目录为项目根目录下的public目录。
6.	项目后台默认账户名admin 密码admin666

	单片机端说明：
1.	修改wifi名称及密码，服务器ip及websocket服务端口，分配唯一设备编号pid作区分。
 ![图片 8.png](https://likecy.oss-cn-beijing.aliyuncs.com/%E5%9B%BE%E7%89%87%208_1574656987305.png)

2.	Arduino环境配置烧录esp32-dev的环境
- 安装第三方库  ：序列化服务器json字符串为数组使用；
- 安装第三方库 :esp32移植esp8266的websocket库。（esp8266供电3.3v 达不到rfid模块要求的5v供电，故采用esp32模块带5v供电）；
- 引入esp32软串口库 ，此处保留esp32的原串口用于调试信息的输出，方便维护。
- Rfid模块连接esp32软串口1:
 ![图片 9.png](https://likecy.oss-cn-beijing.aliyuncs.com/%E5%9B%BE%E7%89%87%209_1574657012413.png)

云中有鹿
2019/11/25
		


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)