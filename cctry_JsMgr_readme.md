##JsMgr是什么?

项目简介：对FireFox火狐浏览器的JavaScript脚本引擎[SpiderMonkey](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey "SpiderMonkey官网")做的二次封装，封装成类库`JsMgr`，供C++程序调用。 
方便在C++中进行与JavaScript脚本代码的交互，调用JavaScript脚本中的相关函数，或者对象的函数等等。 

本库为`开源库`。由 [VC驿站](http://www.cctry.com/ "打开VC驿站论坛") 整理发布。[打开原帖](http://www.cctry.com/thread-253008-1-1.html)


开源地址：[https://git.oschina.net/cctry/JsMgr](https://git.oschina.net/cctry/JsMgr)


###目录结构介绍：
    
    JSMGR
    ├─Example
    │  ├─Example1        #--例子文件:演示加载js文件并运行，取出运行结果
    │  ├─Example2        #--例子文件:演示执行内存中的js代码，取出运行结果
    │  ├─Example3    	#--例子文件:演示执行多个参数的js代码，取出运行结果
    │  └─Example4    	#--例子文件:演示js调用C语言代码，执行并返回运行结果
    ├─js185_static
    │  ├─include     	#--SpiderMonkey的头文件
    │  └─lib	  	   #--SpiderMonkey的静态库:MT/MTD
    ├─JsMgrStaticLib 	#--项目文件	
    └─src			    #--JsMgr源文件


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)