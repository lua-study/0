## JNI 学习

[NDK](https://developer.android.com/training/articles/perf-jni)

**javah**,**javap**

### JNI注册两种方法:
- 静态注册
  - 生成方法规则: Java_完整包名_类名_方法名
> 一种是通过javah,获取一组带签名函数，然后实现这些函数。这种方法很常用，也是官方推荐的方法。

- 动态注册
> 还有一种就是JNI_OnLoad方法。

## 查看方法签名
**javap -s 包名**

例如: javap -s com.assess15.ndkdefault.jni.JNIString
得到: (Ljava/lang/String;)V

---

## 添加log

### 1. 在build.gradle中,添加ldLibs,如下

```Groovy
defaultConfig {
  ndk { ldLibs("log") }
}
```

### 2. 在cpp文件中添加,如下:
```cpp

// 添加头文件
#include  
#define LOG_I(...)  ((void)__android_log_print(ANDROID_LOG_INFO,"nate",__VA_ARGS__))

// 打印日志
LOG_I("from c log");

```

## CMakeLists.txt 中message输出日志,哪里查看?
- 右侧 Gradle -> build -> 点击执行:build
- Run 中即可查看输入日志

CMake message() API
```
message([ ] "message to display" ...)
```

 关键字，可以指定消息的类型：
```
(none)         = 重要消息
STATUS         = 附带消息
WARNING        = CMake警告，继续处理
AUTHOR_WARNING = CMake警告（dev），继续处理
SEND_ERROR     = CMake错误，继续处理，但跳过生成
FATAL_ERROR    = CMake错误，停止处理和生成
DEPRECATION    = 如果分别启用了变量CMAKE_ERROR_DEPRECATED或CMAKE_WARN_DEPRECATED，则CMake弃用错误或警告，否则无消息
```


使用示例:
```
message("CMAKE_SOURCE_DIR = ${CMAKE_SOURCE_DIR}")
message(STATUS "PROJECT_SOURCE_DIR = ${PROJECT_SOURCE_DIR}")
message(WARNING "CMAKE_BINARY_DIR = ${CMAKE_BINARY_DIR}")
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)