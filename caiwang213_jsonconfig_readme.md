## CMake (Windows)

Install CMake:  

MSVC Win32 Debug

     $ md build && cd build
     $ cmake -DCMAKE_INSTALL_PREFIX=./install -DCMAKE_DEBUG_POSTFIX="d" -G "Visual Studio 12" .. 
     $ msbuild INSTALL.vcxproj /t:Build /p:Configuration=Debug

MSVC Win64 Release 

     $ md build && cd build
     $ cmake -DCMAKE_INSTALL_PREFIX=./install -G "Visual Studio 12 Win64" .. 
     $ msbuild INSTALL.vcxproj /t:Build /p:Configuration=Release

## CMake (Unix)

     $ mkdir build && cd build
     $ cmake -DCMAKE_INSTALL_PREFIX=$PWD/install -DCMAKE_BUILD_TYPE=Debug -DCMAKE_DEBUG_POSTFIX="d"  -DCMAKE_PREFIX_PATH=/opt/Qt5.9.3.shared.set2 ..     # Default to Unix Makefiles.
     $ make
     $ make install

## CMake (Android)

     $ mkdir build && cd build
     $ cmake  -DCMAKE_INSTALL_PREFIX=$PWD/install -DCMAKE_BUILD_TYPE=Debug -DCMAKE_DEBUG_POSTFIX="d" -DCMAKE_TOOLCHAIN_FILE=cmake/android.toolchain.cmake -G "Unix Makefiles" ..
     $ make
     $ make install



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)