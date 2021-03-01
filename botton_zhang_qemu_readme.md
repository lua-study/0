
# Qemu Loongson

This is a customized qemu verion for loongson processors based v2.12.92. Currently it supports these loongson boards:

* fulong2e             Fulong 2e mini pc
* ls1a                 mips ls1a platform
* ls1b                 mips ls1b platform
* ls1c                 mips ls1c platform
* ls232                mips ls232 platform
* ls2f1a               mips ls2f1a platform
* ls2h                 mips ls2h platform
* ls2k                 mips ls2k platform
* ls3a                 mips ls3a platform
* ls3a2h               mips ls3a2h platform (still have some issues left)
* ls3a7a               mips ls3a7a platform

## compile and run

The same with official qemu releases. Please refer to official documents to install necessary dependent packages. One example session:

    cd  /
    mkdir ./build
    cd ./build
    ../configure --target-list=mipsel-softmmu,mips64el-softmmu --disable-werror
    make

    BOOTROM=0x110000000 SIMPLEVGA=800x600-16:0x0e800000 ./qemu-system-mips64el -M ls2k -bios ./gzrom.bin -kernel ./vmlinuz  -serial stdio -m 4096 -s -monitor tcp::1235,server,nowait -netdev user,id=n1,net=10.20.41.0/24,host=10.20.41.50,tftp=/srv/tftp/  -device pci-synopgmac,netdev=n1 -usb -smp 1 

## TODO

Previously it is mainly written for internal usages so there are not enough documents yet. Information for related boards/pmons/kernels will be provided later.







 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)