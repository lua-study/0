# CentOS安装docker

## 说明

主要作用是傻瓜式安装，并且使用国内源来加快安装速度，也安装一些基础包。

*默认Docker lib目录设置为`/home/docker/lib/`，因为默认CentOS的分区`/`只有50g，其他都在`/home`下。具体请查看脚本中的DOCKER_LIB_HOME。*

当前系统环境 `CentOS Linux release 7.7.1908 (Core)`

### 版本问题

由于`离线安装方式`一般需要匹配CentOS系统版本，而为了避免安装脚本里面做过多的复杂判断，所以每个版本会建一个分支。请使用时，自行根据CentOS版本使用对应的安装分支。参见 https://gitee.com/kennylee/install-docker/branches

注：若未找到对应版本时，建议试试相近的版本。CentOS8目前阿里云上还未找到离线镜像，所以暂时不支持。

而`在线安装方式`一般情况下兼容性还是比较好的。

### install-docker.sh

在线安装脚本，会自动优化centos和docker等包的源路径，使用国内镜像，避免默认情况下从国外下载的速度缓慢问题。

下载后直接运行即可，如下：

```
sh install-docker.sh
# 或者访问git来安装
curl -sSL https://gitee.com/kennylee/install-docker/raw/master/install-docker.sh | bash -s
```

* 根据实际情况修改docker lib的配置目录，默认是 `/home/docker/lib/`
* 如果有加速镜像，如阿里云的docker加速镜像，可运行脚本的时候添加上，参考:

	```
	sh install-docker.sh https://your-account.mirror.aliyuncs.com
	```

### install-docker-offline.sh

某些特殊环境与互联网隔离，所以有了此脚本和运行环境。

离线安装除了docker-ce包外，还有一些依赖包。建议CentOS最小化安装即可，然后把DVD光盘拷贝到磁盘，再弄成本地源。

_不过为了方便安装，代码内也已经包含了这些包的安装，但升级起来就相对麻烦了，目前docker依赖包如下 *（相关依赖包会更新，以下仅作参考）* ：_

```
(1/10): audit-libs-python-2.7.6-3.el7.x86_64.rpm                                                                                                              |  73 kB  00:00:00     
(2/10): libsemanage-python-2.5-8.el7.x86_64.rpm                                                                                                               | 104 kB  00:00:00     
(3/10): libtool-ltdl-2.4.2-22.el7_3.x86_64.rpm                                                                                                                |  49 kB  00:00:00     
(4/10): container-selinux-2.28-1.git85ce147.el7.noarch.rpm                                                                                                    |  29 kB  00:00:00     
(5/10): libcgroup-0.41-13.el7.x86_64.rpm                                                                                                                      |  65 kB  00:00:00     
(6/10): libseccomp-2.3.1-3.el7.x86_64.rpm                                                                                                                     |  56 kB  00:00:00     
(7/10): python-IPy-0.75-6.el7.noarch.rpm                                                                                                                      |  32 kB  00:00:00     
(8/10): checkpolicy-2.5-4.el7.x86_64.rpm                                                                                                                      | 290 kB  00:00:01     
(9/10): policycoreutils-python-2.5-17.1.el7.x86_64.rpm                                                                                                        | 446 kB  00:00:01     
(10/10): setools-libs-3.3.8-1.1.el7.x86_64.rpm                                                                                                                | 612 kB  00:00:03  
```

### 卸载Docker

```
sudo uninstall-docker.sh
```

注意的 `DOCKER_LIB_HOME` 值，如果安装时修改了install-docker.sh脚本中的该值，这里也需要同样修改才能删除docker的资源文件。

## 关于自行更新离线包

>由于本项目不可能一直保持最新的包，所以提供个方便大家自行更新本地包的方法给大家参考：

本地离线包需要不定时手动更新并且测试通过才提交，但每次找更新的资源比较繁琐（DRY），所以编写了个脚本 `update-offline-packages.py`。

>注意脚本中的 `centos_version` 参数。*因为阿里的镜像库仅对最新版本的进行备份，不支持旧版本*，所以会造成旧版本的系统无法拿到新包的问题，这种情况下如果想要更新离线包，只能手动处理了。

PS：这个脚本维护起来还是比较麻烦，命名风格老是变啊QAQ...

### 更新离线依赖包

```
python update-offline-packages.py
```

运行后可以在 `git status` 命令来查看包的变化情况，如果有更新，可以进一步进行测试，不过这里需要依赖vagrant环境，具体vagrant环境的搭建就不在这里说明了（相应的，如果想要测试其他版本centos的使用情况，也可以自行修改Vagrantfile中的配置）。

>注：由于 *某些不可抗拒的因素* ，下载依赖包的时候可能会比较慢（已经尽量避免了），所以如果自行更新离线依赖包的时候请优化好网络或者手动下载`docker-compose`包到本地（参考旧包命名方式），然后放到`packages`目录下，再删除旧文件。

### 测试离线安装包

```
cd test && sh test-docker-offline.sh
```

如果正常的话可以看到docker和docker-compose的版本情况（一般都会正常的啦）

### 清理测试虚拟机

```
cd test && sh clean-test-vm.sh
```

----

希望对大家有点帮助。






 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)