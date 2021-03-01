# 利用 Python + OpenCV 实现布洛克城自动夺宝

#### 项目介绍

本来是想研究使用 Python + OpenCV 识别图片的，结果有朋友问这个布洛克城能不能自动点击夺宝，正好拿来练练手
 。灵感和代码参考来自： 
 
`微信《跳一跳》Python 辅助`
 `https://github.com/wangshub/wechat_jump_game`

简陋动图效果如下：

![image](readme-1.gif)

#### 工具介绍
1. Python 3
2. Android 手机
3. ADB 驱动
4. Python + OpenCV 图片处理

#### 使用说明

1. 安装 Python3 
2. 安装 PyCharm
3. 使用 PyCharm block_city_ai 项目代码，
4. 安卓手机连接上电脑，打开列表页，并拖动到如下位置：
![image](readme-2.png)
5. 右键 main.py 运行或使用命令行 python main.py 运行


#### 原理说明

1. 将手机点击到《布洛克城》APP 的可夺宝的名单界面
2. 使用 ADB 工具获取当前手机截图
3. 使用 OpenCV 对截图进行处理并分析，找出有手掌的可点击区域的坐标
4. 使用 ADB 工具模拟点击事件，进入夺宝界面
5. 使用 ADB 工具获取当前手机截图
6. 使用 OpenCV 对截图进行处理并分析，找出目标点击区域的坐标
7. 使用 ADB 工具模拟点击事件，完成夺宝
8. 使用 ADB 工具模拟返回事件，回到可夺宝名单的界面，重复 2~8

#### 交流

目前存在比较大的效率问题，这个跟识别的算法有关，以后有时间再慢慢优化了，欢迎加QQ群交流：78404857

我的布洛克城邀请码：BBAU3C

![image](readme-3.png)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)