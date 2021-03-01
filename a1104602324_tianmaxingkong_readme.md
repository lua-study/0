# Spring boot+vue

#### 介绍
 Spring boot ：Spring Boot是由Pivotal团队提供的全新框架，其设计目的是用来简化新Spring应用的初始搭建以及开发过程。该框架使用了特定的方式来进行配置，从而使开发人员不再需要定义样板化的配置。通过这种方式，Spring Boot致力于在蓬勃发展的快速应用开发领域(rapid application development)成为领导者。
        优点
* 嵌入Tomcat，无需部署war文件
* 自动配置Spring
* 简化Maven配置
* 没有对XML配置要求
* 采用yml 或 properties 单一配置文件
        Vue.js : Vue.js（读音 /vjuː/, 类似于 view）是一个构建数据驱动的 web 界面的渐进式框架。Vue.js 的目标是通过尽可能简单的 API 实现响应的数据绑定和组合的视图组件。它不仅易于上手，还便于与第三方库或既有项目整合。
        优点
* 易用，灵活，性能
* 双向绑定
* 可以快速打组建
* 非常容易与其他的库或者已有的项目整合

Vue.js : Vue.js（读音 /vjuː/, 类似于 view）是一个构建数据驱动的 web 界面的渐进式框架。Vue.js 的目标是通过尽可能简单的 API 实现响应的数据绑定和组合的视图组件。它不仅易于上手，还便于与第三方库或既有项目整合。
        优点
* 易用，灵活，性能
* 双向绑定
* 可以快速打组建
* 非常容易与其他的库或者已有的项目整合

 

#### 技术栈
###### 前端
```
|-- 编程语言
|   |-- html
|   |-- js
|   |-- css
|   |-- scss
|-- 开发工具
|   |-- idea
|-- 开发框架
|   |-- vue + element ui
|-- 包管理工具
|   |-- npm
|   |-- cnpm
|-- 打包工具
|   |-- webpack
```

###### 后端
```
|-- 编程语言
|   |-- java
|-- 开发工具
|   |-- idea
|-- 开发框架
|   |-- spring boot
|-- 包管理工具
|   |-- gradle构建工具下的maven资源库
|-- 打包工具
|   |-- gradle
```

 

#### 测试项目

git的项目地址  
    git：https://gitee.com/czqclm/vuedemo.git


git的安装教程  
    首先查看自己的电脑里面有没有git
    
Win的cmd和Mac的终端下输入，即可查看版本，如果提示没有找到git命令尝试重装git或者修改环境变量  
```
$ git —-version
```
Mac用户可以安装Homebrew来安装 git 等命令行工具

 

#### 构建vue项目
```
// 安装node.js，内含npm，Node.js官网：https://nodejs.org/en/ 。

// 设置npm镜像cnpm命令行工具
npm install -g cnpm --registry=https://registry.npm.taobao.org 

// 全局安装 vue-cli 
cnpm install -g vue-cli

// 建议使用2.x的版本，想用3.x的输入
cnpm install -g @vue-cli

// 先创建并进入vue项目目录
// 创建vue-cli脚手架项目
vue init my-project

// 初始化安装项目
cnpm install

// 运行项目
npm run dev
```

 

#### vue-cli项目结构大纲
```
|-- build                            // 项目构建(webpack)相关代码
|   |-- build.js                     // 生产环境构建代码
|   |-- check-version.js             // 检查node、npm等版本
|   |-- dev-client.js                // 热重载相关
|   |-- dev-server.js                // 构建本地服务器
|   |-- utils.js                     // 构建工具相关
|   |-- webpack.base.conf.js         // webpack基础配置
|   |-- webpack.dev.conf.js          // webpack开发环境配置
|   |-- webpack.prod.conf.js         // webpack生产环境配置
|-- config                           // 项目开发环境配置
|   |-- dev.env.js                   // 开发环境变量
|   |-- index.js                     // 项目一些配置变量
|   |-- prod.env.js                  // 生产环境变量
|   |-- test.env.js                  // 测试环境变量
|-- src                              // 源码目录
|   |-- components                   // vue公共组件
|   |-- store                        // vuex的状态管理
|   |-- App.vue                      // 页面入口文件
|   |-- main.js                      // 程序入口文件，加载各种公共组件
|-- static                           // 静态文件，比如一些图片，json数据等
|   |-- data                         // 群聊分析得到的数据用于数据可视化
|-- .babelrc                         // ES6语法编译配置
|-- .editorconfig                    // 定义代码格式
|-- .gitignore                       // git上传需要忽略的文件格式
|-- README.md                        // 项目说明
|-- favicon.ico                      // 网站标题栏图标
|-- index.html                       // 入口页面
|-- package.json                     // 项目基本信息
```

DEMO开发流程概要
----

###### 前端开发流程
* 安装nodejs并初始化Vue项目。
* 在已初始化的Vue项目中的开发页面头、页面尾公共组件。
* 开发登录页面组件。
* 开发首页页面组件。
* 支持跨域，请求路由，页面路由开发。
* 单独运行Vue项目查看效果。  

###### 后端开发流程
* 安装JDK11并配置好JAVA_HOME环境变量.
* 初始化springboot项目。
* 开发restful控制器。
* 支持跨域。
* 单独运行后端springboot项目查看效果。

###### 运行项目流程
* 使用webpack将Vue项目打包。
* 将打包的Vue项目集成到springboot项目中。
* 使用gradle将springboot打包成jar文件。
* 使用jdk运行jar包来启动demo项目服务，请访问地址查看效果。

###### 开发过程中注意点
* 前端项目由于启用了eslint语法检测，所以有时候多个空格或者少个空格或者少个空行，都会运行不起来前端项目，对应提示信息改下即可。
* 前端发送请求的数据格式需要与后端接收请求数据对象格式要约定一致。
* 在前后端未集成的时候需要跨域支持。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)