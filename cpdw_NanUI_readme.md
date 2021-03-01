[NanUI](http://netdimension.github.io/NanUI/)基于ChromiumFX项目进行开发，它能让你在你的Winform应用程序中使用HTML5/CSS3/Javascript等网页技术来呈现用户界面。同时NanUI提供了原生窗口和定制化的无标题栏无边框窗口，你能使用全部使用网页技术来设计你的程序界面。

NanUI基于MIT协议，所以无论你使用NanUI来开发商业项目或者开源、免费项目都补收任何限制，只需要遵照[协议文件](https://github.com/NetDimension/NanUI/blob/master/LICENSE)中规定的，在你的软件中声明使用了NanUI技术即可。

![NanUI](http://images2015.cnblogs.com/blog/352785/201605/352785-20160518180435701-1461536015.png)

## 0.6版本更新说明

- 重写了无边框窗口的代码，新版本与旧版对比绘制速度提升了不少。
- 现在NanUI能够支持使用高DPI模式的操作系统了（Win8.1及更新的系统）。
- 从旧版中合并了HtmlUIForm和HtmlContentForm，现在使用Formium基类可以同时实现原生窗口和无边框窗口两种样式。
- 现在从Nuget获取NanUI的包可以自动安装CEF和ChromiumFX的运行库了。

## 更新说明
**2017/11/24**
- 修正了内置的html属性n-ui-command在页面中没有包含script标记时最大化、最小化、关闭命令不触发的问题。
- 重新上传了CEF2987的依赖项，之前上传的我犯了个错误，32位的依赖文件其实是64位的，这会导致系统在32位环境中无法执行的问题。
- 最新的Nuget包已上传，最新版的是0.6.2987.5，依赖项的版本是3.2987.1601.3；XP版的版本号是0.6.2526.2，依赖项不变。

**2017/9/25**
- 修正：如果项目中不存在全球化微信资源时，程序报找不到dll文件的错误。
- 修改正：如果html中有下拉列表控件，点击展开控件时移动窗口导致下拉框移位的问题。

**2017/9/22**
- 添加了NetDimension.NanUI.XP项目，NanUI0.6也支持Window XP了，它基于CEF3.2526.1373
- 现在NanUI0.6开源了，源码已提交。本来不想开源的，但是昨天跟个业内大佬聊了不少，还是得到了些鼓励。也希望在今后的开发中，能够有更多的代码贡献者。

## 如何编译

编译当前版本的NanUI需要支持C#7.0语法的编译器，推荐的编译工具有且只有Visual Studio 2017。

## 发布
从0.6版本起，暂时不在提供NanUI的源码，当前页面中的源码是案例源码。稳定版的NanUI包通过Nuget进行分发。
**Nuget包管理器**
```
PM> Install-Package NetDimension.NanUI
```

**NetDimension.NanUI.XP - 支持Window XP的NanUI 0.6版本**
```
PM> Install-Package NetDimension.NanUI.XP
```


**手动下载**
Nuget.org搜索NanUI，然后根据需求来手动下载NanUI的Nuget包。如果不会用Nuget，请自己Google/Bing/Baidu，别来问我谢谢。

## 如何使用
**初始化NanUI**
```C#
namespace TestApplication
{
	using NetDimension.NanUI;
	static class Program
	{
		[STAThread]
		static void Main(string[] args)
		{
			Application.EnableVisualStyles();
			Application.SetCompatibleTextRenderingDefault(false);

			//初始化CEF: 设置CEF的相关Path
			//如果要使用Nuget自动下载的fx文件夹结构，需要手动指定各个文件夹的路径

			var result = Bootstrap.Load(PlatformArch.Auto, System.IO.Path.Combine(Application.StartupPath, "fx"), System.IO.Path.Combine(Application.StartupPath, "fx\\Resources"), System.IO.Path.Combine(Application.StartupPath, "fx\\Resources\\locales"));
			
			if (result)
			{
				// Load embedded html/css resources in assembly.
				Bootstrap.RegisterAssemblyResources(System.Reflection.Assembly.GetExecutingAssembly());

				Application.Run(new Form1());

				Application.Exit();
			}

		}
	}
}

```


**使用原生的窗口样式来使用NanUI**
```C#
namespace TestApplication
{
	public partial class Form1 : Formium

	{

		public Form1()
			//Load embedded resource index.html and not set form to no border style by the second parameter.
			: base("http://res.app.local/index.html", false)
		{
			InitializeComponent();
		}
	}
}
```

**使用无边框模式来使用NanUI**
```C#
namespace TestApplication
{
	public partial class Form1 : Formium

	{

		public Form1()
			//Load embedded resource index.html and set form to no border style by igrone the second parameter or set it to true.
			: base("http://res.app.local/index.html")
		{
			InitializeComponent();
		}
	}
}
```

## 文档

暂时没时间写，后面会陆续更细，也可以直接下载例子看。

## 资助

如果你喜欢我的工作，并且希望NanUI持续的发展，请对NanUI项目进行捐助以此来鼓励和支持我继续NanUI的开发工作。你可以使用**微信**或者**支付宝**来扫描下面的二维码进行捐助。

![Screen Shot](http://ohtrip.cn/media/beg_with_border.png)

海外用户也可以通过Paypal转账的方式来进行捐助。

[![DONATE](http://ohtrip.cn/media/PayPal-donate-button.png)](https://www.paypal.me/mrjson)

## 付费服务
**技术支持** - ￥100.00起

如果在使用NanUI的时候遇到无法解决的问题，本人提供付费技术支持。如需付费技术支持，请扫码下方二维码添加本人微信。

**版本定制** - ￥299.00

目前NanUI支持Chromium 3.2526(Chrome 47)和Chromium 3.2987(Chrome 57)两个版本，如需其他版本请联系购买定制。

**购买支持MP3/H264编码的CEF** - ￥699.00

NanUI提供的CEF运行框架与[http://opensource.spotify.com/cefbuilds/index.html](http://opensource.spotify.com/cefbuilds/index.html)下载的一致，都是编译自CEF官方的开源代码，因此原生是不提供MP3、MP4、H264等商业格式支持的。如果你的项目中需要使用这些技术，你可以按照CEF的文档自行对CEF进行重新编译，当然，也可以联系我付费购买。

扫描下方二维码或者加QQ与本人联系

**添加微信**

![微信](http://images2017.cnblogs.com/blog/352785/201709/352785-20170918143606493-1425889329.jpg)

**QQ**

19843266

**请注明NanUI技术支持**

**NanUI交流群**
521854872

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)