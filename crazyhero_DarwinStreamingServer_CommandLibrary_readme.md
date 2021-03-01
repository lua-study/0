#DarwinStreamingServer_CommandLibrary

> 该库中的所有代码仅用于学习，商业运用必须遵守Apple的License。

## 用于编译文件
CommonUtilitiesLib中的文件是用于编译的

## 用于注释的文件

> 主要是vs2015的“反人类”的注释要求导致这个文件夹的产生

CommonUtilitiesLib_comment_package中的文件用于注释，有少许改动

## 关于cmake编写

### 在cmake文件夹下的两个宏文件很重要，可以用于自己的cmake项目

1. cotire.cmake:使用了预编译宏
2. addframework.cmake:Mac平台使用了framework链接条件宏

### 编译
> 以likeUnix平台为例

1. first use `mkdir build && cd build`
2. then use `cmake .. -DDSS_BUILD_SHARED_LIBRARIES=ON/OFF` to make a library
3. use `cmake .. -DDSS_BUILD_SHARED_LIBRARIES=ON/OFF -GXcode` to build a project for xcode
4. use `cmake .. -DDSS_BUILD_SHARED_LIBRARIES=ON/OFF -G"Visual Studio 14"` to build a project for visual studio 2015

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)