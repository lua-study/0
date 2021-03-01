#Ensemble游戏引擎 2D/3D
	
    使用Ensemble之前,您必须阅读以下几点:
    1.您需要安装Svn与Git,如果没有该软件包,我们提供这些软件包

    Git(必须):
    http://hyuan-10007606.file.myqcloud.com/Git-2.8.2-64-bit.exe

    TortoiseGit(必须):
    http://hyuan-10007606.file.myqcloud.com/TortoiseGit-2.1.0.0-64bit.msi

    TortoiseGit汉化包(可选):
    http://hyuan-10007606.file.myqcloud.com/TortoiseGit-LanguagePack-2.1.0.0-64bit-zh_CN.msi

    TortoiseSVN 64位(必须):
    http://hyuan-10007606.file.myqcloud.com/TortoiseSVN%2064%E4%BD%8D_1.8.7.25475.msi

    你需要将以上软件包都进行安装,汉化包为可选包。
    
    2.开始拉取文件
        1) 创建你所要拉取文件的路径并创建文件夹
        2) 右键=>Git克隆=>URL:https://git.oschina.net/nanchengyinan/ensembleengine.git
        3) 拉取项目后,右键=>TurtoialsGit=>切换/检出=>分支选择 feature/new_branch_ 
        4) 分支选择后,创建自己的分支 右键=>TortoialsGit=>创建分支=>分支名: feature/ _  例如 feature/yhh_1.0
        5) 切换分支,右键=>TortoialsGit=>切换/检出=>分支选择=>选择刚创建的分支 例如 feature/yhh_1.0
    至此,你就可以开始开发项目
    --Build 项目生成位置
    --Ensemble 项目主位置

    3.编译文件
        1) 打开Ensemble下的Ensemble.sln文件 编译通过2015及2015以上的vs版本,其他版本未测试。
        2) 右键解决方案进行生成项目,生成文件位于Build文件夹
    
    4.提交文件
        1) 在提交前,您应该切换到ESEngine最上层目录
            右键=>TortoiseGit=>获取=>勾选修建=>确定
            右键=>TortoiseGit=>合并=>选择分支:remotes/origin/feature/new_branch_ 
            右键=>Git提交->"feature/ - "
            日志信息填写您所修改的内容=>勾选设置作者=>添加"Signed-off-by"=>提交
        2) 右键=>TortoiseGit=>推送=>确定
        3) 打开项目首页=>点击+Pull Request=>源分支选择你的分支=>目标分支选择 feature/new_branch_ 
        4) 编写标题为你修改的内容=>说明为你修改的具体内容=>审查人员选择(引擎部分yhh,游戏部分li2lin)=>测试人员选择(引擎部分yhh,游戏部分li2lin)=>勾选必须审查代码=>勾选必须测试=>创建

#已完成功能
    1.基础UI
        1)按钮
        2)输入框
        3)图片框
        4)进度条
        5)界面承载控件
        6)标签
    2.游戏支持mod系统
    3.基础游戏运行
    4.基础输入/输出
    5.支持C#脚本
    6.支持Lua脚本

#预发布功能
    1.新增mod功能
    2.新增基础游戏框架
    3.新增Tiled地图支持

#未来实现
    1.为框架添加IOC功能
    2.新增Farseer物理引擎
    3.新增Zip解析
    4.新增Jitter辅助物理引擎
    5.新增Json数据解析
    6.新增3D音频库
    7.新增Spine动画
    8.新增mp3解码器

#本项目分为引擎和游戏两部分,加入我们
    引擎QQ群:552438279   游戏QQ群:23528675
    官网:http://hyuan.org



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)