 
	 
 

> 针对SpringBoot 封装的一系列的快捷包 提供公共的Controller、自动化拦截器、启动加载资源接口、线程池管理

[![Maven metadata URI](https://img.shields.io/maven-metadata/v/http/central.maven.org/maven2/cn/jiangzeyin/fast-boot/common-parent/maven-metadata.xml.svg)](https://mvnrepository.com/artifact/cn.jiangzeyin.fast-boot/common-parent)
![Hex.pm](https://img.shields.io/hexpm/l/plug.svg)
![jdk](https://img.shields.io/badge/JDK-1.8+-green.svg)
[![travis](https://travis-ci.org/jiangzeyin/Fast-boot.svg?branch=master)](https://travis-ci.org/jiangzeyin/Fast-boot)

## 安装

### Maven
在SpringBoot项目的pom.xml 添加如下代码

     
         cn.jiangzeyin.fast-boot 
         common-parent 
         VERSION 
     

注：VERSION 请更换为公共maven库最新的版本号

## 版本变更

- [Release版本变更说明](/CHANGELOG-1.x.md)

## 文档

[博客地址](http://blog.csdn.net/jiangzeyin_/article/details/78709043)

[参考API](https://gitee.com/keepbx/common-parent/javadoc)

## 依赖
[SpringBoot starter-web](https://docs.spring.io/spring-boot/docs/current-SNAPSHOT/reference/htmlsingle/#spring-boot-starter-web)

[HuTool](https://gitee.com/loolly/hutool/)

[fastjson](https://github.com/alibaba/fastjson)

[J2Cache](https://gitee.com/ld/J2Cache)

## 子项目：

# 1.common-boot

> 此模块主要封装Boot 程序的常用工具和内存缓存
>
>如：公共的Controller、自动化拦截器、启动加载资源接口、线程池管理

**maven坐标**

     
         cn.jiangzeyin.fast-boot 
         common-boot 
     


地址：[https://gitee.com/keepbx/common-parent/tree/master/common-boot](/common-boot)

# 2.common-redis

> 此模块主要是封装了SpringBoot 里面包含Redis 的操作支持动态指定使用数据库编号


**maven坐标**

     
         cn.jiangzeyin.fast-boot 
         common-redis 
     

特点：支持动态指定Redis 索引库编号

地址：[https://gitee.com/keepbx/common-parent/tree/master/common-redis](/common-redis)


### 提供bug反馈或建议

- [码云](https://gitee.com/keepbx/common-parent/issues)
- [Github](https://github.com/jiangzeyin/Fast-boot/issues)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)