## WRT_package项目介绍
此工程的APP跑在以Raspberry Pi为硬件平台、OpenWrt为软件平台的设备上，作为学习LuCI开发的代码托管分支，当然代码是可以移植到其他所有OpenWrt系统上的

## Raspberry Pi跑OpenWrt
参考[Raspberry Pi烧写Openwrt固件](http://jphome.github.io/blog/2014/08/01/raspberry_pi_openwrt.html)

## APPs
* helloworld [详细介绍](http://jphome.github.io/blog/2014/03/29/openwrt_sdk.html)
* luci-app-njitclient-master [详细介绍](http://jphome.github.io/blog/2014/08/03/luci_add_page.html)

## 编译
 
cd sdk_brcm63xx
ln -s xxx/WRT_package ./package
make clean
make menuconfig
make V=99
tree bin
bin
├── brcm63xx
│   └── packages
│       ├── helloworld_1.0-1_brcm63xx.ipk
│       ├── luci-app-njitclient_1.0-1_all.ipk
│       ├── Packages
│       └── Packages.gz
└── packages
 



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)