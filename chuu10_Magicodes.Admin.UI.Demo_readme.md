# 常用命令

 

## 快速启动方式

首先保证自己已经安装了 yarn

- 包还原工具。yarn 下载地址： 
- 推荐前端工具：Vscode

通过 Vscode 打开文件夹，然后在客户端下输入

```!
yarn install            还原组件信息

npm start        启动项目
```

## 前端项目结构说明

本项目是通过 Angular CLI 构建的项目，但是为了符合 ABP 的开发方式，以及满足 DDD 的架构模式，将各个模块进行了剥离和拆分。所以目录结构也和标准的 NG CLI 项目结构发生了变化。

```!
├─src
│  │  AppPreBootstrap.ts    # ABP前端项目的启动组件，
│  │  delon.module.ts          # ng-alian的核心组件，delon
│  │  favicon.ico
│  │  hmr.ts
│  │  index.html
│  │  main.ts
│  │  polyfills.ts
│  │  root-routing.module.ts   # 最外部的根路由，判断是否登录
│  │  root.component.ts          # 根组件
│  │  root.module.ts               #根模块
│  │  styles.less                      #全局样式
│  │  typings.d.ts               # 定义的abp框架中会使用到的方法和模块名称的一些常量
│  │
│  ├─account
│  │  │  account.module.ts           # 负责整个账号体系的模块如：登录、注册、布局、租户管理等
│  │  ├─layout
│  │  │      account-languages.component.ts  # 控制登录、注册、租户登录的布局控件
│  │  ├─login
│  │  │      login.service.ts # 提供登录注册的方法
│  │  ├─register
│  │  │      register.component.ts # 注册组件
│  │  └─tenant
│  │          tenant-change.component.ts   # 切换租户名称登录的组件
│  ├─app
│  │  │  app-routing.module.ts    # 中后台管理的路由总控
│  │  │  app.component.ts  # 52abp应用的核心组件
│  │  │  app.module.ts   # 52abp应用的核心模块
│  │  ├─home
│  │  │      home.component.ts  # 后端首页组件-类似控制台
│  │  │
│  │  ├─layout
│  │  │  │  layout.module.ts # 后端的布局模块
│  │  │  │
│  │  │  ├─default
│  │  │  │  │  default.component.ts  # 布局的默认内容
│  │  │  │  │
│  │  │  │  ├─header
│  │  │  │  │  │  header.component.ts# 布局的头部组件
│  │  │  │  │
│  │  │  │  └─sidebar
│  │  │  │          sidebar.component.ts# 布局的左侧菜单栏组件
│  ├─assets
│  │  │  .gitkeep
│  │  │  appconfig.json #与后端交互配置的 端口号和域名
│  ├─environments          # 环境变量配置
│  ├─shared
│  │  │  │  shared.module.ts  # 整个项目通用贡献的模块
│  │  │
│  │  ├─animations                    # 路由的动画效果
│  │  │      routerTransition.ts
│  │  │
│  │  ├─auth                          # ABP的授权管理
│  │  │      app-auth.service.ts
│  │  │      auth-route-guard.ts
│  │  │
│  │  ├─helpers                        # 字面意思，实时通讯
│  │  │      SignalRAspNetCoreHelper.ts
│  │  │      UrlHelper.ts
│  │  │
│  │  ├─layout            # 菜单组件
│  │  │      menu-item.ts
│  │  │
│  │  ├─nav            #链接的服务类
│  │  │      app-url.service.ts
│  │  │
│  │  ├─service-proxies                # 动态生成的crud接口的代理类
│  │  │      service-proxies.ts
│  │  │      service-proxy.module.ts
│  │  │
│  │  └─session                                   # ABP所提供的Session 服务方法，提供一些基本的用户信息
│  │          app-session.service.ts
│  │
│  ├─styles                  # 可以基于ng-alain 的基础样式上进行调整
│  │      index.less
│  │      theme.less
│  │
│  └─testing
│          common.spec.ts
│
├─_mock                      # Mock 数据规则
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)