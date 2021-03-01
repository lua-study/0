# clfw

#### Description
swoole 服务管理，支持tcp，udp，http，websocket服务启动+管理

#### Support
1.  centos 8
2.  php >= 7.1
3.  swoole 4.4.8


#### Installation

1.  安装php 7.1以上版本
2.  安装swoole扩展
3.  下载源码到本地

#### Instructions

    php bin/swoole.php servName cmd
    servName 列表：
        httpServ        http服务
        tcpServ         tcp服务
        udpServ         udp服务
        webSocketServ   websocket服务
        all             所有服务
        
    cmd 列表：
        start       启动一项服务
        startall    启动所有服务
        reload      重载一项服务
        shutdown    关闭所有服务
        status      查看服务运行状态
        list        查看支持的服务列表
        restart     重启一项服务
        stop        关闭一项服务
        


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)