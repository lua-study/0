
# 编程练习 ![许可证书](https://img.shields.io/badge/license-BSD%203--Clause-blue)

---

## 使用VSCode + cmake + vcpkg开发C/C++编程练习项目

> 作者：optimouskiller

* 开始时间：2017年7月17日
* 开发环境：VSCode（插件：CMake、CMake Tools、Test Explorer、C/C++ tools、Catch2, Google Test and DOCtest Explorer）
* 开发语言：C/C++（包管理器：vcpkg；测试框架：googletest）
* 文件编码：UTF-8

### 一、使用步骤

1. 安装VSCode、vcpkg以及cmake，并通过`vcpkg install sqlite3`来安装sqlite3包，用于项目包导入测试。实际上vcpkg会自动下载cmake工具到vcpkg\downloads\tools路径下，此时直接将cmake.exe添加到环境变量即可。当然，单独安装cmake也是可以的，但是前提是必须将cmake.exe添加到环境变量之中，若不想将cmake.exe添加到环境变量之中的话，需要在第三步中安装VSCode CMake插件后在该插件的设置中指定cmake.exe的路径；
2. 安装Visual Studio Comunity 2019，安装时需选中MSVC编译器组件以及C/C++开发组件，cmake将会使用里面的编译器等组件，当然也可以安装MinGW或者其他编译器；
3. vscode安装如下插件:
   * C/C++：开发必备；
   * CMake：cmake构建，可以智能发现VisualStudio里面的构建工具，若未安装Visual Studio，需要在此插件的设置里面指定构建工具；
   * CMake Tools：给CMakeLists.txt增加颜色以及代码提示；
   * Catch2, Google Test and DOCtest Explorer：方便运行gtest；
   * Test Explorer UI:此插件依赖于上一个插件，用于管理测试用例；
4. 修改`.vscode/settings.json`里面的`CMAKE_TOOLCHAIN_FILE`的值为实际安装的`vcpkg.cmake`文件路径；
5. 使用VSCode打开此模板文件夹，VSCode会自动根据`CMakeLists.txt`初始化工程；
6. 开始编写代码。

### 二、目录结构说明

```txt
├─.vscode   vscode配置文件夹
├─build     cmake构建目录，里面的内容由cmake自动生成
├─src       源代码文件夹
│  └─utils  工具类文件夹
└─test      测试用例文件夹
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)