# x-msg-im-xsc-examples-cpp
c++ examples for libx-msg-im-xsc


* 这里提供了一些例子程序, 用于演示[libx-msg-im-xsc](https://github.com/dev5cn/libx-msg-im-xsc)的用法. 

    * 一个同时支持`tcp`, `http`, `websocket`多协议接入的并发服务器.



* 编译前准备

    * gcc 9.2.1 or later, 其实可以不用这么新. 支持c++14即可, 只是CMakeList.txt中使用了`c++17`.

    * cmake 3.x or later.

    * protobuf-3.5.1

    * on fedora 31: `dnf install libuuid-devel`, on ubuntu:  `apt-get install libuuid-devel`

    * git clone https://github.com/dev5cn/libmisc-cpp

    * git clone https://github.com/dev5cn/libxsc-cpp
        
    * git clone https://github.com/dev5cn/libxsc-proto-cpp

    * git clone https://github.com/dev5cn/libx-msg-im-xsc

    * git clone https://github.com/dev5cn/x-msg-im-xsc-examples-cpp

    * 全部`git clone`后, 得到一个这样的目录结构:

    ```js
    libmisc-cpp  libx-msg-im-xsc  libxsc-cpp  libxsc-proto-cpp  x-msg-im-xsc-examples-cpp
    ```

     * 环境变量

    ```js
    export PLAT=LINUX
    export PROTOBUF=/home/dev5/tools/protobuf-3.5.1
    export CXX_FLAGS="-g3 -O0"
    export MAKE_J="-j3"
    ```

* 编译

    * `chmod 775 */*.sh`

    * 依次进入`libmisc-cpp`, `libxsc-cpp`, `libxsc-proto-cpp`, `libx-msg-im-xsc`, `x-msg-im-xsc-examples-cpp`, 在每个目录下运行`./build.sh`

    * 最后将得到一个可执行程序, 直接启动即可.
    ```js
    [xxx@dev5 x-msg-im-xsc-examples-cpp]$ ldd x-msg-im-xsc-exapmples-cpp 
	linux-vdso.so.1 (0x00007ffde39ad000)
	libuuid.so.1 => /lib64/libuuid.so.1 (0x00007f8f27661000)
	libpthread.so.0 => /lib64/libpthread.so.0 (0x00007f8f27640000)
	libstdc++.so.6 => /lib64/libstdc++.so.6 (0x00007f8f27446000)
	libm.so.6 => /lib64/libm.so.6 (0x00007f8f27300000)
	libgcc_s.so.1 => /lib64/libgcc_s.so.1 (0x00007f8f272e6000)
	libc.so.6 => /lib64/libc.so.6 (0x00007f8f2711e000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f8f27687000)
    [xxx@dev5 x-msg-im-xsc-examples-cpp]$
    ```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)