## Embedme项目简介
Embedme是一个基于linux的嵌入式应用类库，包括线程，线程池，定时器，事件分发，消息队列，socket，HttpClient，JSON，SqliteWrapper，Tuple,MD5，CRC，文件，目录，共享内存，互斥锁，串口，日志,配置等开发中常用的模块。Embedme集成了cJson,sqlite,tinyxml,libconfig++等优秀的开源库,并将这些库封装成非常人性化的C++接口,同时Embedme为嵌入式linux应用程序常使用的功能接口提供一个小巧简洁的C++封装库libemb，它可以帮助您快速的构建稳定的嵌入式应用程序，省去广大码农造轮子的重复劳动。libemb库已应用在多个实际项目中，可以放心使用，欢迎各位同行fork本开源库，期待您的建议和开源贡献。
## 注意事项
**本软件遵循LGPL协议,请自觉遵守该协议，否则将追究您的法律责任！**

**如果您使用此源码,请务必保留README在您的工程代码目录下!**
## 编译系统mbuild system
本工程采用自行编写的mbuild系统进行编译,mbuild系统的使用请参考**build/README.md**
###目录树结构

* **app 	-------------应用程序源代码存放目录.**

* **build 	-------------mbuild编译系统源码目录.**

* **libemb ---------为embedme库文件夹,如果您只是使用libemb库,请不要删除或修改该文件夹内的任何文件.**

* **opensource---目录用于集成外部开源库.**

* **output	----------目录为输出目录,用于存储编译过程中间文件及目标文件.**

		
---------------------------------------------------------------------
**在编译前请先确认已安装autoconf,automake,libtool等工具,否则无法编译成功,如遇编译错误，请自行查看错误提示，判断是否是工具未安装。**

##编译说明

**1. cd到工程跟目录下:**

*#cd embedme*

*#ls*

*app*

*build*

*libemb*

*opensource*

*test*

**2. 设置mbuild编译环境:**

*#source build/envsetup.sh*

**3. 设置编译目标体系:**

*#lunch*

**4. 先清理整个工程:**

*#mrprop*

**5. 编译整个工程:**

*#mrball*

注：您也可以使用**mbuild**命令单独编译各个目标，详细方法请参考**build/README.md**

##编码说明
***本工程支持cygwin/Android环境下编译,源码中使用OS_CYGWIN/OS_ANDROID宏来隔离代码，如果不使用宏将默认代码同时支持在Linux,cygwin,Android环境下编译.***

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)