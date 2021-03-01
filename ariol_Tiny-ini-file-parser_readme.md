#Tiny ini 文件解析

## 简介

这是一个简单的ini文件解析功能的实现


- tiny_ini_file.h/tiny_ini_file.c: ini文件解析的API声明以及实现
- main.c:  一个简单的测试程序.

## 如何编译?

本实现是使用的标准c语言，没有系统相关的部分，顾它是可以跨平台的。
- gcc 
- visual studio 
- Qt Creator
- ...
等等这些都可以对其进行编译

## 注意
本项目中使用到了strdup这个API，所以在使用gcc编译的时候，可能会出现错误，此时需要预定义一些宏来
启用strdup这个API。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)