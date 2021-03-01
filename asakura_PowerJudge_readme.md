#PowerJudge#
Judge Core for PowerOJ on Linux platform.

Based on UESTC and HUST judge core.

##Features##
auto get data files from data directory and sort by lexicographical.

set process limit for compiler, executor and spj.

chroot and setgid/setuid with nobody account for secuirty.

fast judge for Python which doesn't use chroot or copy rutime env.

support Linux 32 bit and 64 bit.
  * Ubuntu 12.10 Desktop 32bit
  * Ubuntu 12.04 Desktop 64bit
  * Ubuntu 14.04 Server 32bit
  * Linux Mint 14 32bit
  * Linux Mint 14 64bit
  * Debian 7.5 32bit
  * Debian 7.1 64bit

  * Redhat 5.5  **NOT** support
  * CentOS 4.8  **NOT** support

##Download##
    git clone http://git.oschina.net/power/PowerJudge.git


##Compilers##
    sudo apt-get install fpc openjdk-7-jdk python2.7 gcc g++

    sudo yum install glibc-devel glibc-static gcc gcc-c++ java-1.7.0-openjdk java-1.7.0-openjdk-devel gpm
    sudo rpm -ivh fpc-2.6.0-5.1.i686.rpm

not support Eclipse Java Compiler or gcj-jdk.


##Build##
    make

or
    make -e FAST_JUDGE=true
    
    make -e LOG_LEVEL=LOG_NOTICE


##Test##
    make test


##Install##
    make install


##Usage##
    /usr/local/bin/powerjudge -s 10000 -p 1000 -t 1000 -m 65536 -l 2 -D ./data -d ./temp

* **-s**    solution id
* **-p**    problem id
* **-t**    time limit   (optional, default 1000 ms)
* **-m**    memory limit (optional, default 65536 KB)
* **-l**    language id
  1. 1 -- C
  2. 2 -- CPP
  3. 3 -- Pascal
  4. 4 -- Java
  5. 5 -- Python
* **-D**    root data directory, e.g. ~/oj/data/
* **-d**    root work directory, e.g. ~/oj/temp/

简要流程：

  1.初始化

  2.解析参数

   2.1 检查参数完整性

   2.2 获取数据目录和工作目录

   2.3 检查源代码文件

   2.4 设置程序语言时空限制

  3.检查有效用户

  4.改变当前目录

  5.设置judge时钟

  6.注册超时信号处理程序

  7.编译

   7.1 设置编译限制

   7.2 重定向编译程序输入输出

   7.3 调用外部编译器

   7.3 获取外部编译器返回状态，处理信号

  8.运行评测

   8.1 扫描数据目录，获取数据文件

   8.2 对于每组数据评测

   8.2.1 重定向输入输出

   8.2.2 设置安全限制

   8.2.3 设置资源限制

   8.2.4 设置超时时钟

   8.2.5 监控系统调用

   8.2.6 调用用户程序

   8.2.7 主进程初始化系统调用表

   8.2.8 主进程检查子进程运行状态

         1. 检查信号

         2. 检查内存

         3. 检查系统调用

   8.2.9 子进程正常退出检查结果

         a. 调用spj程序或者

         b. 比较输出文件

   8.2.10 更新评测中间状态

  9.清理工作目录

  10.输出评测结果
  


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)