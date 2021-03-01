# 轻量级持续集成工具 -- 简单配置 一键发布
## 希望使用这个工具的同学能够给我个反馈，我想知道你们都是怎么用的，谢谢！！！
## 特别感谢
* 感谢t-io作者[谭总](http://git.oschina.net/tywo45)的大力支持。
* 感谢谭总将我列入t-io企业级支持的用户，我的荣幸，[点我](http://www.t-io.org:9292/donate.html?v=1)。
* 他也是第一个以资鼓励本项目的人 :pray: 。

## ATB交流QQ群：== [326363033](https://shang.qq.com/wpa/qunwpa?idkey=04c38c2f3d6aebca1930ddd5f3ccf9a5581bc0e4fffd6ea156c1cebe9e4b3716) ==

## 简介
在开发中我们需要频繁的调整代码并发布到各种环境去测试。通常会花费比部署代码要多的多的时间去进入和退出各个目录、执行启动脚本、查看启动日志。尤其是分布式系统，各个模块可能在不同的服务器上，光是部署就要来回的切换，如果注意力不能高度集中很容易忘了刚才干了什么，你最初的目的可能只是想看看代码执行的效果。假如有一款工具，可以从零开始，帮助我们完成创建文件夹、代码检出、编译打包、发布到服务器、回滚、备份、查看启动日志的整个流程，我们就可以把更多的精力放到代码本身上，只关注开发和测试，很大程度上可以提高开发效率。借鉴Jenkins的思想，但atb又不完全是一个持续集成工具，持续集成只是它的一个属性，它的目标在于节省开发人员的时间，节省到极致，只要是重复的事情决不做第二遍，把那些开发中重复的、繁杂琐碎的步骤整合起来，让开发变得更轻松愉快。它已具有和将具有以下功能：
* [x] 自动检测ATB是否满足使用条件，即前提条件中列出的软件，目前只在plugin.sh中可用，将来会用plugin.sh替换掉现在atb.sh
* [x] 根据配置自动创建代码文件夹
* [x] 自动从版本管理工具下载代码，如svn、git
* [x] 自动构建工程，依赖maven、gradle（暂未实现）等
* [x] 自动发布包到远程和本地服务器（远程服务器需要账号和密码）
* [x] 支持远程多机发布（目前只能一个一个发）
* [x] 自动重启远程或本地服务器
* [x] 自动查看启动日志
* [x] 自动备份功能，开关可控，可配置最大备份数，默认路径:${tomcat_path}/backup
* [x] 可查看服务器上备份历史，并且回滚到指定版本
* [x] 日志配色功能，想了解如何输出不同颜色日志的同学可以看看这部分代码
* [ ] 插件化，目前的想法是将不同构建工具和版本控制系统以插件的形式按照配置自动集成

你可以用它来发布代码到你自己的阿里云。在项目组内推广后备受好评，谁用谁知道。

`注意：本脚本默认认为发布程序到Tomcat的webapps下，若使用其他服务器请自行修改脚本中容器启动部分的代码`

## 前提条件
* 安装JDK并配置环境变量
* 安装maven
* 安装git或svn(windows下需安装[svn命令行工具](https://tortoisesvn.net/downloads.html))并配置到环境变量
* 安装tomcat到本地任意目录（本地发布）
* 配置ssh免密码登录（防止操作过程中频繁输入密码）

## 快速上手
1. 检出代码

    `git clone https://git.oschina.net/houjinxin/auto_build_shell.git`
2. linux、mac系统设置环境变量 （windows系统自行百度）

    ```SHELL
        export ATB_HOME=${your path}
        export PATH=$PATH:$ATB_HOME/bin
        source ${your profile}
    ```
3. 修改conf.ini文件中的配置项，参考：[配置说明](docs/配置说明.md)
4. 初始化

    `atb.sh -i`
5. 发布

    ```SHELL
        atb.sh -l # 本地
        atb.sh -r   #远程
    ```
6. 具体用法见下面帮助

```
 usage: atb [Options]

     Options：
      -v                                        版本号与项目信息
      -i                                        根据配置文件进行初始化
      -c                                        clean 工程
      -du [ -l ]                                直接上传已存在war包到本地服务器
      -du -r                        直接上传已存在war包到指定的远程服务器
      -h                                        帮助
      -l                                        自动编译打包本地部署
      -lstop                                    关闭本地服务器
      -r                            自动编译打包远程部署到指定的远程服务器
      -r   -his                     查看指定的远程服务器上备份详情"
      -r   -rb       回滚当前版本到backup_version指定的版本"

```

```
    Options说明 
     v                       -- version         版本信息
     i                       -- init            初始化项目
     c                       -- clean           来自mvn clean
     du                      -- direct upload   已有war包，直接上传；没有war包，重新打包上传 
     h                       -- help            帮助
     l                       -- local           本地
     r                       -- remote          远程
     his                     -- history         备份历史
     server_flag             -- 服务器标识        用于标识上传到哪一台远程服务器
     rb                      -- rollback        回滚命令
     backup_version          -- 备份版本号        与rb配合使用 用于指定回滚到的版本

```

## 示例
```
    `atb.sh -i` 初始化环境
    `atb.sh -r -du` war包已存在的情况下直接发布war包到远程服务器，不存在重新打包再发布
    `atb.sh` 本地发布 等同于 `atb.sh -l`
    `atb.sh -r 244` 如果你的remote_server_flags中包含244 那么就会发布到244所代表的机器上
    `atb.sh -r 244 -his` 查看244上备份历史
    `atb.sh -r 244 -rb maiev_20170415211120` 244机器上回滚当前版本到2017-04-15 21:11:20的版本

```

## 动图演示
![image](images/atb效果图.gif)

## 支持的操作系统
* windows 
	使用[Git for windows](https://git-for-windows.github.io/)的Git Bash执行脚本
* linux
* mac

## CHANGELOG
### v1.0.2 
* 增加了初始化功能
    - 自动创建`本地发版`和`远程发版`路径
    - 自动检版查本管理工具（依赖配置文件中command节点的配置，请务必保证书写正确）
    - 自动检出代码
    - 自动上传`restart.sh`脚本到不同服务器
    - 不再需要拷贝`conf.ini`到家目录，而是直接从`conf/conf.ini`读取配置信息
* 必须设置环境变量否则将无法执行
* [更多](CHANGELOG.md)

## 我的联系方式
* Email: woshihoujinxin@163.com
* QQ: 574311651
* 微信：h574311651

## TODO事项
* 考虑支持其他类型的工程结构的支持，如gradle
* 考虑支持SpringBoot工程的构建

## 需求征集
如果你们有任何好的想法和需求都可以告诉我，我来完善。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)