### 查尔斯动态加载启动器(CharlesLoader)

Charles v4.x 查尔斯动态加载启动器(CharlesLoader)

#####使用方法:
>
* Windows系统下,请将out/win目录下的CharlesLoader.jar和run-charlesloader.bat两个文件放置在Charles/lib/下运行run-charlesloader.bat即可，
* Linux和Mac OS X等类Unix系统下,可以使用自行看bat中的命令写shellcode脚本启动

######此方法无需破解jar包即可完成Charles的破解，并且不影响升级

######最新版v4.1.4相对v.4.0.2以前旧版本比较，明文类名已混淆.请查看分析记录文档.

>关于依赖javassist.jar库文件打包的问题,可以先解压javassist.jar里的class字节码再重
新打包为CharlesLoader.jar.这样就只需要一个CharlesLoader.jar文件啦O(∩_∩)O~.

>打包具体可以看jar-x-javassist-1.bat和jar-m-2.bat文件(.sh文件在类Unix系统下使用).先运行后缀-1,再运行后缀-2的文件.

---

最新charles v4.1.4破解文件. 附件里下载

> 1. Windows 平台,将下载的charles.jar文件覆盖到安装目录下的lib文件夹下即可完成破解!
> 2. Mac 平台,将下载的charles.jar文件右键 Charles.app 显示包内容,覆盖到Content->Java下即可完成破解! 

注意: 这是v4.1.4的破解文件,不确定其他版本也同样适用!请下载相应版本文件,然后改名为charles.jar.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)