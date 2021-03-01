#QQ消息记录
原理: QQ、MSN和skype等的软件使用riched20.dll显示聊天内容的时候，我们做一个riched20代理将内容记录下来.
#编译环境 VS2010
#用法
将编译生成的riched20.dll和系统原来的riched20.orig.dll复制到QQ/BIN 目录下.
启动QQ开始聊天,关闭聊天窗口后,聊天记录保存在 `%TEMP%\chat` (默认在 C:\Users\Administrator\AppData\Local\Temp\chat) 文件夹中。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)