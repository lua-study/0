# Qt测试项目
本项目中包含多个Qt的Demo程序，用于各个模块的测试使用

项目名称 | 插件 | 功能介绍
-------- | ----	| ---------
JSqlServer | 无	| Qt连接SqlServer数据的测试程序
JMySql	| MySQL官方库	| Qt连接MySql远程数据的测试程序
JSQL	| MySQL官方库	| 模仿Navicat软件
JThread	| 无	| 利用继承QObject的方式来使用线程，并操作线程
ImageDemo	| 无	| 实现12306登录点击验证码图片出现火车标志
MulThreadSQL	| MySQL官方库	| 多线程访问数据库
SingleChannel	| QCustomPlot	| 基于QCustomPlot实现波形画图和控制
DrawDXF			| dxflib		| 基于dxflib实现读取dxf文件
FirFilter		| QCustomPlot	| 读取波形数据文件、FFT变换、滤波操作等
MatlabDemo		| 无			| 实现调用MATLAB库
EChartDemo		| ECharts		| 基于ECharts显示柱状图并进行通信
WebFirFilter	| ECharts		| 对波形进行滤波，然后使用ECharts显示波形
JTabWidgetDemo	| 无			| QTabWidget基本操作和样式设置
JMainFrame  	| 无			| Qt搭建软件框架
DxfGraphics		| dxflib		| 基于 GraphicsView 显示线
TabScorllArea	| 				| 仿照网易云音乐设置界面实现滚动显示设置界面
DateEditQSS		| 				| QSS 改造 QDateEdit、QCalendarWidget
FormatData		| 				| 格式化数据工具



## JSqlServer
> 次项目是使用Qt连接SqlServer数据的测试程序
1. 程序初始化时自动连接数据库，并控制台输出连接成功或者失败；
2. 点击界面中按钮可以显示数据中表的数据；
3. 待完善...

注：在项目中的xxx.pro文件中一定要加上sql模块，否则是不行的；  QT += sql

## JMySql
> 次项目是使用Qt连接MySql远程数据的测试程序
1. 程序初始化时自动连接数据库，并控制台输出连接成功或者失败；
2. 点击界面中按钮可以显示数据中表的数据；
3. 待完善...

注1：在本次程序我连接的是远程数据库，为了保证个人信息，程序中已经删除远程数据库信息，如果使用需要填写自己数据库信息

注2：在项目中的xxx.pro文件中一定要加上sql模块，否则是不行的；  QT += sql


## JSQL
> 本软件是模仿Navicat软件来操作MySql和SQL Server数据库，由简单的功能一步一步的完善。

## JThread 		2018-11-09
> 本次小项目是对线程进行实现，利用继承QObject的方式来使用线程，并操作线程

1. 继承QObject方式，然后使用moveToThread；
2. 线程的开始已经线程的终止；
3. 线程中共享变量的互斥锁；

## ImageDemo
> 此小Demo是实现12306登录点击验证码图片出现火车标志。

1. 使用QLabel加载一张12306验证码图片
2. 每次点击图片时保存图片信息；
3. 根据坐标判断每次点击做标；

## MulThreadSQL		2019-06-05
> 多线程访问数据库与单线程会有一点不一样，做了个实验；
1. 程序中使用继承QObject的方式使用多线程；
2. 在现场中访问数据库；
3. 数据库操作部分进行再次封装；

## SingleChannel	2020-02-12
> 基于QCustomPlot实现波形画图和控制
1. 实现画波形曲线
2. 实现放大选中区域波形，改变坐标显示放大部分区域波形
3. 点击鼠标左键画一条线显示曲线点，表示到时起始点
4. 点击鼠标中键还原

![局部放大_到时画线.gif](https://i.loli.net/2020/03/25/TFpEtX1UHyx9qvr.gif "QCustomPlot")

## DrawDXF			2020-2-14
> 基于dxflib实现读取dxf文件并显示
1. 实现基于dxflib读取dxf文件
2. 实现将读取的dxf使用Qt中QGraphicsView、QGraphicsScene、QGraphicsItem等绘制
3. 实现鼠标对图进行放大、缩小、拖拽、还原等功能
4. 鼠标中键还原

![effect.gif](https://i.loli.net/2020/03/25/J7EfS2qhWbsKOgn.gif "dxf")

## FirFilter		2020-3-3
> 波形显示基于QCustomPlot显示波形，FFT变换等通过算法
1. 读取特定数据文件格式的波形数据
2. 通过快速傅里叶变换对波形获取波形频谱图
3. 通过窗口函数法实现FIR滤波器
4. 对输入波形进行滤波最终获取输出波形
5. 对输出波形进行快速傅里叶变换获取频谱波形

## MatlabDemo		2020-3-3
> 注意本次编译器使用了MSVC2017_32bit，测试使用mingw编译器无法使用
1. 使用MATLAB编译出库，MATLAB也需要使用32bit编译，本次使用的是MATLAB2010a版本
2. 使用Qt调用MATLAB库并调用相关函数

## EChartDemo		2020-3-4
> 本次使用Qt MSVC2017_32bit进行编译
1. 引入ECharts的js库，并基于ECharts绘制柱状图
2. 使用QWebChannel库，是Qt和js之间进行通信

![Qt_html_js.png](https://i.loli.net/2020/03/25/TtajhQEwFUOeBzW.png "Echats")

## WebFirFilter		2020-3-5
> 对波形进行滤波，然后使用ECharts显示波形
1. 读取特定数据文件格式的波形数据
2. 通过快速傅里叶变换对波形获取波形频谱图
3. 通过窗口函数法实现FIR滤波器
4. 对输入波形进行滤波最终获取输出波形
5. 对输出波形进行快速傅里叶变换获取频谱波形
6. 波形显示使用ECharts显示

![filter_echarts.png](https://i.loli.net/2020/03/25/XK9MPnglQ6Su412.png "filter_echarts")

![filter_echarts_bandpass.png](https://i.loli.net/2020/03/25/23uDS8albf7AXVP.png "filter_echarts_bandpass")

## JTabWidgetDemo	2020-3-13
> QTabWidget基本操作和样式设置
1. 对QTabWidget方法操作，切换Tab、Tab方向控制
2. 对Tab进行样式设置

## JMainFrame	2020-3-23
> Qt搭建软件框架
1. 实现设置 Logo 的图片
2. 实现双击菜单栏放大、缩小
3. 实现拖动菜单栏
4. 实现最小化、最大化、关闭功能
5. QSS 实现图标上划变换功能
6. 实现推动标题栏到窗口顶部最大化

![title.png](https://i.loli.net/2020/03/25/vp5uQFcJsU3VM9K.png "title bar")

## DxfGraphics	2020-4-3
> 于 GraphicsView 显示线
1. 使用 QGraphicsView、QGraphicsScene 和 QGraphicsItem 显示线段
2. 实现滚轮缩放事件
3. 实现在 Scene 中添加 2w 个线段 item 缩放基本不卡

![DxfGraphics_line.gif](https://i.loli.net/2020/04/03/JYWziRrgxAUHQF9.gif "DxfGraphics line")


## TabScorllArea	2020-4-9
1. 仿照网易云音乐设置界面实现滚动显示设置界面
2. 使用 QSS 设置滚动区域样式
3. 使用按钮快速定位

![scroll_setting.gif](https://i.loli.net/2020/04/09/Fq6HxEnSIbto5W7.gif "scroll setting")

## DateEditQSS	2020-4-15
> QSS 改造 QDateEdit、QCalendarWidget
1. 使用 QSS 重新搭配 QDateEdit，并下拉弹出 QCalendarWidget
2. QCalendarWidget 表头设置渐变色，使用图标设置上/下个月按钮
3. QCalendarWidget 年选择设置图标按钮并修改样式

![date_calendar.gif](https://i.loli.net/2020/04/15/6CdRyQM7fzKFsb4.gif "QDateEdit")

## FormatData	2020-4-24
> 工作中需要提取文件中数据，所以编写一个小工具简化工作量

1. 使用正则式去掉多余数据
2. 使用 QString 中 replace 去掉多余数据

![format_data.gif](https://i.loli.net/2020/04/24/v1E9e37yHdzVghs.gif "format_data")



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)