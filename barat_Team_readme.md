# Team

小团队协作平台（任务管理系统）。**IE等旧浏览器不支持。推荐Chrome**  
如果有问题，请提ISSUE。因为这个是业余时间在搞，可能不会及时回复。但我是无法忍受有未解决的ISSUE的！  
同时，欢迎Fork，进行二次开发。如果你有更好的实现，也欢迎提交PR。  

![预览](./screenshot.png)

## 特色

1. 部署简单，只需要下载可执行文件及提供一个可用的MySQL服务。提供可视化参数配置。
2. 集成任务流管理、团队文档、文件分享等常用协作功能。
3. 支持内置帐号/LDAP/SMTP多种登录方式。
4. 代码简单，外部依赖少，二次开发门槛低。

## 旧版本升级说明

5.x版本由于重构了后台，导致数据库及配置文件与之前版本不兼容。
**新版本不再使用json作为配置文件！！！**  
**请不要直接使用之前的数据库！！！**

重要变更：

1. 【工作台】视图移除【发布任务】，所有任务的创建转到【项目】模块
2. 【管理】视图中项目相关操作移到【项目】模块
3. 【项目】相关
    * 任何人可以创建项目
    * 任务发布移到【项目】>【任务】和【项目】>【里程计划中】
    * 项目重命名/删除项目/成员管理 移动到【项目】>【项目管理中】

## 使用说明

1. [发行版](https://gitee.com/love_linger/Team/releases)中提供Windows与Linux的可执行文件。MacOS用户需要按2说明，自行编译

2. 自行编译说明。  

    2.1 环境

    * Go 1.12+  
    * Node.js
    * Git  

    2.2 编译生成可执行文件

    ```shell
    # 第一步生成前端JS代码
    cd view
    npm install
    npm run build

    # 第二步生成可执行文件
    cd ..
    go build

    # 第三步使用Go.Rice将资源文件打包入可执行文件中，如果不打入包中，需要将view/dist/目录也放入部署环境
    # 【注1】Go.Rice的安装方式`go get github.com/GeertJohan/go.rice/rice`
    # 【注2】windows下`--exec`后面的参数需要加上.exe后缀
    rice append --exec team
    ```

3. 运行team可执行文件，访问 http://localhost:8080 进行配置

## 源代码说明

为方便二次开发，对源代码结构统一说明

    repo
    |-- common                      - 通用组件
    |   |-- auth                        - 帐号验证工具
    |   |-- ini                         - INI配置文件解析
    |   |-- orm                         - 实现的一个简单的golang struct与MySQL表映射的ORM库
    |   |-- web                         - 网络框架
    |   |   |-- context.go                  - HTTP Context定义
    |   |   |-- logger.go                   - 日志工具
    |   |   |-- responser.go                - 响应类
    |   |   |-- router.go                   - 路由组件实现
    |   |   |-- session.go                  - 会话功能
    |   |   |-- value.go                    - 参数
    |
    |-- config                      - 网站配置结构
    |
    |-- controller                  - 控制器
    |   |-- admin.go                    - 处理 /admin/* 的请求 （系统管理功能）
    |   |-- documents.go                - 处理 /api/document/* 的请求 （文档管理）
    |   |-- file.go                     - 处理 /api/file/* 的请求 （文件管理）
    |   |-- home.go                     - 处理 / 的请求（主页）
    |   |-- install.go                  - 处理 /install/* 的请求（网站部署功能）
    |   |-- loginout.go                 - 处理 /login 及 /logout 的请求（登录/登出功能）
    |   |-- notice.go                   - 处理 /api/notice/* 的请求（通知功能）
    |   |-- project.go                  - 处理 /api/project/* 的请求（项目模块）
    |   |-- task.go                     - 处理 /api/task/* 的请求（任务模块）
    |   |-- user.go                     - 处理 /api/user/* 的请求（个人信息管理）
    |
    |-- middleware                  - 中间件
    |   |-- authorization.go            - 权限相关
    |   |-- logger.go                   - 访问日志记录
    |   |-- panic_as_error.go           - 统一的错误处理
    |   |-- prerequisites.go            - 部署检测
    |
    |-- model                       - 数据模型
    |   |-- document                    - WIKI在线文档
    |   |-- notice                      - 通知数据
    |   |-- project                     - 项目
    |   |-- share                       - 分享
    |   |-- task                        - 任务
    |   |-- user                        - 用户
    |
    |-- view                        - 视图层（纯前端，非服务器渲染）
    |   |-- dist                        - 静态文件（包含生成好的js bundle）
    |   |-- src                         - 前端代码（React + TypeScript）
    |   |   |-- common                      - 通信协议、常用函数、常用类
    |   |   |-- components                  - 实现的组件库，样式参考了antd与layui
    |   |   |-- pagas                       - 页面实现
    |   |   |-- app.tsx                     - 主入口
    |   |
    |   |-- package.json                - NPM依赖（建议使用cnpm安装）
    |   |-- tsconfig.json               - TypeScript配置
    |   |-- webpack.config.js           - webpack配置（打包js bundle的命令：npm run build）
    |
    |-- go.mod                      - golang工程依赖
    |-- main.go                     - 主入口









 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)