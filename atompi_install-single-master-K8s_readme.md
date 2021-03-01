# install-single-master-K8s

#### 介绍

两个命令从空白系统到单 master 节点 K8s 集群。

支持操作系统： CentOS 7+

支持 K8s 版本： v1.14.0+

#### 软件架构

单 master 节点，使用 kubeadm 快速部署，使用 calico 作为 CNI 插件。生产环境 HA 部署见：[Prod-K8S-HA-Installer](https://gitee.com/atompi/Prod-K8S-HA-Installer)

#### 安装教程

1.  init node (脚本执行完成会自动重启服务器)

```
# 两个参数： $hostname $host_ip
sh pre_reboot.sh $hostname $host_ip
```

2.  初始化集群并完成安装

```
# 三个参数： $docker_version $kubernetes_version $host_ip
sh post_reboot.sh $docker_version $kubernetes_version $host_ip
```

#### 参与贡献

1.  Fork 本仓库
2.  新建 Feat_xxx 分支
3.  提交代码
4.  新建 Pull Request


#### 码云特技

1.  使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2.  码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3.  你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4.  [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5.  码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6.  码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)