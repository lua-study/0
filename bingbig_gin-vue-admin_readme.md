﻿
 
 
 
 
 
 
 
 
 
 

English | [简体中文](./README-zh_CN.md)

# Project Guidelines
[Online Documentation](http://doc.henrongyi.top/)

- Web UI Framework：[element-ui](https://github.com/ElemeFE/element)  
- Server Framework：[gin](https://github.com/gin-gonic/gin) 

## 1. Basic Introduction

### 1.1 Project Introduction

[Online Demo](http://qmplus.henrongyi.top/)
> Gin-vue-admin is a full-stack (frontend and backend separation) framework designed for management system. 
> It integrates multiple functions, such as JWT authentication, dynamic routing, dynamic menu, casbin authentication, form generator, code generator, etc. So that you can focus more time on your business Requirements.

Hi! Thank you for choosing gin-vue-admin.

Gin-vue-admin is a full-stack (frontend and backend separation) framework for developers, designers and product managers.

We are excited that you are interested in contributing to gin-vue-admin. Before submitting your contribution though, please make sure to take a moment and read through the following guidelines.

### 1.2 Contributing Guide
#### 1.2.1 Issue Guidelines

- Issues are exclusively for bug reports, feature requests and design-related topics. Other questions may be closed directly. If any questions come up when you are using Element, please hit [Gitter](https://gitter.im/element-en/Lobby) for help.

- Before submitting an issue, please check if similar problems have already been issued.

#### 1.2.2 Pull Request Guidelines

- Fork this repository to your own account. Do not create branches here.

- Commit info should be formatted as `[File Name]: Info about commit.` (e.g. `README.md: Fix xxx bug`)

-  Make sure PRs are created to `develop` branch instead of `master` branch. 

- If your PR fixes a bug, please provide a description about the related bug.

- Merging a PR takes two maintainers: one approves the changes after reviewing, and then the other reviews and merges.

### 1.3 Version list

- master: 2.0 开发版代码，生产环境

- develop: 2.0 开发版代码，测试环境

- [gin-vue-admin_v2.0_dev](https://github.com/flipped-aurora/gin-vue-admin/tree/gin-vue-admin_v2_dev) （v2.0 is no longer compatible with v1.0）

- [gin-vue-admin_v1.0_stable](https://github.com/flipped-aurora/gin-vue-admin/tree/gin-vue-admin_v1_stable) （v1.0 is kept up to date and maintained）

- [gin-vue-admin_v1.0_dev](https://github.com/flipped-aurora/gin-vue-admin/tree/gin-vue-admin_v1_dev) （v1.0 is kept up to date and maintained）


## 2. Getting started
```
- node version > v8.6.0
- golang version >= v1.11
- IDE recommendation: Goland
- After you clone the project, use the scripts in directory db to create your own database.
- We recommend you to apply for your own cloud service in QINIU. Replace the public key, private key, warehouse name and default url address with your own, so as not to mess up the test database.
```

### 2.1 Web

```bash
# clone the project
git clone https://github.com/piexlmax/gin-vue-admin.git

# enter the project directory
cd web

# install dependency
npm install

# develop
npm run serve
```

### 2.2 Server

```bash
# using go.mod

# install go modules
go list (go mod tidy)

# build the server
go build
```

### 2.3 API docs auto-generation using swagger

#### 2.3.1 install swagger 

##### (1) Using VPN or outside mainland China
````
go get -u github.com/swaggo/swag/cmd/swag
````

##### (2) In mainland China 
In mainland China, access to go.org/x is prohibited，we recommend `gopm`
````bash
# install gopm
go get -v -u github.com/gpmgo/gopm

# get swag
gopm get -g -v github.com/swaggo/swag/cmd/swag

# cd GOPATH/src/github.com/swaggo/swag/cmd/swag
go install
````

#### 2.3.2 API docs generation

````
cd server
swag init
````
After executing the above command，`docs` will show in `server/`，then open your browser, jump into `http://localhost:8888/swagger/index.html` to see the swagger APIs.

### 2.4 Docker image

Thanks [@chenlinzhong](https://github.com/chenlinzhong) for providing docker image.
```  
# start docker
docker run -itd --net=host --name=go_container shareclz/go_node /bin/bash;

# come into docker 
docker exec -it go_container /bin/bash;
git clone https://github.com/piexlmax/gin-vue-admin.git /data1/www/htdocs/go/admin;

# run web
cd /data1/www/htdocs/go/admin/QMPlusVuePage;
cnpm i ;
npm run serve;

# update db config
vi /data1/www/htdocs/go/admin/QMPlusServer/static/dbconfig/config.json;

# run server
cd /data1/www/htdocs/go/admin/QMPlusServer;z
go run main.go;
```

## 3. Technical selection

- Frontend: using `Element-UI` based on vue，to code the page.
- Backend: using `Gin` to quickly build basic RESTful API. `Gin` is a web framework written in Go (Golang).
- DB: `MySql`(5.6.44)，using `gorm` to implement data manipulation, added support for SQLite databases.
- Cache: using `Redis` to implement the recording of the JWT token of the currently active user and implement the multi-login restriction.
- API: using Swagger to auto generate APIs docs。
- Config: using `fsnotify` and `viper` to implement `yaml` config file。
- Log: using `go-logging` record logs。

## 4. Project layout

```
    ├─server  	     （backend）
    │  ├─api            （API entrance）
    │  ├─config         （config file）
    │  ├─core  	        （core code）
    │  ├─db             （db scripts）
    │  ├─docs  	        （swagger APIs docs）
    │  ├─global         （global objet）
    │  ├─initialiaze    （initialiazation）
    │  ├─middleware     （middle ware）
    │  ├─model          （model and services）
    │  ├─resource       （resources, such as static pages, templates）
    │  ├─router         （routers）
    │  └─utils	        （common utilities）
    └─web            （frontend）
        ├─public        （deploy templates）
        └─src           （source code）
            ├─api       （frontend APIs）
            ├─assets	（static files）
            ├─components（components）
            ├─router	（frontend routers）
            ├─store     （vuex state management）
            ├─style     （common styles）
            ├─utils     （frontend common utilitie）
            └─view      （pages）

```

## 5. Features

- Authority management: Authority management based on `jwt` and `casbin`. 
- File upload & download: File upload operation based on Qiniu Cloud (In order to make it easier for everyone to test, I have provided various important tokens of my Qiniu test number, and I urge you not to make things a mess).
- Pagination Encapsulation：The frontend uses mixins to encapsulate paging, and the paging method can call mixins
- User management: The system administrator assigns user roles and role permissions.
- Role management: Create the main object of permission control, and then assign different API permissions and menu permissions to the role.
- Menu management: User dynamic menu configuration implementation, assigning different menus to different roles.
- API management: Different users can call different API permissions.
- Configuration management: The configuration file can be modified in the web page (the test environment does not provide this function).
- Rich text editor: Embed MarkDown editor function.
- Conditional search: Add an example of conditional search.
- Restful example: You can see sample APIs in user management module.

```
fontend code file: src\view\superAdmin\api\api.vue 
backend code file: model\dnModel\api.go 
```
- Multi-login restriction: Change `userMultipoint` to true in `system` in `config.yaml` (You need to configure redis and redis parameters yourself. During the test period, please report in time if there is a bug).
- Upload file by chunk：Provides examples of file upload and large file upload by chunk.
- Form Builder：With the help of [@form-generator](https://github.com/JakHuang/form-generator).
- Code generator: Providing backend with basic logic and simple curd code generator.

## 6. To-do list

- [ ] upload & export Excel
- [ ] e-chart
- [ ] workflow, task transfer function
- [ ] frontend independent mode, mock

## 7. Changelog

|  Date   | Log  |
|  :---:  | --- |
|2020/01/07| Added data resource function to Role, added the return of data resource association, the demo code was synchronized, and the multi-point login interception has been turned on, which may prevent being crowded out by others |
|2020/01/13| Added configuration management function. This function is not published to the test environment. The test environment will not be published until the protection mechanism and the service restart mechanism are released. Please clone and import the sql scripts into your own database |
|2020/02/21| Modified `casbin` custom authentication method to fully support `/:params and?Query=` interface modes in RESTful API |
|2020/03/17| Added verification code function with [@dchest/captcha](https://github.com/dchest/captcha) |
|2020/03/30| Code generator implementation, form generator implementation with[@form-generator](https://github.com/JakHuang/form-generator)  |
|2020/04/01| Add frontend history tab function, add (modify) condition query example, and change the frontend background to white. (If you don't need this feature, you can change `background` in `&.el-main` to shield background color of `HistoryComponent`, which is located at line 260 of the code `web/src/view/layout/index.vue`) |
|2020/04/04| Starting version 2.x, standardize the project documentation, reconstructing the log function, and adding English comments to all methods |

## 8. Team blog

> https://blog.henrongyi.top
>
>
There are video courses about frontend framework in our blo. If you think the project is helpful to you, you can add my personal WeChat:shouzi_1994，your comments is welcomed。

## 9. Video courses

### 9.1 Development environment course

> Bilibili：https://www.bilibili.com/video/BV1Fg4y187Bw/    (coming soon)
    
### 9.2 Template course

> Bilibili：https://www.bilibili.com/video/BV1Fg4y187Bw/    (coming soon)

### 9.3 Golang basic course (coming soon)

> URL: https://space.bilibili.com/322210472/channel/detail?cid=108884

## 10. Contacts

| QQ group |  
|  :---:  |
|   |


| Jiang | Yin | Yan | Du | Yin | Song |
|  :---:  |  :---: | :---: | :---:  |  :---: | :---: |
|   |   |   |   |   |   |

### QQ group: 622360840

### Wechat group: add anyone above, comment "加入gin-vue-admin交流群"


## 11. Developers

|  Nick name   | Project position  | First name  |
|  ----  | ----  | ----  |
| [@piexlmax](https://github.com/piexlmax)  | Project sponsor | Jiang |
| [@granty1](https://github.com/granty1)  | Backend developer | Yin |
| [@Ruio9244](https://github.com/Ruio9244)  | Full-stack developer | Yan |
| [@1319612909](https://github.com/1319612909)  | UI developer |  Du |
| [@krank666](https://github.com/krank666)  | Frontend developer | Yin |
| [@chen-chen-up](https://github.com/chen-chen-up)  | Novice developer | Song |

## 12. Donate

If you find this project useful, you can buy author a glass of juice :tropical_drink:



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)