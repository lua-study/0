weixin-java-tools

GITHUB转载，非本人编写

[![Build Status](https://travis-ci.org/chanjarster/weixin-java-tools.svg?branch=develop)](https://travis-ci.org/chanjarster/weixin-java-tools)
![Maven Central](https://img.shields.io/maven-central/v/me.chanjar/weixin-java-parent.svg)

===========

微信公众号、企业号Java SDK。

详细文档请看 [wiki](https://github.com/chanjarster/weixin-java-tools/wiki)。

## Quick Start

如果要开发公众号（订阅号、服务号）应用，在你的maven项目中添加：

```xml
 
   me.chanjar 
   weixin-java-mp 
   1.3.1 
 
```

如果要开发企业号应用，在你的maven项目中添加：

```xml
 
   me.chanjar 
   weixin-java-cp 
   1.3.1 
 
```

## SNAPSHOT版

本项目的BUG修复和新特性一般会先发布在*-SNAPSHOT版里供大家预览，如果要使用*-SNAPSHOT版，则需要在你的pom.xml中添加这段：

```xml
 
   
       
       sonatype snapshots 
       https://oss.sonatype.org/content/repositories/snapshots/ 
   
 
```

## 升级指南

* [1.0.3升级指南](https://github.com/chanjarster/weixin-java-tools/wiki/1_0_3升级指南)
* [1.1.0升级指南](https://github.com/chanjarster/weixin-java-tools/wiki/1_1_0升级指南)
* [1.1.1升级指南](https://github.com/chanjarster/weixin-java-tools/wiki/1_1_1升级指南)

## 关于Pull Request

非常欢迎和感谢对本项目发起Pull Request的同学，不过本项目基于[git flow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)开发流程，因此在发起Pull Request的时候请选择develop分支。

且本项目代码风格是用2个空格代表一个tab，因此在发起PR时注意一下，否则很容易发生在IDE格式化代码后与原代码产生大量diff，这样我在阅读PR的时候就很困难。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)