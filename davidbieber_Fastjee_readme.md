## SpringCloud && Vue 分布式微架构 + 前后端分离解决方案
> **目前正在开发阶段, 请持续关注, 相关文档会根据项目进度逐渐完善**

## 技术栈
- 后端：SpringCloud、oAuth2、JWT、Eureka、Fegin、Ribbon、Zuul、Hystrix...
- 前端：Vue2.x、iView、Webpack...

## 预览
![](http://ww1.sinaimg.cn/large/005yUwzsly1foupqs12l8g31260nzkjq.gif)

## 目录结构

    Fastjee:
          ├─fastjee-authority `(授权中心:5005)`
          ├─fastjee-common    (通用模块)
          ├─fastjee-config    `(配置中心:5001)`
          ├─fastjee-config-repo   (配置中心指向的git仓库)
          ├─fastjee-gateway   `(对外暴露的API服务网关:5002)`
          ├─fastjee-persistence (持久化工具)
          │  ├─fastjee-db-mybatis (Mybatis-Plus集成实现)
          │  └─fastjee-nosql-redis  (Redis集成实现)
          ├─fastjee-registration  `(Eureka服务注册中心:5000)`
          ├─fastjee-usercenter  `(用户中心微服务:5004)`
          └─fastjee-webui `(基于vue的前端实现, 使用iview-admin脚手架:8080)`
              ├─build (项目构建配置)
              ├─src
              │  ├─api  (API请求封装)
              │  ├─assets (静态资源)
              │  ├─components (自定义组件)
              │  ├─libs (工具文件)
              │  ├─locale (多语言文件)
              │  ├─router (路由配置)
              │  ├─store  (状态管理)
              │  ├─styles (样式文件)
              │  ├─template (模板文件)
              │  ├─utils  (自定义工具)
              │  ├─vendors (公共库文件)
              │  └─views  (页面文件)
              └─static  (静态资源)

## 开发进度

 - 2018/02/28： 初次提交, 完成项目搭建, 实现用户登陆、注销、修改密码（基于SpringSecurity + oAuth2 + JWT）

  
## 如何启动？
**请确保已具备以下环境：**
 1. jdk8
 2. mysql
 3. redis
 4. IntelliJ IDEA(不推荐使用eclipse系列的开发工具)
    ***注**：idea需安装lombok插件, 详见：https://www.cnblogs.com/aligege/p/7797642.html*
 5. nodejs (v8.9.3)
 6. npm (v5.5.1)

**配置hosts：**

    127.0.0.1       fastjee-authority.com
    127.0.0.1       fastjee-config.com
    127.0.0.1       fastjee-gateway.com
    127.0.0.1       fastjee-registration.com
    127.0.0.1       fastjee-usercenter.com
    
**拉取项目：**

先fork项目到你的账户，再拉取代码到本地:

    git clone https://gitee.com/{{yourUsername}}/Fastjee.git
    

**导入项目、修改配置：**

1.导入数据库脚本：

/Fastjee/doc/sqls/***.sql (请根据文件名事先创建好数据库, 编码为UTF-8)

2.通过idea导入Fastjee项目 （使用Maven的方式导入），等待项目building完毕后，修改相关配置：

    /Fastjee/fastjee-config-repo/application-dev.yml
    在此文件中修改有关mysql和redis连接相关的参数
    
    /Fastjee/fastjee-config/src/main/resources/application.yml
    在此文件中指定有关SpringCloudConfig配置中心的仓库地址：
      # 配置中心git仓库
      cloud:
        config:
          label: master
          server:
            git:
              uri: https://gitee.com/{{yourUsername}}/Fastjee.git
              searchPaths: fastjee-config-repo
              username:
              password:

提交相关的修改到github。

3.关于vue的API访问跨域代理（可使用默认配置）

详见： Fastjee/fastjee-webui/build/webpack.dev.config.js

    //设置跨域代理
    devServer: {
        disableHostCheck: true,
        historyApiFallback: true,
        hot: true,
        inline: true,
        stats: {colors: true},
        proxy: {
            // 授权服务器
            '/auth/*': {
                target: "http://fastjee-gateway.com:5002/api/auth/",
                // target: 'http://fastjee.s1.natapp.cc/api/auth/',
                logLevel: "debug",
                changeOrigin: true,
                pathRewrite: {
                    "^/auth": ""
                }
            },
            // 用户中心服务器
            '/uc/*': {
                target: "http://fastjee-gateway.com:5002/api/uc/",
                // target: 'http://fastjee.s1.natapp.cc/api/uc/',
                logLevel: "debug",
                changeOrigin: true,
                pathRewrite: {
                    "^/uc": ""
                }
            }
        }
    }


**启动运行：**

先启动后端服务，按顺序依次启动以下服务：

    1. RegistrationApplication
    2. ConfigApplication
    3. UserCenterApplication
    4. AuthorityApplication
    5. GatewayApplication
    
再启动前端项目：

打开idea自带的终端命令行工具, 依次执行以下命令：

    cd fastjee-webui
    npm install
    npm run dev


打开浏览器查看：http://localhost:8080, 默认用户名密码：admin / password


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)