 
   
     
     

   xmake 

   
     
       
     
     
       
     
     
       
     
     
       
     
   
   
     
       
     
     
       
     
     
       
     
     
       
     
     
       
     
     
       
     
   

   A cross-platform build utility based on Lua 
 

## Introduction ([中文](/README_zh.md))

xmake is a cross-platform build utility based on lua. 

The project focuses on making development and building easier and provides many features (e.g package, install, plugin, macro, action, option, task ...), 
so that any developer can quickly pick it up and enjoy a productivity boost when developing and building projects.

 

If you want to know more, please refer to:

* [Documents](https://xmake.io/#/home)
* [HomePage](https://xmake.io)
* [Github](https://github.com/xmake-io/xmake)
* [Gitee](https://gitee.com/tboox/xmake)

## Installation

#### via curl

```bash
bash  

## Package dependences

 

An official xmake package repository: [xmake-repo](https://github.com/xmake-io/xmake-repo)

## Build project

```bash
$ xmake
```

## Run target

```bash
$ xmake run console
```

## Debug target

```bash
$ xmake run -d console
```

## Configure platform

```bash
$ xmake f -p [windows|linux|macosx|android|iphoneos ..] -a [x86|arm64 ..] -m [debug|release]
$ xmake
```

## Menu configuration

```bash
$ xmake f --menu
```

 

## Package management

### Download and build

 

### Processing architecture

 

## Supported platforms

* Windows (x86, x64)
* macOS (i386, x86_64)
* Linux (i386, x86_64, cross-toolchains ...)
* Android (armv5te, armv6, armv7-a, armv8-a, arm64-v8a)
* iOS (armv7, armv7s, arm64, i386, x86_64)
* WatchOS (armv7k, i386)
* MinGW (i386, x86_64)

## Supported Languages

* C
* C++
* Objective-C and Objective-C++
* Swift
* Assembly
* Golang
* Rust
* Dlang
* Cuda

## Supported Projects

* Static Library
* Shared Library
* Console
* Cuda Program
* Qt Application
* WDK Driver (umdf/kmdf/wdm)
* WinSDK Application
* MFC Application

## Builtin Plugins

#### Generate IDE project file plugin（makefile, vs2002 - vs2019 .. ）

```bash
$ xmake project -k vs2017 -m "debug,release"
$ xmake project -k cmakelists
$ xmake project -k compile_commands
```

#### Macros script plugin

```bash
$ xmake m -b                        # start to record
$ xmake f -p iphoneos -m debug
$ xmake
$ xmake f -p android --ndk=~/files/android-ndk-r16b
$ xmake
$ xmake m -e                        # stop to record
$ xmake m .                         # playback commands
```

#### Run the custom lua script plugin

```bash
$ xmake l ./test.lua
$ xmake l -c "print('hello xmake!')"
$ xmake l lib.detect.find_tool gcc
```

#### Generate doxygen document plugin

```bash
$ xmake doxygen [srcdir]
```

## More Plugins

Please download and install from the plugins repository [xmake-plugins](https://github.com/xmake-io/xmake-plugins).

## IDE/Editor Integration

* [xmake-vscode](https://github.com/xmake-io/xmake-vscode)

 

* [xmake-sublime](https://github.com/xmake-io/xmake-sublime)

 

* [xmake-idea](https://github.com/xmake-io/xmake-idea)

 

* [xmake.vim](https://github.com/luzhlon/xmake.vim) (third-party, thanks [@luzhlon](https://github.com/luzhlon))

## More Examples

Debug and release modes:

```lua
add_rules("mode.debug", "mode.release")

target("console")
    set_kind("binary")
    add_files("src/*.c") 
    if is_mode("debug") then
        add_defines("DEBUG")
    end
```

Download and use packages in [xmake-repo](https://github.com/xmake-io/xmake-repo):

```lua
add_requires("libuv master", "ffmpeg", "zlib 1.20.*")
add_requires("tbox >1.6.1", {optional = true, debug = true})
target("test")
    set_kind("shared")
    add_files("src/*.c")
    add_packages("libuv", "ffmpeg", "tbox", "zlib")
```

Download and use packages in third-party package manager:

```lua
add_requires("brew::pcre2/libpcre2-8", {alias = "pcre2"})
add_requires("conan::OpenSSL/1.0.2n@conan/stable", {alias = "openssl"}) 
target("test")
    set_kind("shared")
    add_files("src/*.c")
    add_packages("pcre2", "openssl")
```

Find and use local packages:

```lua
target("test")
    set_kind("shared")
    add_files("src/*.c")
    on_load(function (target)
        target:add(find_packages("zlib", "openssl", "brew::pcre2/libpcre2-8", "conan::OpenSSL/1.0.2n@conan/stable"))
    end)
```

## Project Examples

Some projects using xmake:

* [tbox](https://github.com/tboox/tbox)
* [gbox](https://github.com/tboox/gbox)
* [vm86](https://github.com/tboox/vm86)
* [more](https://github.com/xmake-io/awesome-xmake)

## Example Video

 
 
 

## Contacts

* Email：[waruqi@gmail.com](mailto:waruqi@gmail.com)
* Homepage：[tboox.org](https://tboox.org)
* Community：[/r/tboox on reddit](https://www.reddit.com/r/tboox/)
* ChatRoom：[Char on telegram](https://t.me/tbooxorg), [Chat on gitter](https://gitter.im/tboox/tboox?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
* Source Code：[Github](https://github.com/xmake-io/xmake), [Gitee](https://gitee.com/tboox/xmake)
* QQ Group: 343118190(full), 662147501
* Wechat Public: tboox-os

## Thanks

This project exists thanks to all the people who have [contributed](CONTRIBUTING.md):
   

* [TitanSnow](https://github.com/TitanSnow): provide the xmake [logo](https://github.com/TitanSnow/ts-xmake-logo) and install scripts
* [uael](https://github.com/uael): provide the semantic versioning library [sv](https://github.com/uael/sv)
* [OpportunityLiu](https://github.com/OpportunityLiu): improve cuda, tests and ci

## Backers

Thank you to all our backers! 🙏 [[Become a backer](https://opencollective.com/xmake#backer)]

   

## Sponsors

Support this project by becoming a sponsor. Your logo will show up here with a link to your website. [[Become a sponsor](https://opencollective.com/xmake#sponsor)]

   
   
   
   
   
   
   
   
   
   




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)