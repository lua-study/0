 
   
 


 
   
     
   
   
     
   
     
     
   
 


  [English](https://github.com/wenjianzhang/go-admin/blob/master/README.en.md) | 简体中文
  

##### 基于Gin + Vue + Element UI的前后端分离权限管理系统 

系统初始化极度简单，只需要配置文件中，修改数据库连接，系统启动后会自动初始化数据库信息以及必须的基础数据

[在线文档](https://wenjianzhang.github.io/go-admin-site)

## ✨ 特性

- 遵循 RESTful API 设计规范

- 基于 GIN WEB API 框架，提供了丰富的中间件支持（用户认证、跨域、访问日志、追踪ID等）

- 基于Casbin的 RBAC 访问控制模型

- JWT 认证

- 支持 Swagger 文档(基于swaggo)

- 基于 GORM 的数据库存储，可扩展多种类型数据库 

- 配置文件简单的模型映射，快速能够得到想要的配置

- 代码生成工具

- 表单构建工具

- 多命令模式

- TODO: 单元测试


## 🎁 内置

1.  用户管理：用户是系统操作者，该功能主要完成系统用户配置。
2.  部门管理：配置系统组织机构（公司、部门、小组），树结构展现支持数据权限。
3.  岗位管理：配置系统用户所属担任职务。
4.  菜单管理：配置系统菜单，操作权限，按钮权限标识等。
5.  角色管理：角色菜单权限分配、设置角色按机构进行数据范围权限划分。
6.  字典管理：对系统中经常使用的一些较为固定的数据进行维护。
7.  参数管理：对系统动态配置常用参数。
8.  操作日志：系统正常操作日志记录和查询；系统异常信息日志记录和查询。
9.  登录日志：系统登录日志记录查询包含登录异常。
10. 系统接口：根据业务代码自动生成相关的api接口文档。
11. 代码生成：根据数据表结构生成对应的增删改查相对应业务，全部可视化编程。
12. 表单构建：自定义页面样式，拖拉拽实现页面布局。
13. 服务监控：查看一些服务器的基本信息。

## ⚙ 配置详情

1. 配置文件说明
```yml
settings:
  application:  
    # 项目启动环境            
    mode: dev  # dev开发环境 test测试环境 prod线上环境；
    host: 0.0.0.0  # 主机ip 或者域名，默认0.0.0.0
    # 服务名称
    name: go-admin   
    # 服务端口
    port: 8000   
    readtimeout: 1   
    writertimeout: 2 
  log:
    # 日志文件存放路径
    dir: temp/logs
  jwt:
    # JWT加密字符串
    secret: go-admin
    # 过期时间单位：秒
    timeout: 3600
  database:
    # 数据库名称
    name: dbname 
    # 数据库类型
    dbtype: mysql    
    # 数据库地址
    host: 127.0.0.1  
    # 数据库密码
    password: password  
    # 数据库端口
    port: 3306       
    # 数据库用户名
    username: root   
```

2. 文件路径  go-admin/config/settings.yml


## 📦 本地开发

### 首次启动说明

```bash
# 获取代码
git clone https://github.com/wenjianzhang/go-admin.git

# 进入工作路径
cd ./go-admin

# 编译项目
go build

# 修改配置
vi ./config/setting.yml 

# 1. 配置文件中修改数据库信息 
# 注意: settings.database 下对应的配置数据
# 2. 确认log路径

```

### 初始化数据库，以及服务启动
```
# 首次配置需要初始化数据库资源信息
./go-admin init -c config/settings.yml -m dev


# 启动项目，也可以用IDE进行调试
./go-admin server -c config/settings.yml -p 8000 -m dev

```
[在线文档](https://wenjianzhang.github.io/go-admin-site)


### 文档生成
```bash
swag init  

# 如果没有swag命令 go get安装一下即可
go get -u github.com/swaggo/swag/cmd/swag
```

### 交叉编译
```bash
env GOOS=windows GOARCH=amd64 go build main.go

# or

env GOOS=linux GOARCH=amd64 go build main.go
```


## 🎬 在线体验
> admin  /  123456

演示地址：[http://www.zhangwj.com](http://www.zhangwj.com/#/login)


## 📨 互动

 
   
       
       
       
   
   
     微信 
     此群已满 
         
   
 
  

## 🤝 特别感谢
[chengxiao](https://github.com/chengxiao)
[gin](https://github.com/gin-gonic/gin)
[casbin](https://github.com/casbin/casbin)
[spf13/viper](https://github.com/spf13/viper)
[gorm](https://github.com/jinzhu/gorm)
[gin-swagger](https://github.com/swaggo/gin-swagger)
[jwt-go](https://github.com/dgrijalva/jwt-go)
[vue-element-admin](https://github.com/PanJiaChen/vue-element-admin)
[ruoyi-vue](https://gitee.com/y_project/RuoYi-Vue)

## 🤟 打赏

> 如果你觉得这个项目帮助到了你，你可以帮作者买一杯果汁表示鼓励 :tropical_drink:


 

## ❤️ 赞助者

zhuqiyun LLL狐

## 🔑 License

[MIT](https://github.com/wenjianzhang/go-admin/blob/master/LICENSE.md)

Copyright (c) 2020 wenjianzhang



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)