#CheckUpdate.Net

##[DownLoad](http://git.oschina.net/xcong/CheckUpdate.Net/attach_files "version 1.2")

##更新历史
####version 1.2
>+ [新增]添加UpdateFileClient.exe.config文件，修改UpdateFileClient.exe依赖的.Net Framwork 2.0版本与主程序兼容问题
>+ [修改]修改更新程序，下载文件不存在时提示文件出错。

####version 1.1
>+ 【修改】修改窗体文件丢失 
+ 【新增】新增服务端配置项添加安装包位置和版本  
+ 【新增】新增UpdateCommon中VersionHelper下载安装包方法**GetNewVersionToDownloadSetup**。如果需要下载，弹窗提醒，并调用浏览器下载，同时返回True。


##介绍
>**CheckUpdate.Net**是.Net C/S下一个检查更新程序。现有的检查更新方式多种多样，更新程序也大不相同。有个比较出名的 OSAU （参考了他的界面），微软也有比较方便的ClickOnce。自己也尝试了其他的，发现没有合适的就决定自己写一个。
考虑到复用，在.Net Framework2.0下开发。主要就是利用WebClient下载服务器网站目录下的文件，安全性暂没有考虑，比较适用于小型项目。

###注意事项：
1.UpdateFileClient.exe依赖于.Net Framwork 2.0，如果主程序的.Net Framwork版本高于2.0，需要修改UpdateFileClient项目下的App.config文件(默认是兼容4.0)。
如果主程序的.Net Framwork版本为2.0，请删除App.config文件。
>.Net Framwork 4.0是新的CLR，无法兼容旧版CLR。该方案主要兼容在Windows Xp下单独安装了.Net Framework 4.0 版本。
Windows Vista/Win7 已经分别安装.Net Framework 2.0与3.5，具有CLR 2.0特性，需要删除App.config。
    
###1.主要功能
+ 支持单个或多个文件更新
     读取服务端XML配置文件，获取需要修改或新增的文件，然后进行下载，下载完成之后，更新本地版本。
+ 支持更新更新程序本身
     通过配置本地的XML文件，放置更新程序的目录。主程序启动时，进行检查，处理。
+ 服务端支持程序更改配置文件，无需手动更改XML

###2.使用方式
+ ####将主程序运行需要的文件通过XML配置起来
  将Update.xml、UpdateFileClient.exe、UpdateFileCommon.dll添加到主程序相同目录，主程序需要引用UpdateFileCommon.dll。
  将主程序运行所需的文件通过XML进行配置，放在File节点下，初始版本为1。
  配置服务端XML所在路径，当前版本、版本对应的值、临时文件夹、更新程序名称可以采用默认值。
![](http://images.cnitblog.com/blog/494159/201409/241446340765227.png)

+ ####实现更新程序的更新
  需要在主程序中添加一行代码，进行检查临时文件夹是否包含更新程序，如果有，进行剪切操作。
```
using UpdateFileCommon;
//发现新的更新程序，进行剪切到根目录
VersionHelper.CutNewUpdateEXE();
```
+ ####按需添加检查更新代码
  可以在程序启动时或者点击按钮进行检查更新操作。
  检查更新是弹窗进行提醒，需要传两个参数，一个更新描述，一个是否强制更新。对应XML节点是服务端XML的ReleaseNote和IsMustUpdate。
![](http://images.cnitblog.com/blog/494159/201409/241510389512745.png)
  NextShowEvent 事件是点击按钮下次提醒需要执行的操作。

```
    //发现设定的目录存在新的更新程序，进行剪切到根目录
    VersionHelper.CutNewUpdateEXE();

    //检查是否需要下载安装包，不需要下载返回False
    if (!VersionHelper.GetNewVersionToDownloadSetup())
    {
        //检查版本更新
        if (VersionHelper.IsRequiredUpdate())
        {
            string xmlPath = System.AppDomain.CurrentDomain.BaseDirectory + "UpdateFile.xml";
            if (File.Exists(xmlPath))
            {
                //加载XML路径
                XmlDocument doc = new XmlDocument();
                doc.Load(VersionHelper.GetLoaclServerConfigURL(xmlPath));
                //获取值
                var releaseNote = VersionHelper.GetServiceReleaseNote(doc);
                var isMustUpdate = VersionHelper.GetServiceIsMustUpdate(doc);
                PromptingForm form = new PromptingForm(releaseNote, isMustUpdate);
                //赋值委托，点击下次提醒的按钮执行的操作
                form.NextShowEvent += delegate
                {
                    //执行xxx
                };
                context = new ApplicationContext(form);
            }
        }
    }
```
+ ####需要更新时，通过服务端程序设置更新
  ![](http://images.cnitblog.com/blog/494159/201409/241517267325989.png)

  ![](http://images.cnitblog.com/blog/494159/201409/241517466709647.png)

  ![](http://images.cnitblog.com/blog/494159/201409/241518019518017.png)


###源码介绍
![](http://images.cnitblog.com/blog/494159/201409/241519568428316.png)

UpdateFileCommon.dll是主程序必须引用的。里面包含更新提示窗口。包含版本辅助类等信息。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)