# Netadmin-driver
## Netadmin-driver 是什么?
- 将脚本或者命令发送至juniper或者cisco执行，并且获取返回结果
- 提供http服务，接收和返回json. 采用[tornado](https://github.com/tornadoweb/tornado)开发
- 支持并发到多台设备执行命令
- 此工程为[netadmin](https://gitee.com/pippozq/netadmin)提供底层驱动服务
## Build  By

Package | Page
---|---
Python3.6|https://www.python.org/downloads/release/python-363/
Junos-eznc | https://github.com/Juniper/py-junos-eznc
Ansible | https://github.com/ansible/ansible
Tornado |https://github.com/tornadoweb/tornado


## docker 镜像打包
提供了dockerfile，可直接打包成镜像
```
docker build -t  /netadmin-driver:  .

```

## Web Interface

### Juniper
#####  Command

```
define a JSON named "json_data" like
{
 "hosts":["192.168.1.2","192.168.1.3".....],
 "port":22,
 "user": {
    "name":"ssh name",
    "password":"ssh password"
    },
 "command": "show version"
 }
```

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' -d post_data 'http://netadmin-driver-url/juniper/command'
```
#####  Config

```
define a JSON named "json_data" like
{
 "hosts":["192.168.1.2","192.168.1.3".....],
 "port":22,
 "user": {
    "name":"ssh name",
    "password":"ssh password"
    },
 "file_content": "line1\nline2\n""
 }
```
```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' -d post_data 'http://netadmin-driver-url/juniper/config'
```



### Cisco
##### Command

```
define a JSON named "json_data" like
{
 "hosts":["192.168.1.2","192.168.1.3".....],
 "port":22,
 "user": {
    "name":"ssh name",
    "password":"ssh password"
    },
 "command": "show version"
 }
```

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' -d post_data 'http://netadmin-driver-url/cisco/command'
```
#### Config

```
define a JSON named "json_data" like
{
 "hosts":["192.168.1.2","192.168.1.3".....],
 "port":22,
 "user": {
    "name":"ssh name",
    "password":"ssh password"
    },
 "file_content": "line1\nline2\n",
 "blob_id":"Forza_Milan"
 }
```
```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' -d post_data 'http://netadmin-driver-url/cisco/config'
```
"blob_id" 是gitlab中文件的id,作为本地临时文件名, 如果你只是单独使用该服务，可以随意修改这个值.比如"Forza_Milan"

## License
GNU General Public License v3.0

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)