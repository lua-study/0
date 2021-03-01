## Qt小项目之串口助手控制LED

![](https://wcc-blog.oss-cn-beijing.aliyuncs.com/img/UART_Demo/qt.jpg)

### 前言

最近刚学了一点Qt开发上位机，尝试着做个小软件练练手。查找了很多资料，做了一个简单的串口助手，可以实现串口基本发送和接收功能，支持中文显示，还可以控制STM32开发板上的两个LED。

#### 1.软件界面

![](https://wcc-blog.oss-cn-beijing.aliyuncs.com/img/UART_Demo/%E4%B8%BB%E7%95%8C%E9%9D%A2.jpg)

#### 2.主要功能：

- 启动自动搜索本机串口，或者手动点击搜索键扫描串口
- 自定义波特率
- 支持中文显示
- 支持发送新行

#### 3.实际效果：

![](https://wcc-blog.oss-cn-beijing.aliyuncs.com/img/UART_Demo/Animation.gif)

花了大概3天时间吧，找了很多资料，功能很简单， 但想着是自己一点一点开发的，还是挺有成就感的哈！

写这篇文章是为了总结一下开发的过程和一些知识点，主要包括两部分，上位机的实现和STM32端程序的实现。

### Qt上位机的实现

#### 0.新建一个Dialog项目

新建一个Dialog项目，这3种基类的区别可以根据你的程序来确定。

>
- 如果需要嵌入到其他窗体中，则基于QWidget创建。
- 如果是主窗体，则基于QMainWindow创建，有菜单栏，状态栏，工具栏等。
- 如果是顶级对话框，则基于QDialog创建。

![](https://wcc-blog.oss-cn-beijing.aliyuncs.com/img/UART_Demo/new_prj.jpg)

#### 1.软件UI界面的设计

使用Qt Designer添加所需要的控件，并进行合理布局，尽量每一个控件，起一个合理易懂的名字。

![](https://wcc-blog.oss-cn-beijing.aliyuncs.com/img/UART_Demo/ui.jpg)

#### 2.串口库的添加

pro文件添加一行：
	
	QT += serialport

对应的头文件包含：

	#include  
	#include  

#### 3.串口自动搜索功能的实现

自动搜索本机串口，并在ComboBox中添加串口号

	ui->cbb_com->clear();
    //运行开始查找可用串口
    foreach(const QSerialPortInfo &info, QSerialPortInfo::availablePorts())
    {
        ui->cbb_com->addItem(info.portName());  //串口号下拉菜单，增加一个条目，为串口号COM4
        qDebug()  ui->btn_uart_Ctrl->text() == "打开串口")   //初始状态，配置串口参数
	    {
	        serial.setPortName(ui->cbb_com->currentText());     //设置串口号、
	        serial.setBaudRate(ui->cbb_baud->currentText().toInt());    //设置波特率
	        serial.setDataBits(QSerialPort::Data8);     //设置串口数据位8
	        serial.setParity(QSerialPort::NoParity);    //无校验位
	        serial.setStopBits(QSerialPort::OneStop);   //1位停止位
	        serial.setFlowControl(QSerialPort::NoFlowControl);
	        //打开串口
	        if(!serial.open(QIODevice::ReadWrite))
	        {
	            QMessageBox::critical(NULL, "提示", "串口打开失败");
	            return;
	        }
	        qDebug()  ui->btn_uart_Ctrl->setText("关闭串口");
	    }
	    else
	    {
	        //关闭串口
	        serial.close();
	        this->ui->btn_uart_Ctrl->setText("打开串口");
	    }
	}

#### 5.串口发送数据

        serial.write("A1\n");     //串口发送A1

#### 6.串口数据的接收和显示，支持中文

QT默认的编码是unicode，不能显示中文的，windows默认使用（GBK/GB2312/GB18030），使用了fromLocal8Bit()函数，实现了从Unicode到本地字符集GBK的转换，用于处理汉语显示乱码等问题

槽函数的实现：

	//串口数据接收并显示
	void Dialog::serialPort_readyRead()
	{
	    QByteArray rx_buf = serial.readAll();   //读取串口接收的数据
	    if(rx_buf.endsWith("\r\n")) //判断接收最后是否是回车换行，即接收完成标志
	    {
	
	    }
	    QString rx_buf_tmp = QString::fromLocal8Bit(rx_buf);    //转换为中文格式
	    qDebug()  tb_rx_buf->append(rx_buf_tmp);
	
	    rx_buf_tmp.clear();
	    rx_buf.clear();
	}

connect语句：

    connect(&serial, & QSerialPort::readyRead, this, &Dialog::serialPort_readyRead);

#### 7.下拉框自定义波特率的实现

	//自定义波特率
	void Dialog::on_cbb_baud_currentIndexChanged(const QString &arg1)
	{
	    if(this->ui->cbb_baud->currentIndex() == 3)
	    {
	        this->ui->cbb_baud->setItemText(3, ""); //调成自定义波特率时，内容设置为空，准备接收输入
	        this->ui->cbb_baud->setEditable(true);
	    }
	    else
	    {
	        this->ui->cbb_baud->setItemText(3, "自定义"); //调成自定义波特率时，内容设置为空，准备接收输入
	        this->ui->cbb_baud->setEditable(false);
	    }
	    serial.setBaudRate(ui->cbb_baud->currentText().toInt());    //即使打开串口后，仍然可以设置波特率
	}

#### 8.发送新行功能的实现

通过一个全局变量实现，发送新行按钮勾选时，标志位置1，然后发送按钮功能里，根据标志位决定是否在末尾添加换行符。

对应的槽函数实现：

	//是否发送新行
	void Dialog::on_cb_send_enter_clicked()
	{
	    if(ui->cb_send_enter->isChecked())
	    {
	        send_enter_flag = true;
	        qDebug()  te_tx_buf->toPlainText().toUtf8();
	
	    if(send_enter_flag == true)
	        tx_buf += "\n";
	
	    serial.write(tx_buf);     //把数据通过串口发送出去
	    tx_buf.clear();
	}
	

#### 9.只改变标签颜色

本来想着通过改变样式表的方式改变颜色

        this->ui->lbe_blue->setStyleSheet("color: rgb(255, 0, 0);");

但是，实际运行时，连字体和大小都改成了默认的，有没有一种只改变颜色其他的格式不变的方法呢？还真有，如下，不过好像只支持标准颜色？

    	QPalette colr;
        colr.setColor(QPalette::WindowText,Qt::red);    //设置标签颜色红色
        this->ui->lbe_red->setPalette(colr);

#### 10.按钮的使能失能控制

以下两行语句效果相同，都是失能按钮功能：

    this->ui->btn_led1_Ctrl->setDisabled(true); //LED控制按钮不可用
    this->ui->btn_led1_Ctrl->setEnabled(false); //LED控制按钮不可用

#### 11.文本显示框设置最大显示行数

    this->ui->tb_rx_buf->document()->setMaximumBlockCount(10);

### 程序的图标、标题设置和打包发布

![](https://wcc-blog.oss-cn-beijing.aliyuncs.com/img/UART_Demo/dialog.jpg)

你不希望窗口的标题是“Dialog”吧，所以添加一个标题和一个好看的图标还是很有必要的。

#### 1.添加标题

添加窗口标题还是很简单的，一行代码：

    this->setWindowTitle("串口控制LED - By wcc ");

#### 2.添加icon图标

- 找一个好看的图标，格式一定要是.ico，像素大小推荐128*128
- 命名为my_app.ico，名字无所谓，不要有中文就好了，放在工程目录下，即和.pro文件和.cpp文件同一个目录。
- 打开.pro文件，最底下添加一行：RC_ICONS = my_app.ico

重新编译就可以看到这种效果了。

![](https://wcc-blog.oss-cn-beijing.aliyuncs.com/img/UART_Demo/icon.jpg)

#### 3.程序文件的生成

构建选项改成Release版本，编译完成后，会在Release目录下生成一个.exe文件，把这个文件单独拷出来放在一个空白的文件夹里，如`D:\QT_Prj\Export\UART_Demo.exe`，可以运行试一下，会提示缺少运行所需要的dll组件

![](https://wcc-blog.oss-cn-beijing.aliyuncs.com/img/UART_Demo/not_fine_qt5_dll.jpg)

而且，这个文件如果单独拷贝到其他没有安装Qt环境的电脑上，也是不能运行的。

所以我们需要添加一些当前程序运行所需要的组件才能正常运行，但是需要添加哪些文件呢？不用担心，Qt早已经想好了，运行MinGW工具：

![](https://wcc-blog.oss-cn-beijing.aliyuncs.com/img/UART_Demo/mingw.jpg)

先进入到exe文件所在的文件夹中：`cd /d D:\QT_Prj\Export`

然后输入命令：`windeployqt UART_Demo.exe`

![](https://wcc-blog.oss-cn-beijing.aliyuncs.com/img/UART_Demo/windeployqt.jpg)

此时，打开exe文件所在的文件夹，可以看到Qt已经为我们添加好了，当前程序运行所需要的组件了。

![](https://wcc-blog.oss-cn-beijing.aliyuncs.com/img/UART_Demo/add_dll.jpg)

这个时候，如果想给别人分享你开发好的上位机软件，就可以直接把这个文件夹拷贝给他。当然也可以安装一个`Enigma Virtual Box`软件，把当前目录下的所有文件打包成一个exe文件。

### STM32端程序的实现

连接串口模块，发送接收短接，可以看出Qt上位机的的收发都是正常的。下一步就是编写STM32端的程序了，很简单，当接收到字符串"A1"时，点亮红灯；当接收到字符串“A2”时，熄灭红灯；当接收到字符串“B1”时，点亮蓝灯；当接收到字符串“B2”时，熄灭蓝灯，每个字符串结尾都有换行符“\n”，即：

上位机发送 | 单片机执行 
:-: | :-: 
A1 | 红灯点亮
A2 | 红灯熄灭
B1 | 蓝灯点亮
B2 | 蓝灯熄灭

实现思路也很简单，即把接收到的字符存入一个字符数组，当接收到“\n”换行标志时，意味着接收完成，判断此时数组的内容，分别和命令比较，如果一致，执行相应的操作，串口1中断服务函数：

	void USART1_IRQHandler(void)
	{
		char dat;
		char flag = 0;
		if(USART_GetITStatus(USART1, USART_IT_RXNE) != RESET)	//接收中断
		{
			dat = USART1->DR;
			if(usart1Len >= 64)									//防止数据过多，导致内存溢出
				usart1Len = 0;
			if(dat == 0x0D || dat == 0x0A)		//回车换行，接收完成，此时的buf不含回车换行
			{
				if(strcmp(usart1Buf, "A2") == 0)	//字符串比较
				{
					UsartPrintf(USART1, "红灯熄灭\r\n");
					GPIO_SetBits(GPIOB, GPIO_Pin_9);
				}
				else if(strcmp(usart1Buf, "A1") == 0)
				{
					UsartPrintf(USART1, "红灯点亮\r\n");
					GPIO_ResetBits(GPIOB, GPIO_Pin_9);			
				}
				else if(strcmp(usart1Buf, "B2") == 0)
				{
					UsartPrintf(USART1, "蓝灯熄灭\r\n");
					GPIO_SetBits(GPIOB, GPIO_Pin_6);			
				}			
				else if(strcmp(usart1Buf, "B1") == 0)
				{
					UsartPrintf(USART1, "蓝灯点亮\r\n");
					GPIO_ResetBits(GPIOB, GPIO_Pin_6);			
				}	
				usart1Len = 0;
				memset(usart1Buf,0,64);
			}
			else
			{
				usart1Buf[usart1Len++] = dat;
			}
			USART_ClearFlag(USART1, USART_FLAG_RXNE);
		}
	}

程序还是很简单。板子是用的中移的麒麟座Mini板，基于F103C8T6的，串口1连接上位机，波特率115200，PB9-红灯，PB6-绿灯，都是低电平点亮。

### 改进和优化的地方

- 按钮发送字符可自定义
- 界面UI的设计优化
- 数据波形的显示
- 发送和接收，16进制和字符模式的切换
- 定时发送功能
- 接收内容保存成文件
- 一个小Bug，不支持多个串口的自动搜索。

### Qt工程和STM32工程下载

由于国内Github下载速度实在令人着急，Qt工程文件和STM32工程文件，还包括Enigma_Virtual_Box的安装包，我都已经上传到国内的码云Gitee上了，有需要的朋友可以在Git中使用以下命令下载：

	git clone https://gitee.com/whik/qt_uart_demo.git

或者是在公众号后台回复**【串口助手】**，我会把下载链接发送给你。

![](https://wcc-blog.oss-cn-beijing.aliyuncs.com/img/UART_Demo/download.jpg)

当然，如果有朋友也在学习Qt开发上位机，欢迎互相交流学习。

-----

### 历史精选文章：

- [一键自动格式化你的代码](http://www.wangchaochao.top/2019/01/23/Keil-Astyle/)
- [C标准库string.h中几个常用函数的使用详解](http://www.wangchaochao.top/2019/01/21/C-String/)
- [Jlink使用技巧系列教程索引](http://www.wangchaochao.top/2019/01/17/Jlink-series/)
- [Jlink使用技巧之烧写SPI Flash存储芯片](http://www.wangchaochao.top/2019/01/12/Jlink-SPI-Flash/)
- [Jlink使用技巧之虚拟串口功能](http://www.wangchaochao.top/2019/01/09/Jlink-UART/)
- [Jlink使用技巧之读取STM32内部的程序](http://www.wangchaochao.top/2019/01/06/Jlink-ReadBack-Hex/)
- [Jlink使用技巧之J-Scope虚拟示波器功能](http://www.wangchaochao.top/2018/10/17/JScope/)

----

欢迎大家关注我的[个人博客](http://www.wangchaochao.top)

或微信扫码关注我的公众号

![](https://wcc-blog.oss-cn-beijing.aliyuncs.com/img/%E6%B1%82%E5%85%B3%E6%B3%A8.jpg)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)