# wrtoy(wrtoy构建玩具)

最后更新2015.04.28
####
增加hard_manage.sh配置的project_name属性.
补丁工具功能优化

####
安装使用问题加群290045468,可以在线解答

#### 写在前面的话(2015.0228)
非常郁闷，因为联想笔记本电脑linux驱动的问题，这个Readme写了5次，每次写了两三百字就死机，也不保存写过的信息。
实在没有心情更新帮助了。

因为原有的构建脚本被废弃了，这里简单说说使用方法


## 安装openwrt编译环境

先安装ubuntu-utils shell工具集
```bash
mkdir -p /works/utils
cd /works/utils
git clone https://git.oschina.net/darcyg/ubuntu-utils.git 
cd ubuntu-utils/ubuntu_install_script
./install_base_lib.sh
./install_cppide.sh
./install_utils.sh
cd ../vpnssh_proxy
./install_proxy.sh
cd ../ubuntu_install_script
./install_env.sh
```

以上操作，将安装大量的编译工具，都是linux下openwrt或其他开发不可或却的库与工具
即便最小编译固件用不到相关库，也会某些特定功能开发而用到．

建议安装install_proxy.sh，将安装基于sock5的代理服务．其中需要用户自己申请一下ssh或shadowsocks代理帐号,并修改相关配置代码（在vpnssh_proxy/bin目录的shadowsocks用config.json和vpn.sh中）

安装proxy非常关键，部分库通过代理才能下载．
配置好以后．通过vpn.sh或svpn.sh开启代理服务
使用proxychains [cmd]来保证，下载通过代理服务器进行．

有兴趣的人，可以安装一下install_git.sh，主要提供
＊git的短命令（具体看源码）
＊配置自动登录git服务器的~/.netrc，这个对在私有git上部署的库的下载访问很有用

```bash
mkdir -p /works/openwrt
cd /works/openwrt
git clone http://git.oschina.net/darcyg/wrtoy
cd wrtoy
```

-------------------------------
安装所有编译openwrt所需各种程序库执行脚本后会有提示。如果需要编译全部packages的库，请选`y`代表安装全部工具和依赖程序库，否则选`n`只安装一般必备工具和程序库。

```bash
./install_openwrt_hostlib.sh
```

*** 桌面版本建议手工安装Beyond Compare 3.x For Linux的源码比较工具 ***

开启中文信息模式

```bash
echo 1 > .zh_cn
./build -h
```

同步openwrt源码到本地,建立工作目录树

```bash
./build -I
```

打mtall开发板的目标平台补丁到openwrt

```bash
./build -pp mtall
```

打mtall项目的应用补丁到openwrt

```bash
./build -po mtall
```

升级openwrt，仓库feed包

```bash
./build -f
```

执行make menuconfig

```bash
./build -m
```

开启tftp服务，并编译固件，拷贝固件到tftp目录

```bash
./build --tftp
./build -bj 8 -c
```

本项目构建四个基本程序

- build
    
    构建常用操作

- openwrt_synchro

    从源同步数据到本地（build会自动处理）

- hardware_manage

    硬件方案的配置工具
   
- publish

    固件提交到统一服务器(通过scp传数据)

--------------------------------

安装完之后，openwrt默认工作路径为:

`/works/openwrt`

#### 工作目录结构
    + /works/openwrt
        + dl                # packages 中各种编译用源码包下载路径
        + staging_dir       # 软链到openwrt目录下的staging_dir，减少更新主项目时重新build工具链的时间 
        + build_dir         # 软链到openwrt目录下的build_dir，减少更新主项目时重新build工具链的时间
        + nfs               # nfs目录配置 直接软链openwrt软链目录下的bin/ramips目录中的文件
        + tftproot          # tftp目录配置 直接软链openwrt软链目录下的bin/ramips目录中的文件
        + openwrt.git       # openwrt的官方git代码，不再此版本下工作
        + works             # openwrt导出的不同分支版本的源码目录
            + 2014-06-25_cb592a3        
                            # 2014-06-25的 分支版本 （工作目录）
            + 2014-06-25_cb592a3.orig   
                            # 2014-06-25的 分支版本 （用于生成patch的目录）
        + openwrt           # 当前openwrt工作目录，此为一个软link，如直接指到works/2014-06-25_cb592a3目录下的分支路径
        + thirdparty_libs   # 第三方编译库，解决某些HOST编译时，系统缺乏相关依赖库的问题
        . lastgit           # 最后的git提交版本
        . usegit            # 当前使用git提交版本（openwrt的软link）
        + openwrt-script    # 本脚本工具库
        
-------------------------------

# 以下说明废弃掉

## openwrt-script 脚本库功能

### 配置更新

    - 增加rt5350库新设备配置更新(2014.07.08)
    - 增加lan/wan共口的配置更新(2014.07.08)

### install_openwrt.sh 
本脚本用于新安装环境和更新已有环境中openwrt源码到最新版本
更新openwrt.git，也更新其他第三方feeds/packages
最新版本，不造成编译链工具重新制作

### update_openwrt.sh 
本脚本仅更新已有环境中openwrt源码中的feeds中的包到最新版本
不更新openwrt.git，只更新其他第三方feeds/packages
最新版本，不造成编译链工具重新制作

### patch_openwrt.py
应用在projs目录下的所有相关补丁到/works/openwrt/openwrt的当前工作用的源码中

base和common目录中是每次补丁都会操作

proj_*的目录，在patch_openwrt.py是指定项目名，会选择应用
```
./patch_openwrt.py proj -p 5350 -w
```
上述例子中`5350`即项目名称，脚本会自动应用projs/proj_5350中的补丁

#### 帮助
```
./patch_openwrt.py -h
```

#### 应用补丁(虚拟)
```
./patch_openwrt.py proj -p 5350 
```

#### 应用补丁(写入补丁,同时删除测试补丁产生的文件*.fix)
```
./patch_openwrt.py proj -p 5350 -w
```

#### 补丁测试生成(写入*.fix测试补丁，不会修改原文件，用来测试补丁脚本)
```
./patch_openwrt.py proj -p 5350 -f
```

#### 补丁的格式
补丁采用yaml格式（类json）
    * 最新支持单YAML文件，多条配置补丁
    * 字符替换std和正则替换模式regex，orig字段支持单或多条规则

具体参考projs/base中的示例

这里仅对单条补丁中的模式表示说明：mode

    - std       # 或不填mode项目，为标准字符串替换（允许多条规则，仅替换第一条匹配成功）
    - std+      # 或不填mode项目，为标准字符串替换（允许多条规则，全部匹配替换）
    - regex     # 匹配多条正则规则的一条，匹配正确进行替换（仅替换第一条匹配成功）
    - regex+    # 匹配多条正则规则，匹配正确进行替换（全部匹配替换）
    - add       # 在文件最后或某行后面增加一行，不会重复添加
    - debug     # 打印详细一点的信息
    - source    # 显示源字串和替换字串
    - copy      # 拷贝文件
    - del       # 删除文件
    - skip      # 跳过这一项    
    
## build.sh

辅助编译命令行工具，直接对/works/openwrt/openwrt目录下进行操作，减少目录切换的必要

### 命令格式
```
./build.sh [f/m/b/d/j/j2/j4/j8/c/set/down/down+/clear/clear_tmp]
```
    - f feeds 更新feeds
    - m menuconfig 从菜单选择配置
    - b build 编译固件
    - d debug 显示详细编译信息
    - j[j2/j4/j8] 编译中多线程的使用
    - c copy 将目标目录生成的文件拷贝到tftpboot目录，并建立软链便于下载
    - set 设置开发板信息（用于-c参数文件拷贝）
    - down[down+] 下载源码或通过代理下载
    - clear 清除工作目录中的文件
    - clear_tmp 清除tmp目录下的临时文件
    
### 设置开发板信息(用于c复制参数)
```
./build.sh set
```
输入boardname(板名),platform(方案),chipname(芯片名),tftplink(tftp软链)4个参数
### 升级feeds，并启动menuconfig，配置好以后编译(详细显示d,j参数),并更新到tftpboot目录中的5350软链
```
./build.sh f m b d j c
```
## 工作目录结构
    + /works/openwrt/openwrt-script
        + common                        # 共享脚本程序库
        + extra                         # 第三方packages库（手工安装）此目录被禁止提交
        + projs                         # 项目本地patch库
            + base                      # openwrt基本补丁
                . 001-open-wireless.yaml 
                                        # 打开无线补丁
                . 002-set-chinese.yaml  # 中文语言配置用补丁(特别注意)
            + common                    # openwrt共享补丁
            + demo                      # 补丁功能测试用例
            + proj_5350                 # 5350通用补丁
            + proj_7620n                # 7620n通用补丁
            + proj_7620a                # 7620a通用补丁            
            + proj_7620a                # 7620a通用补丁            
            + proj_mediastation         # 媒体基站项目用补丁
            + proj_smarthomegate        # 智能家居项目用补丁
        + tools                         # 额外工具脚本目录
        + utils                         # python程序库
        . extra.sh                      # 未来用来刷新第三方package库的脚本，暂空
        . install_openwrt.sh            # 安装或切换最新分支源码到openwrk软链的工具
        . install_openwrt_hostlib.sh    # HOST编译源码所需依赖库工具库安装
        . patch_openwrt.py              # 给当前openwrt打内核补丁
        . update_openwrt.sh             # 升级当前openwrt的软链下的feeds/packages
        . README.md                     # 本说明文件


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)