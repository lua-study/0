# budo-config V2

## 1. 使用

### 1.1. 引入依赖，最新版本号请从私服确认
```
 
     org.budo 
     budo-boot-starter-config-client 
     xxx 
 
```

### 1.2. 配置SpringBean
```
 
 

 
 

 
 
```

### 1.3. 机器初始化配置(开发环境电脑或生产环境服务器)

文件`\.budo.config\.server.properties`，Windows环境在当前磁盘下（如 `D:\.budo.config\.server.properties`）

内容

```
# 配置中心地址
budo.config.url=http://conf-ip:8888/list_for_artifact_v2.json
# 给当前机器起个名字,与机器上运行的程序无关
budo.config.serverName=lmw
# 给前机器生成一个随机密码
budo.config.serverSecret=12369
# 环境(开发/测试/生产),生成环境定义为800
budo.config.profile=100
```

## 4. 配置管理

1. 数据库中 `t_artifact` 表管理应用程序；`t_artifact_parent` 管理应用继承关系，以实现配置复用；`t_config` 存储配置的值; `t_server` 管理服务器信息; `t_server_artifact` 管理应用在那台服务器上

2. 敏感值，如密码，存储在外部文件中；`t_config.value` 通过 `dbpwd@file:///pwd.txt` 的形式引用

3. 查看配置信息 [artifact-list](http://taojin-config-host/artifact-list)

3. 导入properties配置 [properties-import](http://taojin-config-host/properties-import.jsp)，不可以导入到已有的 artifactKey，应每次加一个新的，再通过继承来组合使用

4. 可通过 `key@this` 方式提供配置项别名，如已通过继承的方式得到配置 `db.username=root`，而项目中通过 `db.user` 引用，则可添加配置 `db.user=db.username@this`

## 5. 程序安全

1. 仅允许指定客户端IP访问

2. 每次请求sign签名校验，每次访问时间参数不允许相同

3. 返回内容加密传输

4. 为每次请求记录日志

5. 网络层限制，只在内网运行

6. 密码等关键数据不存到数据库，由运维人员保存到文件系统


## 6. 运行安全

1. 仅由运维人员掌握这个数据库的写权限，核心开发人员掌握读权限，其他人不接触这个数据库。

2. 运维人员应当周期性的备份这个数据库，以免以外丢失。

3. 可周期性的修改资源的密码。


## 7. 其他

[V1](V1.md)

[doc 2.0](http://git.itaojin.cn/taojin/budo-config/wikis/V2.0.0)

[Apollo 在Spring Boot初始bootstrap阶段注入配置](https://github.com/ctripcorp/apollo/wiki/Java%E5%AE%A2%E6%88%B7%E7%AB%AF%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%97#3213-%E5%9C%A8spring-boot%E5%88%9D%E5%A7%8Bbootstrap%E9%98%B6%E6%AE%B5%E6%B3%A8%E5%85%A5%E9%85%8D%E7%BD%AE)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)