[![License](https://img.shields.io/badge/License-GPL3-blue.svg)](http://www.gnu.org/licenses/gpl-3.0.html)
[![Format](https://img.shields.io/badge/Format-JSON-blue.svg)](http://www.json.org/json-zh.html)
[![Python versions](https://img.shields.io/badge/Python-2.7.10-blue.svg)](https://www.python.org)
[![API](https://img.shields.io/badge/API-RESTful-blue.svg)](http://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)


[TOC]: # "目录"

# 目录
- [项目描述](#项目描述)
- [功能指标](#功能指标)
- [未来计划](#未来计划)
- [安装](#安装)
    - [JimV-C 快速安装](#jimv-c-快速安装)
    - [[JimV-C 手动安装](docs/install.md)](#jimv-c-手动安装)
- [架构图](#架构图)
- [[规划与建议](docs/suggest.md)](#规划与建议)
- [问题反馈](#问题反馈)
- [FAQ](#faq)
- [项目成员](#项目成员)
- [JimV 控制平台截图展示](#jimv-控制平台截图展示)
- [Demo](#demo)


## 项目描述

计算机硬件越趋便宜，性能更为强劲，企业电子信息化方面的业务加重，"互联网+"、大数据的浪潮已经掀起，物联网、AI的趋势正在形成。

因为上述的一切，虚拟化技术被处于一个软化硬件，揉和硬件与业务系统这么一个核心角色。

虚拟化技术虽然已经被普及了很久，但多数企业依然仅仅是把它当做独立的虚拟硬件来使用。在资源的科学分配、高效利用、自动化管理方面，还差些许。

JimV 是一个，结构清晰简单，易于部署、维护、使用的，低门槛企业私有云管理平台。

相比于业界知名的 OpenStack、OpenNebula...，JimV 没有很多的零部件，不需要庞大的维护团队。


## 功能指标

|功能|JimV|
|:-|:-:|
|部署复杂度|低|
|维护复杂度|低|
|KVM虚拟化|✓|
|本地存储|✓|
|共享挂载点|✓|
|GlusterFS|✓|
|Windows Guest|✓|
|Linux Guest|✓|
|Guest 性能统计|✓|
|计算节点性能统计|✓|
|CPU超分|✓|
|内存超分|✓|
|磁盘超配|✓|
|磁盘 IO 性能配额管理|✓|
|磁盘吞吐量性能配额管理|✓|
|云盘管理|✓|
|云盘热挂载|✓|
|热迁移|✓|
|批量创建|✓|
|RESTful 风格的 API|✓|
|Virtio设备|✓|
|Guest 暂停/恢复|✓|
|Guest 在线重置密码|✓|
|SSH 公钥管理、在线注入功能|✓|
|基于 Guest 实例的快照|✓|
|从快照磁盘创建模板镜像|✓|
|网络流量限额|✓|
|Guest 配置变更|✓|


## 未来计划

>* 增加计费功能
>* 增加过期 Guest 自动回收机制
>* 增加模板上传功能
>* 增加 tag 功能
>* 增加替换 IP 功能
>* 增加对 Ceph 的支持
>* 多租户
>* 用户操作轨迹
>* 用户管理功能
>* 参照 gitlab，打包出 CentOS yum 一语安装仓库
>* 国际化
>* 加入移动端的支持
>* 指定 Guest 是否随计算节点自动启动


## 安装

### JimV-C 快速安装
> 在一台服务器上仅部署 JimV-C。与其它部署 JimV-N 的计算节点一起协同工作。

1. [配置 `/etc/hosts` 文件](docs/install.md#配置-etchosts-文件)
2. 通过在线脚本自动安装 JimV-C
    ``` bash
    bash -c "$(curl -fsSL https://raw.githubusercontent.com/jamesiter/JimV-C/master/INSTALL.sh)"
    ```
3. [安装部署 JimV-N](https://github.com/jamesiter/JimV-N#%E5%AE%89%E8%A3%85)
4. [获取系统镜像模板](http://template.iit.im)
5. 上传系统镜像模板
   > 存放系统镜像模板，到所有计算节点可以访问到的路径(如果是单个计算节点，可以存放到 /opt/template_images 目录下。如果是多个计算节点，可以通过 NFS 共享该目录。)。

   `NFS 参考配置`
   ``` bash
   # NFS 服务端
   yum install nfs-utils -y
   mkdir /srv/nfs_template_images
   cat > /etc/exports  > /etc/fstab
   mount -a
   ```

6. 创建虚拟机模板
   > 在 JimV-C 控制面板中，添加虚拟机模板。
7. 享受"简单、快速开"创虚拟机实例的快乐。。。。。

### [JimV-C 手动安装](docs/install.md)


## 架构图
* [JimV 简单应用架构](./topology/JimVSimpleArchitecture.png)
* [JimV 典型应用架构](./topology/JimVRecommendArchitecture.png)


## [规划与建议](docs/suggest.md)


## 问题反馈

[提交Bug](https://github.com/jamesiter/JimV-C/issues)   技术交流 QQ 群:
377907881


## FAQ
Q1: 出现如下错误该如何解决
> could not find capabilities for arch=x86_64 domaintype=kvm

A1: 检查 BIOS 中 CPU 的 VT 技术是否启用。


## 项目成员

 
姓名:    James Iter
E-Mail: james.iter.cn@gmail.com
 


## JimV 控制平台截图展示

[JimV 控制平台截图展示](docs/screenshot.md)


## Demo

[demo.jimv.io](https://demo.jimv.io)  
[jimv.iit.im](https://jimv.iit.im)  
管理员账密 `admin`:`jimv.pswd.com`



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)