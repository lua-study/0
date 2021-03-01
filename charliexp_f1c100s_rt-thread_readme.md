## 我增加的
 1.增加了I2C驱动，并适配了GT911触摸驱动;
 2.将LittleVgl升级到6.1.1，并增加了触摸功能;
 3.增加了看门狗驱动，并在LittleVgl中喂狗
 
## 感谢www.whycan.cn的朋友，还有晕哥
    后续会继续移植更多驱动，大家有问题请使用Isues，有时间我会回复的，同时也建议一起玩的伙伴们将问题同步到whycan.cn
    从whycan上白嫖了很多资料，大家可以加QQ群：516836432 群里个个都是人材，说话又好听！
	如果大家也觉得F1C100S+（RTT+LittleVgl）这种少林功夫加唱哥跳舞很好玩的，也可以加我的群686338051

##关于本代码
   本人不属于高手，只是将XBOOT老大中的驱动移了过来。半桶水，这里算是抛砖引玉。

# 环境
---
## linux
---
## windows

使用msys2请使用国内源,使用Mingw64进入
```shell
pacman -S git make scons gcc make pkg-config ncurses-devel mingw-w64-x86_64-libusb mingw-w64-x86_64-zlib
```

# 编译器
---
## 百度网盘下载
[百度网盘链接](https://pan.baidu.com/s/16hCiVEnsWqkEROxbpzD-9Q)

.tar.bz2 是64位linux使用的

.7z 是64位windows使用的

解压后放在tools目录下面

---
# sunxi烧录工具
---
```shell
cd tools/sunxi-tools
make
```
---
# Rt-Thread所用的BOOT代码
---
## 编译
```shell
cd f1c100s_spl
scons
```
## 清理
```shell
cd f1c100s_spl
scons -c
```
---
# Rt-Thread

---

## 配置下载ENV工具
```shell
cd rt-thread
scons --menuconfig

注意使用此包中的LittleVgl与原始packages里的有冲突。需要删除
RTT的环境中的
env\packages\packages\system目录下的kconfig中的
source "$PKGS_DIR/packages/system/LittlevGL2RTT/Kconfig"
```

## 配置完成后刷新下载lvgl
```shell
cd rt-thread
soure ~/.env/env.sh
pkgs --update
```

## 编译
```shell
cd rt-thread
scons
```

## 清理
```shell
cd rt-thread
scons -c
```

## 测试
```shell
cd rt-thread
./script/[linux or windows]/dram_exec.sh
```
   测试增加USB模式不下载，直接USB运行.方便调试使用
`./script/[linux or windows]/run.sh

## 烧录到SPI-FLASH
```shell
cd rt-thread
./script/[linux or windows]/write_spiflash.sh
```

## 清除SPI-FLASH的SPL
```shell
cd rt-thread
./script/[linux or windows]/erase_spiflash.sh
```

---

## 感谢xboot作者

## 感谢rt-thread作者

## 感谢www.whycan.cn

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)