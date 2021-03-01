#Broccoli
这是一个基于LoRa的无线通讯协议，有协调器（BROCCOLI_COORDINATOR），路由器（BROCCOLI_ROUTER），终端节点（BROCCOLI_ENDDEVICE）。结构简单，无需RTOS操作系统。
协调器可以连接多个路由器，路由器可以连接多个终端节点，终端节点不可以直接连接协调器。
如果网络只有两级可以使用路由器（BROCCOLI_FREE_ROUTER）和终端节点（BROCCOLI_ENDDEVICE），也可以使用协调器（BROCCOLI_COORDINATOR）和路由器（BROCCOLI_ROUTER）。
为了避免产生僵尸网络，路由节点不能接力。

本协议适合区域型物联网使用，比如智能水表系统。每个小区内放置一个协调器，每栋楼放置一个路由器，每户水表使用一个终端节点。终端节点可以使用锂亚电池供电，只要通讯不是特别频繁可以使用几年。

单片机和LoRa模块接口代码在level0.c中
测试代码使用了stm32f030f4p6单片机的硬件SPI和sx1278相连，实际应用时请使用低功耗单片机比如STM32L0

单片机	SX1278
PA0	->	DIO0
PA3	->	RESET
PA4	->	NSS
PA5	->	SCK
PA6	->	MISO
PA7	->	MOSI

最近在做一个项目，做完后会把通讯部分整理上来。短距离传感器用了2.4G数据比较密集的时候速率越高越省电，长距离通讯使用了LoRa 433M。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)