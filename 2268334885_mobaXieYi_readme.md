#protobufferUnity

1:src 目录是 protobuffer csharp port 修改后的代码， 用于ios 上面使用
2:Google.ProtocolBuffersLite.dll 是编译的ios 上可用的 dll
3:build.bat  是编译生成 协议dll 的脚本
4:cs 目录下面是 根据protos 目录 中协议 生成的cs 协议代码
    cs 目录的 AssemblyInfo.cs
    UpdateSln.py
    protoDll.csproj
    new.csproj
    是一个 cs 工程，执行 UpdateSln.py 之后 编译 new.csproj 可以生成协议的dll 文件， 需要mono 环境的支持，只在 mac上面测试过

5:windows 使用 protoc_win.exe mac使用brew install 安装的官方 protoc  pb 2.5.0版本


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)