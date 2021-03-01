# Athena-ZigBee AT指令集

----

### AT+R 重启模块

命令：

> AT+R

返回：

> +R=OK

1秒后重启

----

### AT+Z 恢复为出厂设置

命令：

> AT+Z

返回：

> +Z=OK

1秒后重启并恢复出厂设置

----

### AT+VER 查看固件版本号

**查询：**

> AT+VER

**返回：**

> +VER=2017.10M

----

### AT+RSSI 查询信号强度

**查询：**

> AT+VER

**返回：**

> +RSSI=9

----

### AT+MAC 查看硬件MAC地址

**查询：**

> AT+VER

**返回：**

> +MAC=xxx

### AT+UART 查询/设置串口

----

### AT+CLEAR 清除网络环境

----

### AT+TYPE 查询/设置设备类型

参数格式：

> =`[TYPE]`

### AT+STAT 查询模块运行状态

----

### AT+PAN 查询设置PANID

参数格式：

> =[PANID]

----

### AT+CH 查询/设置信道

参数格式：

> =[CHANNEL]

----

### AT+GPIO 查询/设置本地GPIO

**参数格式：**

> =`[GROUP:PIN]` , `[TTL]`

- `STATE` 状态，值范围：[TL, TH]，分别是低电平和高电平；

**查询端口的电平状态**：

> AT+GPIO=[GROUP:PIN]

返回：

> +GPIO= [GROUP:PIN] , [TTL]

**设置端口电平状态**：

> AT+GPIO=[GROUP:PIN], [TL, TH]
> 1: AT+GPIO=0:1,TL // 设置P0_1端口为低电平
> 2: AT+GPIO=1:4,TH // 设置P1_4端口为高电平

返回：

> +GPIO=`OK` // 成功
> +GPIO=`ERR,IODIR` // 状态错误：GPIO端口非输出模式

----

### AT+RGPIO 查询/设置远程GPIO

----

### AT+IOPULL 查询/设置本地端口的输入模式

**参数格式：**

> = `[GROUP]`, `[PULL]`

- `PULL` 输入模式，值范围：[PU, PD]：
  1. `PU` PullUp，上拉；
  2. `PD` PullDown，下拉；

查询：

> AT+IOPULL=[GRUOP]
> e.g: AT+IOPULL=0 // 查询P0上拉下拉状态

返回：

> +IOPULL=[GROUP]:[PULL]
> e.g: +IOPULL=0:PU // 当前P0为上拉状态
> e.g: +IOPULL=1:PD // 当前P1为下拉状态

设置：

> AT+IOPULL=[GRUOP],[PULL]
> e.g: AT+IOPULL=0,PD // 设置P0为下拉状态
> e.g: AT+IOPULL=1,PU // 设置P1为上拉状态

返回：

> +IOPULL=OK

----

### AT+IODIR 查询/设置本地端口输入输出

**参数格式：**

> = `[GROUP:PIN]`, `[DIR]`, `[INMODE]`

- `DIR` IO方向，值范围：[DI, DO]：
  1. `DI` DirInput 输入方向
  2. `DO` DirOutput 输出方向

- `INMODE` 在IO方向不输入时生效，表示端口输入模式，范围: [MP, MN]
  1. `MP` ModePull 上拉下拉模式。需要在 AT+INPULL 指令中配置；
  2. `NM` ModeNone 三态（高阻）模式。

----

### AT+RIODIR 查询/设置远程端口输入输出

> 通过点对点通讯实现

----

### AT+INTTRI 查询/设置中断触发方式

**参数格式：**

> =`[GROUP]`,`[PULL]``

**查询：**

> AT+INTTRI=`[GROUP]`
> e.g: AT+INTTRI=0   // 查询P0组的中断触发方式

返回：

> +INTTRI=[GROUP]:[PULL]
> e.g: +INTTRI=2:PD // 返回当前P2组的中断触发方式为PullDown下降沿触发。

**设置：**

> AT+INTTRI=`[GROUP]`,`[PULL]`
> e.g: AT+INTTRI=1,PU // 设置P1组为PullUP上升沿触发方式；

返回：

> +INTTRI=OK

----

### AT+INT 查询/设置本地端口中断

**参数格式：**

> =`[GROUP, PIN]`, `[STATE]`

- `STATE` 使能，值范围：[EN, DIS]，分别是禁用和启用；

**查询：**

> AT+INT=`[GROUP,PIN]`

**返回示例：**

> +INT=[GROUP:PIN],[STATE]
> e.g: +INT=0:1:SE // 当前P0_1端口启用中断
> e.g: +INT=1:5:SD // 当前P1_5端口禁用中断

**设置：**

> AT+INT=[GROUP:PIN],[STATE]
> e.g: AT+INT=0:4,SE // 设置P0_4端口，启用中断
> e.g: AT+INT=2:1,SD // 设置P2_1端口，禁用中断

**返回：**

> +INT=`OK`

----

### AT+RINT 查询/设置远程端口中断

> 通过点对点通讯实现

----

### AT+PWM 查询/设置本地PWM

**参数格式：**

> =`[PIN] `, `[PWN] `, 

----

### AT+RPWN 查询/设置远程PWM

> 通过点对点通讯实现

----

### AT+ADC 查询/设置本地ADC

**参数格式：**

> =`[PIN] `

----

### AT+RADC 查询/设置远程ADC

> 通过点对点通讯实现

----

### AT+CNF_PWM 设置PWM波周期

**参数格式：**

> =`[PWM_PERIOD] `, 



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)