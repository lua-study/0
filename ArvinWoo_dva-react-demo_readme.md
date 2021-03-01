# React-Dva技术分享培训

#### 项目介绍
公司内部组织的React-Dva技术分享培训会，意在让广大程序员去认识 React、Dva，认识前段框架。

#### 软件架构
![软件架构说明](https://images.gitee.com/uploads/images/2018/0830/141940_dce422cb_962024.png "前端框架.png")
#### 安装教程
##### 克隆本项目
- 如果直接下载会提示登陆，建议大家用 git clone 的方式进行下载项目
- git clone https://gitee.com/kangkang521/dva-react-demo.git


##### 该工程是依赖于 node.js 环境才能够正常工作，若需要在本地机器上运行本项目，则首先需要安装 node.js 环境。
- 官方的 node.js 安装包：[node下载地址](https://nodejs.org/en/download/)，大家可以根据自己的机器进行选择适合自己的 node.js 安装包即可。
- 在安装完 node.js 环境之后，可打开命令行，输入 node -v 若能够看到相应的版本信息，那么祝贺你，你已经安装成功；若提示你命令不存在，那么很遗憾，你没有安装成功，仍需要你进行相应的安装。如下图：![node环境检查](https://images.gitee.com/uploads/images/2018/0830/142640_1cedc1f5_962024.png "QQ截图20180830142435.png")
- node.js 环境安装配置成功之后，你可以打开你从 git 拉下的代码的根目录：/dva-react-demo ，然后在此路径下打开命令行，也可以打开命令行之后切到此目录下。接着我们需要执行： **npm install** 命令，这一步是进行本项目的依赖安装，在安装的过程中可能会因网络的原因比较慢，大家需耐心等待。另外如果你执行此命令实在不行，没能够成功安装依赖。那么你可以尝试去更换一下镜像地址，具体操作大家请问度娘，这里就不做具体说明了。
- 若大家按照以上两种方式还是没能够解决问题，还是安装不成功的话，那么大家也可以去了解一下 yarn 这个命令，具体实现，请问度娘。
- 至此你的环境已经搭建好，项目的依赖也已经安装好接下来就可以启动项目了
- 在命令行输入 npm start 若用 yarn 的 则可以输入 yarn start 在第一次启动项目的时候会有一些慢，大家请耐心等待！
- 在等到你的命令行出现以下字样的时候，那么你的项目已经启动成功了。如下图：![启动成功](https://images.gitee.com/uploads/images/2018/0830/143802_8c6e1d2b_962024.png "QQ截图20180830143717.png")
- 项目启动成功之后就可以打开浏览器在上面输入 http://localhost:8000 回车，就可以看到相应的页面了。

#### 使用说明

### 目录结构

```bash
├── /mock/           # 模拟数据的目录
├── /dist/public     # 项目输出目录
├── /public          # 公共文件，编译时copy至dist目录
├── /src/            # 项目源码目录
│ ├── /components/   # UI组件及UI相关方法
│ ├── /layouts/      # 全局公共的布局
│ │ ├── app.js       # 项目的全局布局
│ │ ├── app.less     # 项目的全局布局的样式
│ │ └── index.js     # 项目的入口类
│ ├── /models/       # 全局数据的数据模型目录
│ │ └── app.js       # 数据模型的实现类
│ ├── /pages/        # 包含全部的业务侧的所有及生成路由的文件夹
│ ├── /plugins/      # 全局的插件
│ │ └── onError.js   # 全局错误处理
│ ├── /services/     # 全局数据的数据接口
│ │ ├── app.js       # 数据接口（包含人员信息的接口）
│ ├── /themes/       # 主题
│ │ ├── default.less # 全局样式
│ │ ├── index.less   # 全局样式
│ │ ├── mixin.less   # 全局样式
│ │ └── vars.less    # 全局样式变量
│ ├── /utils/        # 工具函数
│ │ ├── config.js    # 项目常规配置
│ │ ├── index.js     # 工具函数输出的主文件
│ │ ├── request.js   # 异步请求函数
│ │ └── theme.js     # 项目需要在js中使用到样式变量
│ └── global.js      # 全局配置
├── package.json     # 项目信息
├── .eslintrc        # Eslint配置
└── .roadhogrc.js    # roadhog配置
```
#### 联系方式

- 因为本项目是开源的，任何人都可以看到，所以联系方式只留了个人邮箱，希望大家理解
- 邮箱：liyankang@sdcncsi.com.cn 
- 大家若有任何问题都可以以邮件的形式想我提问。
- 如有注册码云账户的人员也可以直接在 [issues](https://gitee.com/kangkang521/dva-react-demo/issues) 上直接进行提问，我会为大家解答。
- 另外大家由邮箱提出的问题，我也会在 [issues](https://gitee.com/kangkang521/dva-react-demo/issues) 进行详细的说明

#### 参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)