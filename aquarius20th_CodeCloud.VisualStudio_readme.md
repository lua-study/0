# 码云的 Visual Studio 扩展
## 安装

- 在[码云/CodeCloud.VisualStudio附件](https://git.oschina.net/GitGroup/CodeCloud.VisualStudio/attach_files)中下载预先编译好的vix安装文件。
- 下载完成之后，双击运行，中间会提示关闭所有VisualStudio相关进程，按照相关提示操作即可。

注：CodeCloud.VisualStudio只支持VisualStudio 2015/2017。稳定之后，将会发布到VisualStudio市场，安装就简单了。

## 使用

VisualStudio版本管理相关功能，都集中在Team Explorer面板中。CodeCloud.VisualStudio的各个功能，都是穿插在Team Explorer的工作流中。

### Connect页

打开VisualStudio之后，展开Team Explorer面板，默认是Connect页（也可以在Team Explorer面板的工具栏中，点击插头图标，跳转到Connect页).  

如果用户尚未登陆码云, 可以在Connect页的CodeCloud区中，点击连接按钮登陆；若尚未注册码云，可以在该区中，点击注册按钮，在码云网站进行注册。  

用户登陆码云之后，CodeCloud区中，会显示已经通过VisualStudio克隆到本地的码云项目。可以在CodeCloud区的工具栏进行克隆、克隆和退出操作。双击该区中项目列表的项目，可以打开该项目。

#### 克隆

在CodeCloud区的工具栏中，点击克隆按钮，会弹出当前用户的所有码云项目，包括所属组的项目。选择其中一个，点击下方克隆按钮即可。

注：默认情况下，所选项目会被克隆到%USERPROFILE%\Source\Repos下，可以通过下方浏览按钮修改clone路径。若该目录下有和项目同名的文件夹存在，克隆按钮将不可用。

#### 创建项目

在CodeCloud区的工具栏中，点击创建项目按钮，在弹出的对话框中，填写项目名称, 描述，选择Git ignore和协议，项目路径之后，点击下方创建按钮即可。

#### 退出

在CodeCloud区的工具栏中，点击退出按钮，即可登出当前用户。

注：登陆信息会从系统清除，但是克隆的项目仍旧保留，下次登陆仍旧存在。

#### 推送到码云
在Team Explorer的Synchronization/Publish页中，通过其中的码云区，可以将当前Git项目发布到码云（需要填写项目名，描述，协议，以及所有权）。若当前项目不是Git项目，可以在VisualStudio右下角，点击Add to Source Control / Git，将其转化为Git项目，然后再发布。

#### 提交更改

Team Explorer本身集成了Commit，pull，sync等Git操作，可以通过Team Explorer工具栏的小房子按钮，跳转到Home页进行相关操作。 CodeCloud.VisualStudio插件将码云特有的Attachment，Pull Request，Issues，Statistics，Wiki功能，都集成到该页面，通过点击相关按钮，跳转到对应的页面。

## 演示动画

![image](./docs/images/option.gif)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)