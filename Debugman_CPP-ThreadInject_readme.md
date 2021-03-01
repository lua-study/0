#C++ 线程注入

写在前面，本人C++纯小白，公开项目是希望获得更多朋友的帮助，如果您正好能解决我目前遇到的问题，希望您能在问题中回复我，项目改进后会继续保持开源，感谢大家的支持

编译 dll.cpp 为 dll：
g++ -shared -o dll.dll dll.cpp

编译 Inject.cpp 为 exe：
g++ Inject.cpp

执行 Inject.exe 注入DLL线程到 calc.exe 中

[已解决]目前遇到的问题：注入的DLL并没有执行
感谢 @ysc3839 在过程中对我的帮助

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)