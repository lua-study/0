# 说明：
    本文档适用于python3目录下的工程，python2的脚本不不适用。

    python2目录工程适用于centos6/pyhton2.7版本

    依赖安装：yum install file rsync , pip install pyinotify


# 简介：

- 监控指定的目录，目录内有修改操作就执行同步操作，同步到指定服务器的指定目录中。
- 监控项可修改可修改添加，默认只监控修改。
- 可配置监控目录、远程ip、端口、同步的目标地址。
- 默认日志打印info级别，日志路径可配置
- 所有配置文件在settings.py中

# 环境：
开发语言：python3.6

开发环境：centos6

开发依赖：
```
pip install pyinotify
yum install file rsync
```
# 启动：
python dir-real-rsync.py
# 关闭：
- kill掉pid号即可：
- cat /tmp/pyinotify.pid|xargs kill && rm -f /tmp/pyinotify.pid

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)