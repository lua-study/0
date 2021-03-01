### 1、AutoUpdater 项目介绍
> AutoUpdater 是一个基于 ClickOnce 发布后的自动更新组件，解决客户端软件自动升级的重要解决方案。
### 2、为什么不直接使用ClickOnce
> 使用过 ClickOnce 的人，都知道ClickOnce 应用程序就是任何使用 ClickOnce 技术发布的 Windows 窗体或控制台应用程序。ClickOnce 应用可以自行更新。开发人员可以指定更新行为；网络管理员也可以控制更新策略。

> 从上面可以看出ClickOnce 无疑是微软对Client/Server模式部署的最佳解决方案，但正是因为它的强大而又简单。但正是他的简单而无形的把一些定制化的操作拒绝于门外。 如：
 - 1、 用户不能自己指定安装路径。
 - 2、 对自动更新流程不能做定制化的操作。
 - 3、对自动更新的UI不能定制化的设计。
 - 4、程序集模糊处理（防止逆向的手段）并未集成到 Visual Studio IDE 或 ClickOnce 部署过程中，需要手动执行发布过程（过程麻烦且复杂） 。
 - ···· 等等一些特殊化的操作。
> 正是因为这些特殊化，所有我们要有定制化，开发定制化升级插件 AutoUpdater 正是为了解决这些特殊的问题。
### 3、AutoUpdater 为什么基于ClickOnce
> 使用过 ClickOnce 的人都感叹它的强大与方便，写完代码，立刻编译发布一气呵成，方便又有效率。正是因为ClickOnce 把发布模式集成在了开发工具（Visual Studio IDE ）里，我们只需要简单的配置，就可以把项目更新文件发布到服务端。

### 4、AutoUpdater 的使用
- ##### 1、下载 AutoUpdater 已经编译好的程序 （AutoUpdateLib.dll、AutoUpdater.exe），地址： https://gitee.com/longqin/AutoUpdater/attach_files

![编译好的文件](https://images.gitee.com/uploads/images/2019/0301/164204_166cf25f_1270779.png "屏幕截图.png")
- ##### 2、拷贝AutoUpdater.exe文件到项目下，并在文件上 右键 -> 属性 -> 复制到输出目录 ： 选择如果较新则复制。

![AutoUpdater.exe](https://images.gitee.com/uploads/images/2019/0301/164552_9b7af953_1270779.png "屏幕截图.png")

- ##### 3、 添加应用选择 AutoUpdateLib.dll。

![AutoUpdateLib.dll](https://images.gitee.com/uploads/images/2019/0301/165033_1d25259f_1270779.png "屏幕截图.png")

- ##### 4、 修改 Program.cs 类 Main函数 代码
```C#
        [DllImport("user32.dll")]
        public static extern void SwitchToThisWindow(IntPtr hWnd, bool fAltTab);

        ///  
        /// 应用程序的主入口点。
        ///  
        [STAThread]
        static void Main(string[] args)
        {
            // 判断是否更新成功
            bool AutoUpdateSuccess = AutoUpdate.CheckSuccess(args);
            if (!AutoUpdateSuccess)
            {
                Process Aup = AutoUpdate.CheckRunning();
                // 判断更新程序是否在运行
                if (Aup != null)
                {
                    SwitchToThisWindow(Aup.MainWindowHandle, true);    // 激活，显示在最前
                    return;
                }
                if (!AutoUpdateSuccess)
                {
                    try
                    {
                        // ClickOnce 发布后的 xxx.application http请求路径
                        string CheckUpdatesUrl = "http://xxxxx.com/xxxxx/xxxxxxx.application";
                        if (AutoUpdate.CheckUpdates(CheckUpdatesUrl, args))
                        {
                            return;
                        }
                    }
                    catch (AutoUpdaterFileNotExistException e)
                    {
                        MessageBox.Show(e.Message, "提示");
                    }
                }
            }
            Application.EnableVisualStyles();
            Application.SetCompatibleTextRenderingDefault(false);
            Application.Run(new From());
        }
```
> 以上配置已经在代码层面配置完毕，注意： xxx.application 需要发布到服务端才能获取。

- ##### 5、ClickOnce 发布配置
> 这里不做过多的发布配置说明，不懂的百度搜索或者查看[官网文档](https://docs.microsoft.com/zh-cn/visualstudio/deployment/publishing-clickonce-applications?view=vs-2015)。

![1](https://images.gitee.com/uploads/images/2019/0301/171438_4268cc30_1270779.png "屏幕截图.png")
![2](https://images.gitee.com/uploads/images/2019/0301/171556_a9feac8e_1270779.png "屏幕截图.png")
![3](https://images.gitee.com/uploads/images/2019/0301/171640_c1f48c8c_1270779.png "屏幕截图.png")

> 配置好以上内容后就可以立即发布更新了，发布后先把安装项目打包成安装文件，发个客户安装， 我这边使用的是：InstallShield Limited Edition for Visual Studio 工具。

- ##### 6、查看效果
- 项目进行组件发布

![发布成功](https://images.gitee.com/uploads/images/2019/0301/172218_47f9af85_1270779.png "屏幕截图.png")
- 客户端检测到更新进行更新

![更新](https://images.gitee.com/uploads/images/2019/0301/172329_b33354cc_1270779.png "屏幕截图.png")

- 更新过程

![更新过程](https://images.gitee.com/uploads/images/2019/0301/172540_8aaf7565_1270779.png "屏幕截图.png")
- 更新完成

![更新完成](https://images.gitee.com/uploads/images/2019/0301/172617_eaf218f2_1270779.png "屏幕截图.png")

### 5、参考文档
- 1、[VS 之 InstallShield Limited Edition for Visual Studio 2015 图文教程](https://www.cnblogs.com/xinaixia/p/5473815.html)
- 2、[自动更新组件分享 - 圣殿骑士 - 博客园](https://www.cnblogs.com/KnightsWarrior/archive/2010/10/20/1856255.html)
- 3、[发布 ClickOnce 应用程序](https://docs.microsoft.com/zh-cn/visualstudio/deployment/publishing-clickonce-applications?view=vs-2015)

> 作者： 神马不是神 2019-03-01 - qq联系 : 272358695



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)