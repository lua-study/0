# 常用脚本
> ### 一键测试脚本bench.sh
使用方法：
```
wget -qO- bench.sh | bash
或者：
curl -Lso- bench.sh | bash
```

> ### 一键测试脚本（中国线路版）superbench.sh
使用方法：
```
wget -qO- https://gitee.com/511311/Script/raw/master/superbench.sh | bash
或者
curl -Lso- https://gitee.com/511311/Script/raw/master/superbench.sh | bash
```

> ### 多线路测速脚本（中国线路）superspeed.sh
使用方法：
```
wget https://gitee.com/511311/Script/raw/master/superspeed.sh
chmod +x superspeed.sh
./superspeed.sh
```

> ### Linux性能测试unixbench.sh
使用方法：
```
wget --no-check-certificate https://gitee.com/511311/Script/raw/master/unixbench.sh
chmod +x unixbench.sh
./unixbench.sh
```

> ### FTP 上传一键脚本ftp_upload.sh
 **1、下载该脚本并赋予执行权限** 
```
wget --no-check-certificate https://gitee.com/511311/Script/raw/master/ftp_upload.sh
chmod +x ftp_upload.sh
```
 **2、修改并配置脚本** 
关于变量名的一些说明：

LOCALDIR （脚本当前所在目录）

LOGFILE （脚本运行产生的日志文件路径）

FTP_HOST （连接的 FTP 域名或 IP 地址）

FTP_USER （连接的 FTP 的用户名）

FTP_PASS （连接的 FTP 的用户的密码）

FTP_DIR （连接的 FTP 的远程目录，比如： public_html）

 **3、脚本运行示例**

1）上传当前目录下的文件 filename.tgz

```
./ftp_upload.sh filename.tgz
```

2）上传当前目录下的多个文件 filename1.tgz，filename2.tgz，filename3.tgz

```
./ftp_upload.sh filename1.tgz filename2.tgz filename3.tgz
```

3）上传当前目录下的通配符文件 *.tgz（注意此时后面跟的参数要加双引号）

```
./ftp_upload.sh "*.tgz"
```

4）上传当前目录下的多个通配符文件 *.tgz，*.gz（注意此时后面跟的参数要加双引号）

```
./ftp_upload.sh "*.tgz" "*.gz"
```

> ### 一键安装最新内核并开启 BBR

本脚本适用环境

系统支持：CentOS 6+，Debian 7+，Ubuntu 12+

虚拟技术：OpenVZ 以外的，比如 KVM、Xen、VMware 等

内存要求：≥128M

使用方法：
```
wget --no-check-certificate https://gitee.com/511311/Script/raw/master/bbr.sh
chmod +x bbr.sh
./bbr.sh
```


安装完成后，脚本会提示需要重启 VPS，输入 y 并回车后重启。

重启完成后，进入 VPS，验证一下是否成功安装最新内核并开启 TCP BBR，输入以下命令：

```
uname -r
```

查看内核版本，含有 4.12 就表示 OK 了
```
sysctl net.ipv4.tcp_available_congestion_control
```
返回值一般为：

net.ipv4.tcp_available_congestion_control = bbr cubic reno

```
sysctl net.ipv4.tcp_congestion_control
```
返回值一般为：

net.ipv4.tcp_congestion_control = bbr

```
sysctl net.core.default_qdisc
```
返回值一般为：

net.core.default_qdisc = fq

```
lsmod | grep bbr
```
返回值有 tcp_bbr 模块即说明bbr已启动。



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)