QQrobot
=======
好久没关注我这个开源代码了，没想到还有人在讨论使用，关注我的最新开源作品，请通过我的个人网站，找到我：http://lieefu.com/
 
    QQrobot是用C++语言开发设计，程序界面、网络通迅等模块使用了Qt，Qt是开源的，跨平台C++程序图形界面框架库,QQrobot具备跨平台特性，可在linux、MAC OS以及Windows等操作系统中运行，集成开发编译环境请到 http://qt-project.org/ 下载。
 
 
    QQrobot基于腾讯公司WebQQ协议实现，可以向QQ群或者是个人自动发送信息。分为两个部分，QQ主体和robot插件。QQ主体解析WebQQ协议，负责QQ号码登录，信息接收和发送功能。robot分析聊天内容，跟据聊天内容智能做出回应。
 
 
    QQ主体窗口内，可监控显示聊天信息、好友列表、群列表和机器人列表。为QQ群或者个人指定随意多个机器人为之提供服务。也提供了信息发送功能，可随时向QQ群或者个人发送信息。
 
 
    robot插件，使用Qt5的plugin技术，可单独开发，编译后拷贝到plugins目录中，QQ主体自动识别安装运行。robot插件只要完成接口RobotInterface内的name和listenandsay方法就ok，name返回robot的名子，listenandsay的参数是收到的聊天内容和发送者信息，返回值是robot回应信息。
 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)