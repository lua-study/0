工程目录结构简述
================

此Python网关中间件工程包含在wot_gateway文件夹内，各文件夹及文件功能简述如下：
###

* cfg/
	* dev_property.xml: 设备属性信息（向平台添加设备时用到）
	* gw_property.xml: 网关属性信息（网关注册时用到）
	* res_property.xml: 资源属性信息（向平台添加资源时用到）
	
	* gw_json.cfg: json格式配置文件，目前包括3个域
		* updated:网关是否已经更新过
		* mwid:网关在平台上的ID
		* hwid:网关硬件ID，目前用MAC地址指代
	* local.cfg: 平台相关配置，包括平台IP,服务器端口号，各开放接口URL
	
	* mac_dev_map.cfg: hwid与设备号的本地映射表
	* mac_resID_resPlat_map.cfg:hwid、本地资源ID（我们自己定义的）和平台资源ID的本地映射表


* lib/
	* campra_thread.py:
	摄像头线程模块,接收来自AllJoyn服务端的图片。数据分成两部分，一部分是图片的二进制流，另一部分是头部。头部信息就指明图片是对应哪个MACADDR上的哪个本地资源

	* common.py: 通用模块，包括获取MAC地址、写配置文件等

	* gateway.py: 网关核心类，封装了网关注册、网关更新、删除网关、添加/删除设备、添加/删除资源、上传传感器数据/图像等

	* heartbeat.py: 心跳线程模块，用于定时向平台上传心跳，获取平台上的操作指令。如用微信端控制，则当用微信发送指令时，
	在心跳的返回信息中就可知道命令已下达。目前包含控制红外摄像机和TV

	* init.py: 初使化模块，用以读local.cfg配置文件

	* main.cfg: json格式配置文件，包含心跳间隔时间，python接收传感器、图片等端口号
	* main.py：主模块，采用多线程开发。总共五个线程：主线程、网关资源属性注册线程(数据由AllJoyn服务端发送)、心跳线程、传感器数据上传线程(数据由AllJoyn服务端发送)、图像上传线程(数据由AllJoyn服务端发送)

	* register.py: 网关注册线程（由杨平所写），采用多路复用方式获取网关的设备及资源属性信息(json格式，由AllJoyn服务端发送)，同时建立本地映射表。网关注册信息格式如下：
	    * Mac_address: 设备硬件ID
	    * flags: 0表示有设备进入，需要添加设备及资源；1表示有设备离开，需要注销资源
	    * Res_num: 资源数量
	    * Res: 资源
	        * Res_type: 资源类型
	        * Res_name: 资源名称
		* Res_unit: 资源单位

	* res_data.py: 传感器数据上传线程，接收来自AllJoyn服务端发来的传感器数据，格式封装为json:
	    * Mac_addr: 设备硬件ID
	    * Res_port: 资源本地编号
	    * Res_val: 资源数值

	* restful.py: GET,POST请求python方法封装
	

* log/
	* 日志，目前维护较少


维护人邮箱： merryok@163.com(陈)    876621413@qq.com(杨)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)