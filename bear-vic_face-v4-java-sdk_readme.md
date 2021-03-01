![输入图片说明](http://www.qiansou.cn/Scripts/img/lmxt-1bi1.jpg "在这里输入图片标题")  
# Version 5.5
千搜科技第五代人脸识别引擎java接口 
> 提供技术支持及免费试用，非盈利项目可申请免费使用

## 目录结构 
> 提供基于jni和jna两种版本的java SDK，使用者根据自身情况选择其中一种API即可
1. jni 存放java调用C++ SDK的jni源码 
2. jna 新的不需要依赖jni代码的java API 源码(maven工程)
* 建议直接引入jna的工程，根据说明即可 不依赖其它包使用

## java版本
java version "1.8.0_111"  
Java(TM) SE Runtime Environment (build 1.8.0_111-b14)  
Java HotSpot(TM) 64-Bit Server VM (build 25.111-b14, mixed mode)  

## jni是C++包装层，要区分32位还是64位。
32位SDK: x86_32\JNIWisFaceEngineWrap.dll  
64位SDK: x86_64\JNIWisFaceEngineWrap.dll  
java SDK: com.qs.face.jar    


## 注意：将C++的SDK目录加入系统Path目录 

License文件需要放在 java.exe的根目录下。  

## 注意
这个版本的java sdk 是针对的windows系统编译的  
如果您使用的是linux系统，java的代码基本不用改变，但是需要自己编译jni目录下的c++代码，将本地c++的sdk libWisFaceEngineWrapV4.so 包装成jni 供java调用


## 技术支持
QQ： 2843028512  
QQ群：567619263

## Q&A
Q：sdk是离线的还是基于云服务通过http调用的。  
A: 离线的，不需要联网，直接在本地计算 

## C++ SDK 下载连接
baidu网盘： [v5.5](https://pan.baidu.com/s/1Ik0UEOr-_ZDaqAmqdsNiDw#list/path=%2F)  

[#人脸识别软件下载地址](http://qiansou.cn/home/productinfo.html)




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)