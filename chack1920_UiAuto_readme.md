    

# 关于 UiAuto 
[UiAuto](#) 是览众独立开发的一款[RPA](#)工具，致力于减少人员处理重复性任务的时间，为客户提供高效的解决方案。通过它帮助企业解决业务流程自动化难题，主要用户处理标准、重复、繁琐、大批量的工作任务。[RPA](#)应用以更低的成本、更快的速度和更高的质量进行全天候服务，极大减少人为从事规律可循的机械性工作，释放员工创造力、提升员工满意度。 

# 开始使用 
`在Windows系统下，下载安装，通过手机号注册即可使用。` 

## 安装包下载 
- v1.0.14 x64
[百度网盘下载](https://pan.baidu.com/s/1WxPE0dB_ARv0TN-BtNOhXQ)   提取码：xmjo

## 安装、配置
- 双击安装包便可自动安装。
- 安装完成之后，启动UiAuto，
- 打开系统配置页面，修改需要连接的服务器地址

## 基础组件介绍
  
- 开始：标记流程开始。
- 条件：根据上游流程执行结果，选择下游支路执行且支持多选；存在多条线路可执行时，按从判断条件的顺序执行。
- 循环：纵向锚点连接的流程线为主干，横向锚点连接的流程线为旁支，先循环执行旁支再执行主干。
- 异常：异常组件的上游组件发生异常时，则执行异常组件的下游线路，否则不执行。
- 等待：等待组件的下游线路执行完成，流程才会继续往下执行。
- 子流程：执行另一个流程。
- 常规类型（蓝色或白色圆角矩形）：
  - 蓝色：普通常规类型，几乎所有功能组件都是常规类型，对所有全局变量可读，并且可返回一个新的变量。
  - 白色：脚本常规类型，一种高级的需要编写代码的常规类型，可以对所有全局变量进行读写，也可随意删减。
- 结束：标记流程结束。 

`脚本类型仅推荐有编程能力的用户使用该类型，也请勿随意植入不能完全可知操作的外来代码，以免隐私受损。` 

## 新增流程项目
- 进入项目库，新建项目
- 进入项目后，拖动左侧组件到中间区域，开始画流程图
- 选中流程图中的每个节点，根据右侧参数区域提示，配置正确的参数
- 使用顶栏区域“执行”按钮运行项目、或配合“控制台打印”组件进行流程项目调试 

`完整的流程图必定是由“开始”通向“结束”，并且除了循环旁支、“开始”和“结束”节点外，不应该存在只有一个相邻节点的组件。` 

## 修改流程项目 
- 可在项目库找到历史项目的入口 

## 下载、上传新的功能组件 
- 移步到插件库，可管理本地功能组件。包括：下载服务器上的插件、上传自己编写的插件、删除本地下载的插件、更新插件。 

# 成为开发者

## 技术框架
>前端：[Vue](https://cn.vuejs.org/) 
>外壳：[Electron](https://www.electronjs.org/docs) 
>中间件：[NodeJS](http://nodejs.cn/api/) + [Python](https://www.python.org/) 

## 项目结构
``` markdown
UIAUTO
├ client ----- electron外壳
|   ├ .uiauto ----- 配置文件及日志记录保存目录
|   ├ build ----- 外壳图标及打包脚本
|   ├ env ----- 基础环境
|   ├ public ----- 基础插件集成，包含执行器、UI选择器、日志输出等插件
├ web ----- web目录
│   ├ build ----- 存放打包后html、css、js等文件(构建相关)
│   ├ mock ----- 模拟接口文件
│   ├ public ----- 插件文件
│   ├ src ----- src目录
│   │   ├ api ----- 存放模拟接口文件
│   │   ├ assets ----- 静态文件，存放图片等
│   │   ├ components ----- 存放小组件(面包屑等)
│   │   ├ icons ----- 存放svg文件
│   │   ├ layout ----- 存放导航栏、设置等组件
│   │   ├ router ----- 路由文件
│   │   ├ store ----- vuex store文件
│   │   ├ styles ----- 框架样式文件
│   │   ├ util ----- 公用文件
│   │   ├ view ----- 模块文件
│   │   │   ├ dependency ----- 环境依赖模块
│   │   │   ├ home ----- 首页模块
│   │   │   ├ login ----- 登录模块
│   │   │   ├ plugin ----- 插件库模块
│   │   │   ├ project ----- 项目模块
│   │   │   ├ setting ----- 设置模块
│   │   └   └ workspace ----- 项目库模块
│   ├ App.vue ----- 入口文件
│   ├ main.js ----- 入口js依赖文件
│   ├ permission.js ----- 权限文件
└   └ setting.js ----- 设置文件
```

## 环境准备
- 下载[Java8]()的jre，并解压至目录client/env/jre
    - 百度网盘下载地址：[https://pan.baidu.com/s/1XNiOdzLUZ1QkmVYLdhugiw](https://pan.baidu.com/s/1XNiOdzLUZ1QkmVYLdhugiw) 提取码：l735 
- 下载[Python](http://python.org)解释器，并解压至目录client/env/python/win32
    - 百度网盘下载地址：[https://pan.baidu.com/s/12wc_lEmrlxdi05Nd5tvrvA](https://pan.baidu.com/s/12wc_lEmrlxdi05Nd5tvrvA) 提取码：qyst
- 在clent/public目录下打开命令行终端执行命令`npm install`

## 执行器 
> 目前执行器支持执行NodeJS、Python、Java等三种语言开发的插件。 
> 执行器基于Python语言开发，执行流程逻辑。 
> 针对基于NodeJS开发的插件的数据交互采用了SOCKET传输的方式。 
> Java插件的支持需要运行环境安装vc_redist_2017。 

## UI选择器 
> 目前UI选择器支持大部份标准Windows组件及常见网页元素的属性捕获。 
> UI选择器基于Python语言开发 
> 标准Windows组件属性捕获是通过UIAutomationCore.dll的api实现。 
> 网页元素的属性捕获是通过是向浏览器注入javascript脚本来实现，因此，浏览器必须通过webdriver启动。 

## 插件开发 
- 目前UiAuto的插件支持NodeJS、Python、Java等三种语言开发。 
- 相关资料：
  - [开发规范](./plugin.md) 
  -  插件开发Demo  

# 软件截图 
   
   
   
   


# [常见问题](./quesions.md)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)