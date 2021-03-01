[NanUI](http://netdimension.github.io/NanUI/)基于ChromiumFX项目进行开发，它能让你在你的Winform应用程序中使用HTML5/CSS3/Javascript等网页技术来呈现用户界面。同时NanUI提供了原生窗口和定制化的无标题栏无边框窗口，你能使用全部使用网页技术来设计你的程序界面。

NanUI基于MIT协议，所以无论你使用NanUI来开发商业项目或者开源、免费项目都不受任何限制，只需要遵照[协议文件](https://github.com/NetDimension/NanUI/blob/master/LICENSE)中规定的，在你的软件中声明使用了NanUI技术即可。

![NanUI](http://img.blog.csdn.net/20171226150643379)

**注意：** 此处仅作为项目的备用GIT存储库，如需获取最新的版本请随时关注[GitHub](https://github.com/NetDimension/NanUI/)主站的代码库。

## 0.6版本更新说明

- 重写了无边框窗口的代码，新版本与旧版对比绘制速度提升了不少。
- 现在NanUI能够支持使用高DPI模式的操作系统了（Win8.1及更新的系统）。
- 从旧版中合并了HtmlUIForm和HtmlContentForm，现在使用Formium基类可以同时实现原生窗口和无边框窗口两种样式。
- 现在从Nuget获取NanUI的包可以自动安装CEF和ChromiumFX的运行库了。

## 更新说明
**2018/4/6**
- 内核升级：内核升级到3239，也就是Chrome63
- 同步：其他更新内容与GitHub同步

**2018/3/2**
- BUG:修正了自定义菜单没用的问题。
- 移除了Formium类构造函数的第二个设置是否采用原生窗口的参数。现在Formium类强制使用无边框的重绘样式。
- 新增了WinFormium类，该类的作用与之前Formium构造函数第二个参数指定为false时效果一致。

**2018/3/1**
- 修正：在DEMO程序中添加了app.manifest文件，通过改文件修正demo程序在高分辨率下不正常的问题。

**2018/2/23**
- 修改：取消了Formium构造函数中的第二个参数，现在窗体强制使用无边框窗体的样式。如果需要使用系统原生窗体，请自行工具箱里添加NetDimension.NanUI.dll中的WebBrowserControl
- 移除了DEMO中的视频测试功能，服务器压力太大，怕老板找我茬。
- **特别提醒：** 在nuget里使用了0.6.xxxx.10版本的朋友请升级到0.6.xxxx.11版，或者自行编译源码，xxxx.10版的Bootstrap.Load函数有问题将导致项目启动失败。

**2018/2/17**

- 改进：现在视频播放时能够正确的支持全屏了。
- 改进：移除了默认的上下文菜单中不常用的功能。

**2018/2/13**

- 改进:更新了Bootstrap的部分初始化逻辑。
- 新功能：AssemblyResourceHandler加入了指定启动目录的功能。

现在Bootstrap的Load方法不需要指定平台和各种目录，新增了NanUI自动探测CEF版本的逻辑，如果按照之前fx文件夹的格式来放置CEF各项文件，只需要执行``Bootstrap.Load()``就可以完成加载，而无需复杂的配置，现在Load方法的两个参数是针对SettingsBuilder、CommandLineHandler快捷代理。在下一个版本的NanUI，Bootstrap将替换成FluentAPI的形式来执行操作，所以目前这些调整也是临时的。

如果还是需要指定特定的CEF文件位置，请单独设置Bootstrap类的LibCefDir、ResourcesDir、LocalesDir三个属性来指定CEF各种文件的位置。

另外，AssemblyResourceHandler加入了指定启动目录的功能。例如老版本的NanUI使用AssemblyResourceHandler时如果资源文件放置于项目的子目录下，那么在调用该资源时需要在url中指定该目录，现在在注册AssemblyResourceHandler时只需要指定baseDir路径，那么就可以跳过该子文件夹直接访问资源。例如，您的资源文件放置于项目的www目录中，那么在指定baseDir为www后，您可以直接通过http://res.app.local/[file.ext]来访问到www目录中对应的文件。


**2018/2/12**

- 新功能：Formium里添加了新的窗体阴影效果，现在可以通过窗体属性ShadowEffect选择传统的GlowShadow和DropShadow(新)两种样式。DropShadow样式效果和Win7的投影效果类似。

**2018/2/11**
- BUG FIX: 修复了一个当拥有并打开了子窗体的主窗体获取焦点时其本身将覆盖子窗体的阴影窗口的问题。
- NEW VERSION: 0.7版的NanUI已在开发中，新版除了继续调整窗口问题外，还将引入新的阴影绘制逻辑，另外类型注册也是新版本的重点内容。

**2018/2/10**
- BUG FIX: 修复了子窗体最小化后主窗体不响应鼠标事件的问题。
- IMPROVE: 优化了窗口逻辑。
- NEW FEATURE: 增加了注册本地文件夹内资源的ResourceHandler，现在可以通过使用Bootstrap的RegisterFolderResources方法来注册一整个文件夹中的资源文件到指定的域名，也就是说除了内嵌资源外，又提供了一种访问磁盘文件的途径。

**2018/1/25**
- 修正: 当FormBorderStyle = None时窗口的边距显示不正常的问题。

**2018/1/23**
- 修正: ShowInTaskBar=True时程序崩溃的问题。

**2018/1/16**
- 修正: ShowInTaskBar=True时窗口阴影效果出现在错误的位置。


**2018/1/10**
- 修正：NanUI.XP运行在32位环境里崩溃的问题。

**2017/12/21**
- 新功能: 添加了一个WebBrowserControl控件。你可以在工具箱里添加这个控件，并且拖到窗口上来使用。

**2017/12/11**
- 修正: n-ui-command不触发并且会导致客户端抛一个JS异常的问题。

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

- [NanUI简介](http://www.cnblogs.com/linxuanchen/p/NanUI-Introduction.html)
- [开始使用NanUI](http://www.cnblogs.com/linxuanchen/p/NanUI-Examples-01-Start-Using-NanUI.html)
- [打包并使用内嵌式的HTML/CSS/JS资源](http://www.cnblogs.com/linxuanchen/p/NanUI-Examples-02-Use-Embedded-Resources-In-NanUI.html)
- [使用网页来设计整个窗口](http://www.cnblogs.com/linxuanchen/p/NanUI-Examples-03-Design-Your-Form-With-Html.html)
- [如何实现C#与Javascript的相互通信](http://www.cnblogs.com/linxuanchen/p/NanUI-Examples-04-Communicate-Between-CSharp-And-JS.html)

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


**QQ**

19843266 **（请注明NanUI技术支持）**



**NanUI交流群**

521854872

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)