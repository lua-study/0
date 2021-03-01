# MQTT客户端
基于QT的MQTT客户端，编译需要先安装QtMQTT模块。

QtMQTT是Qt Automation的一部分，开源版本不提供二进制包，需要自己编译。
Windows下编译需要使用git-bash，编译过程需要调用perl解释器。

1. 下载源码
```bash
git clone git://code.qt.io/qt/qtmqtt.git
```

2. 编译

注意：下面命令中的Qt安装路径需要修改为自己电脑上的值。

  2.1 编译桌面版本
  
  执行`C:\Program Files\Git\git-bash.exe`
  ```bash
  export PATH=$PATH:/C/Qt/Tools/mingw730_64/bin
  cd qtmqtt
  git clean -dfx
  /c/Qt/5.12.4/mingw73_64/bin/qmake
  mingw32-make
  ```
  如果编译失败请检查g++版本，并调整PATH环境变量中的路径。

  2.2 交叉编译Android版本

  执行`C:\Program Files\Git\git-bash.exe`
  ```bash
  cd qtmqtt
  export ANDROID_NDK_ROOT=/d/qtandroid/android-ndk-r19c/ PATH=$PATH:/C/Qt/Tools/mingw730_64/bin
  git clean -dfx
  /c/Qt/5.12.4/android_arm64_v8a/bin/qmake
  mingw32-make
  ```

3. 安装
```bash
mingw32-make install
```

4. 生成API文档
```bash
mingw32-make docs
mingw32-make install_docs
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)