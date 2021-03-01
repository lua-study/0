# ModernUI 样式的 Windows 窗体应用程序

**ModernUI Form** 这个库能够方便的让你的.Net WinForm程序看起来更像Win8/8.1和Win10那种款式的窗口。

它重绘了窗口的整个边框，并且实现了窗口投影的效果。你能够通过设置**BorderSize**属性来调整边框的大小，还能通过**BorderActiveColor**和**BorderInactiveColor**属性来设置边框的颜色。除此之外，窗口的投影颜色也是可以通过属性来进行修改的。

![Screen Shot](http://ohtrip.cn/media/20180212015259.jpg)



## 实现的功能
- 创建Win8/8.1和Win10那种所谓的ModernUI样式的WinForm窗口。
- 创建出来的窗口支持完整的系统动画效果，绝非单纯的将FormBorderStyle设置为None，如果是这样，那么这个项目毫无意义。
- 能够快速的绘制窗口投影，目前实现了两种不同款式的投影。
- 支持窗口的**Active/Inactive**状态中呈现不同的视觉样式。

## NuGet
```
PM> Install-Package NetDimension.WinForm.ModernUI
```



## 使用方法
简单的通过继承**ModernUIForm**即可。本人的另外一个开源项目**NanUI**（这是一个能够使用HTML5/CSS3和JavaScript技术来编写WinForm窗口界面的库）将在未来的版本中使用这个库来作为界面承载的基础库。

```C#
	public partial class Form1 : ModernUIForm
	{
		public Form1()
		{
			InitializeComponent();
		}
	}
```

根据你的意愿，在窗口设计器的属性窗口中，找到UI这个分类，下面有所有你需要使用到的设置属性。

**特别注意：** 请不要尝试使用**Visual Studio 2017**以外的工具编译源码（当然，如果有更高版本的VS是例外，我在写这段话的时候最拽的VS目前就2017）。有朋友下载了源码说代码BUG一大堆完全编译不了，那我只能遗憾的告诉你是你太OUT，因为C#都已经7.0了。

## 更新说明
**2018/2/12**

- 更新了项目，修改了众多bug，现在已经基本稳定了。
- 现在支持两种投影效果。

## 捐赠

如果你喜欢我的工作，作为鼓励，你可以请我喝杯咖啡。当然，这不是必须的。

同时也欢迎你加入到任何项目的开发中来。

![Screen Shot](http://ohtrip.cn/media/beg_with_border.png)

[![DONATE](http://ohtrip.cn/media/PayPal-donate-button.png)](https://www.paypal.me/mrjson)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)