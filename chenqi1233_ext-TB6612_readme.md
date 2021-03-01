# TB6612FNG微型双路直流电机驱动模块
DFRobot微型双路直流电机驱动基于TB6612FNG驱动IC设计，采用特殊逻辑控制方式，仅需4根管脚即可实现双路电机控制，相比纯芯片而言，减少了两个IO管脚，为Arduino等控制器节约了宝贵的IO资源，可以应用在更多领域中。

![](./arduinoC/_images/featured.png)

# 积木

![](./arduinoC/_images/blocks.png)

# 示例程序

**注意** 

- UNO工作电压是5V，电机可以正常运行
- microbit、掌控用的两用扩展板电压是3.3V，使用时会出电机不转动，设置最高速度。或者外接电源。

- LOW = 0; HIGH = 1; PWM = 0~255
- PWM1,PWM2：分别为两个电机控制的使能端(可使用PWM调速)
- DIR1,DIR2：正反转控制信号输入端。比如，DIR1=0，M1电机正转; DIR1=1，M1电机反转。

![](./arduinoC/_images/example.png)

![](./arduinoC/_images/example1.png)



 

# 支持列表

|主板型号|实时模式|ArduinoC|MicroPython|备注|
|-----|-----|:-----:|-----|-----|
|uno||√|||
|micro:bit||√|||
|mpython||√|||
|leonardo||√|||
|nano:bit||√|||
|mega2560||√|||


# 更新日志

V0.0.1 基础功能完成

v0.0.2 适应版本，修改名称


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)