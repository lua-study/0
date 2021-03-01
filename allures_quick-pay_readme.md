 
 
 


# quick-pay
 个人支付页面.自动适配PC ,手机. 识别微信/支付宝. 支付宝可以自动跳转打开客户端
 
## 文件说明:

 function.php : 公用功能函数,配置 
 order.php : 下单演示,订单状态查询 
 notify.php : 订单通知接受 

 index.pug 下单页面 
 pay.pug : 支付页面 
 complate.pug : 支付完成页面 
 src/rest-mapping.js: 配置文件,将接口地址改成自己的实际地址 
 config/dev.env.js  开发环境配置文件 
 config/prod.env.js 生产环境配置文件 
 config/index.js  项目构建配置文件 
 dist/ 将前端和源代码进行构建后生成的目录 
 

#### 项目所用技术栈参考文档
- [Webpack](https://webpack.js.org/).
- [Gulp](https://gulpjs.com/).
- [Vue](https://vuejs.org/)
- [Axios](https://github.com/axios/axios)
- [ESLint](https://eslint.org/)
- [Pug](https://pugjs.org/api/getting-started.html)


## 开始使用

#### 本地开发配置
将根路径下的所有php文件和pxpay文件夹放置到php容器中，并修改dev.env.js 中的RESUEST_HOST字段 

开启跨域请求: 编辑 order.php 进行配置

#### 安装环境
下载并安装 Nodejs (https://nodejs.org/en/)

#### 安装依赖
`npm install`

#### 本地开发
`npm run dev`

`访问：http://localhost:8080/`

#### 生产环境资源发布
`npm run build`  

QQ交流群
153497287

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)