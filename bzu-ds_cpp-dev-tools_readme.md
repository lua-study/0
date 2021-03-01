# Windows 下用 MinGW64、Clang、Git 和 VS Code 搭建 C++ 开发环境

庄波   于 2018/8/25

MinGW-w64 于 2007 年分支于原 mingw.org，支持 32 位和 64 位编程。Clang 是一个优秀的 C/C++/Object C 编译器前端，编译快速、占用内存少，有诊断功能且兼容 GCC。Git 是目前最先进的分布式版本管理系统，快速灵活，可离线工作。VS Code 是 Microsoft 开发的跨平台的代码编辑器，轻量、快速、灵活、强大，还拥有丰富的插件生态系统。下面介绍如何在 Windows 下（以 Win7-64bit 为例）利用上述工具搭建 C++ 开发环境。

## 1. 软件准备

- MinGW-w64（编译器）
  - [下载地址](https://sourceforge.net/projects/mingw-w64/files/)  
  - 在最新版中选择 `x86_64-win32-seh`
- Clang（编译器前端）
  - [下载地址](http://releases.llvm.org/download.html)  
  - 在最新版本中选择 Windows (64-bit) 预编译版，即 `Pre-Built Binaries` 中的 `Windows (64-bit)`。
- Git （版本管理）
  - [下载地址](https://git-scm.com/downloads)  
- VS Code（编辑器）
  - [下载地址](https://code.visualstudio.com/)  

## 2. 软件安装

### 2.1 安装 MinGW-w64

1. 解压缩到 `C:\mingw64`。如下：

![](images/mingw64-folder.png)

2. 设置环境变量，添加到系统路径。查看计算机属性，选择【高级系统设置】，【环境变量】，添加用户变量 `MINGW = C:\mingw64`，并在 `Path` 变量中添加路径 `%MINGW%\bin`。注意不要修改 `Path` 变量中已有的内容，多个路径用英文分号 `;` 隔开。

![](images/mingw64-env-var.png)

3. 验证安装成功。单击【开始】，输入`cmd` 并回车，打开命令窗口。输入命令 `gcc -v`，安装成功会显示 GCC 版本信息。

![](images/gcc-v.png)

### 2.2 安装 Clang

1. 运行 LLVM 安装程序（所有选项默认）。最后可能提示未找到 MSBuild toolsets 目录，这里直接忽略，并完成安装。
2. 设置环境变量，添加到系统路径。打开【环境变量】，添加用户变量 `LLVM = C:\Program Files\LLVM`，并在 `Path` 变量中添加路径 `%LLVM%\bin`。注意：多个路径之间用英文分号 `;` 分隔。

![](images/llvm-env-var.png)

3. 验证安装成功。打开新的命令窗口，输入命令 `clang -v` 应看到 Clang 版本信息。

![](images/clang-v.png)

### 2.3 安装 Git

1. 运行 Git 安装程序（所有选项默认）。
2. 验证安装成功。打开新的命令窗口，输入 `git` 应看到 Git 使用帮助。

![](images/git.png)

### 2.4 安装 Code

1. 运行 VS Code 安装程序（所有选项默认）。
2. 忽略中文语言包。初次运行，提示安装中文语言包，建议不安装（英文界面更简洁）。单击小齿轮图标，选择 `Don't Show Again` （不再提示）。

![](images/no-zhcn.png)

3. 安装 Code 扩展（插件）。打开 Code，点击左侧【Extentions】图标，搜索并安装下列插件，以方便 C++ 开发：
   - (1) **C/C++ for Visual Studio Code** -- 提供代码提示、格式化等功能。
   - (2) **C/C++ Clang Command Adapter** -- 利用 Clang 实现编译和诊断功能。
   - (3) **Code Runner** -- 方便运行程序。
   - (4) **GitLens** -- 便于使用 Git 进行版本管理。

> 提示：各插件安装在用户目录下 `C:\Users\username\.vscode\extensions` 目录中，可直接复制 `.vscode` 目录实现快速安装。

安装成功后，打开 Code，选择 Extensions 可以看到已安装的插件。

![](images/code-packages.png)

4. 插件设置。打开 Code，单击左下角小齿轮图标，选择 【Settings】，进入用户设置界面，在【User Settings】中作如下设置：

```json
{
    "terminal.integrated.rendererType": "dom",
    "C_Cpp.clang_format_path": "${env:LLVM}/bin/clang-format",
    "C_Cpp.default.compilerPath": "${env:LLVM}/bin/clang --target=x86_64-w64-mingw32",
    "C_Cpp.errorSquiggles": "Disabled",
    "clang.cflags": ["--target=x86_64-w64-mingw32", "-std=c11"],
    "clang.cxxflags": ["--target=x86_64-w64-mingw32", "-std=c++17"],
    "clang.completion.enable": false,
    "code-runner.runInTerminal": true,
    "code-runner.saveFileBeforeRun": true,
    "code-runner.preserveFocus": false,
    "code-runner.executorMap": {
        "c": "cd $dir && clang --target=x86_64-w64-mingw32 -std=c11 -O2 $fileName -o $fileNameWithoutExt.exe && $dir$fileNameWithoutExt.exe",
        "cpp": "cd $dir && clang++ --target=x86_64-w64-mingw32 -std=c++17 -O2 $fileName -o $fileNameWithoutExt.exe && $dir$fileNameWithoutExt.exe"
    },
}
```

> 上述设置的作用如下：
>
> - `C_Cpp.clang_format_path` 设置 clang-format 路径，以便实现代码格式化功能。
> - `C_Cpp.default.compilerPath` 这里设置 Clang 作为编译器，用 `target` 参数指定 MinGW64 作为编译器后端。
> - `C_Cpp.errorSquiggles` 禁用插件 (1) 错误提示，换用插件 (2) 的诊断功能（更好）。
> - `clang.cflags` 和 `clang.cxxflags` 为插件 (2) 设置编译参数。
> - `clang.completion.enable` 禁用插件 (2) 代码补全（较慢），而利用插件 (1) 实现。
> - `code-runner` 相关设置令程序在命令窗口中执行，执行前保存文件，保持焦点便于交互，最后 `code-runner.executorMap` 指定用 Clang 作为编译器。

> VS Code 的用户设置保存在文件 `~\AppData\Roaming\Code\User\settings.json` 中（`~` 表示用户目录），可直接复制、修改。

5. 自定义代码片段。单击左下角小齿轮图标，选择【User Snippets】，然后选择 【cpp (C++)】，可在 `cpp.json` 中自定义代码片段，如：

```json
{
	"New C++ program": {
		"prefix": "newcpp",
		"body": [
			"#include  ",
			"",
			"int main()",
			"{",
			"    std::cout   常用代码片段保存在`~\AppData\Roaming\Code\User\snippets` 目录中（`~` 表示用户目录），可直接复制、修改。

6. 验证 VS Code 安装正确。关闭后重新打开 VS Code，新建文件，保存为 `hello.cpp`，输入 `newcpp`（如上自定义代码片段），应当看到代码片段提示，选择后建立一个新程序。点击编辑器右上角三角形按钮，编译、执行程序，应该看到命令窗口中显示执行结果 `Hello`。至此安装成功。Enjoy it!

![](images/newcpp.png)


![](images/cpp-run.png)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)