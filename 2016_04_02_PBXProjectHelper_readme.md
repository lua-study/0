> 目录

> 1.[功能介绍](#1-功能介绍)

> 2.[使用方法](#2-使用方法)

> 3.[基础用法](#3-基础用法)

> 3.1[获取分组或文件对象](#3-1-获取分组或文件对象)
 
> 3.2[添加分组](#3-2-添加分组)

> 3.3[移除分组](#3-3-移除分组)

> 3.4[添加Framework](#3-4-添加Framework)

> 3.5[添加动态库](#3-5-添加动态库)

> 3.6[添加静态库](#3-6-添加静态库)

> 3.7[添加头文件](#3-7-添加头文件)

> 3.8[添加Bundle](#3-8-添加Bundle)

> 3.9[添加本地化文件](#3-9-添加本地化文件)

> 3.10[添加ShellScriptBuildPhase](#3-10-添加ShellScriptBuildPhase)

> 3.11[保存变更内容](#3-11-保存变更内容)

> 3.12[添加/删除语言区域](#3-12-添加-删除语言区域)

# 1. 功能介绍

PBXProjectHelper是一个基于Python开发的，目的用于解析和操作PBXProject（XCode项目的配置文件）的工具类库。其提供了非常简单的方法来让开发者对XCode项目进行文件、类库以及项目设置的修改。从而达到自动化维护和管理的目的。

# 2. 集成方式

1. 导入PBXProjectHelper到你的Python脚本中。如：

```
import PBXProjectHelper
```

2. 初始化PBXProjectHelper工具类，并传入pbxproj文件的路径

```
helper = PBXProjectHelper ("/Users/fenghj/Documents/work/Demo/Demo.xcodeproj/project.pbxproj")
```

3. 调用PBXProjectHelper类提供的方法来操作PBXProj文件。如添加一个Group到XCode项目：

```
helper.project.mainGroup.addGroup ("Demo")
```

# 3. 基础用法

## 3.1 获取分组或文件对象

```
# 查找当前分组下名称或者路径匹配的文件或者分组对象
obj = helper.project.mainGroup.getChild(path)

# 第二个参数传入True可以对匹配进行递归，即可以匹配当前分组以及子分组中的所有内容
obj = helper.project.mainGroup.getChild(path, True)

# 根据层级描述来定位文件或者分组对象
obj = helper.project.mainGroup.find("/Demo/ViewController/HomeViewController.m")

# 通过层级描述来定位当前目录下（包括子目录）下匹配的文件或者分组对象
obj = helper.project.mainGroup.find("//ViewController/HomeViewController.m")
```

## 3.2 添加分组

```
# 在项目根目录下添加一个test的分组
helper.project.mainGroup.addGroup("test")

# 在Frameworks目录下添加一个test的分组
frameworksGroup = helper.project.mainGroup.find("/Frameworks")
frameworksGroup.addGroup("test")
```

# 3.3 移除分组

```
# 删除Frameworks目录下的test分组
frameworksGroup = helper.project.mainGroup.find("/Frameworks")
testGroup = helper.project.mainGroup.find("/Frameworks/test")
frameworksGroup.removeChild(testGroup)
```

# 3.4 添加Framework

```
frameworksGroup = helper.project.mainGroup.find("/Frameworks")

# 添加系统框架到第一个Target中
frameworksGroup.addSystemFramework("AVFoundation.framework", helper.project.targets[0])

# 添加自定义框架到第一个Target中
frameworksGroup.addFramework("/User/xxx/Lib/Utils.framework", helper.project.targets[0])

```

# 3.5 添加动态库

```
frameworksGroup = helper.project.mainGroup.find("/Frameworks")

# 添加系统动态库到第一个Target中
frameworksGroup.addSystemDylib("libz.tbd", helper.project.targets[0])

# 添加自定义动态库到第一个Target中
frameworksGroup.addDylib("/User/xxx/Lib/test.dylib", helper.project.targets[0])

```

# 3.6 添加静态库

```
frameworksGroup = helper.project.mainGroup.find("/Frameworks")

# 添加静态库到第一个Target中
frameworksGroup.addStaticLib("/User/xxx/Lib/test.a", helper.project.targets[0])

```

# 3.7 添加头文件

```
group = helper.project.mainGroup.find("/test/Headers")

# 添加一个头文件到项目
group.addHeaderFile("Test.h")

```

# 3.8 添加Bundle

```
group = helper.project.mainGroup.find("/test/Resources")

# 添加一个Bundle到项目的第一个Target
group.addBundle("Test.bundle", helper.project.targets[0])

```

# 3.9 添加本地化文件

```
group = helper.project.mainGroup.find("/test/Resources")

group.addLocalizedFile("Base.lproj/test.strings", "Base", parser.project.targets[0])
group.addLocalizedFile("en.lproj/test.strings", "en", parser.project.targets[0])
```

# 3.10 添加ShellScriptBuildPhase

```
# 给项目第一个target添加ShellScript
helper.project.targets[0].addShellScriptBuildPhase("echo \"Hello World\"");
```

# 3.11 保存变更内容

```
helper.save()
```

# 3.12 添加／删除语言区域

```
# 添加语言
helper.project.addRegion("zh-Hans")

# 删除语言
helper.project.removeRegion("zh-Hans")
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)