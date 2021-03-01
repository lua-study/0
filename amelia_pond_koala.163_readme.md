#### 0- 安装教程

终端里输入 ： npm install

#### 1- CLI结构说明
``` 
--| project
    --| src
        --| index.html
        --| scripts
            --|index
                --|index.xx1.js
                --|index.xx2.js
 ​		 --| stylesheets
    --|dev
    --|dist
```

#### 2- 依赖

基于nodeJs ,gulp的PC端工程化开发环境

```javascript
{
  "name": "koala.163",
  "version": "1.0.0",
  "description": "nope",
  "main": "index.js",
  "scripts": {
    "start": "./node_modules/.bin/gulp gulp-dev",
    "build" : "./node_modules/.bin/gulp build"
  },
  "keywords": [
    "kaola.com.163"
  ],
  "author": "Amelia",
  "license": "MIT",
  "devDependencies": {
    "@babel/core": "^7.4.4",
    "@babel/preset-env": "^7.4.4",
    "gulp": "^3.9.1",
    "gulp-babel": "^8.0.0",
    "gulp-clean-css": "^4.2.0",
    "gulp-concat": "^2.6.1",
    "gulp-connect": "^5.7.0",
    "gulp-imagemin": "^5.0.3",
    "gulp-sass": "^4.0.2",
    "gulp-uglify": "^3.0.2",
    "http-proxy-middleware": "^0.19.1",
    "node-sass": "^4.12.0"
  }
}
```

#### 3- 运行执行指令
- npm start - 转存并运行
- npm run build - 打包压缩

#### 4- 完成进度记录
- 0515 - [9h]
  1. 首页的导航 / 二级菜单 / 广告栏目 / 选项卡 / 轮播图
  2. 商品列表页的头部

- 0516 - [9h]
  1. 首页的推荐栏目 / 秒杀栏目 / 懒加载
  2. 登陆页面样式搭建
  3. 注册页面样式搭建
  4. 搜索框实现进入商品列表功能

- 0517 - [9h]
  1. 首页的全部热门模块
  2. 调整了json加载在gitee.io上无法正常显示的问题
  3. 完成了首页的 轻奢馆/美妆专区等数据渲染部分

- 0518 - [9h]
  1. 增加了公共footer
  2. 完成了商品列表页面，实现了分页 / 懒加载
- 0519 -[5h]
  1. 完成了首页的吸顶菜单和其他固定定位
  2. 完成了登陆注册与后台的链接

- 0520 - [9h]
  1. 完成了登陆注册后首页显示所携带cookie的功能。
  2. 完成了部分购物车功能

- 0521 - [9h]
  1. 完成了购物车的功能
  2. 完成了首页的楼梯功能
  3. 完成了详情页的放大镜功能

#### 5- 主要界面
- 主页：包含轮播图，json渲染，吸顶及两端fixed固定菜单
- 登录页：正则验证 / 后端接口连接 / cookie
- 注册页：正则验证 / 后端接口连接 / cookie
- 商品列表页：json渲染 / 分页 
- 商品详情页面：放大镜 / 添加进入购物车 (localStorage)
- 购物车页面：读取缓存 / 修改缓存 (localStorage)

#### 6- 项目简介及基本功能介绍
1. 在搜索框中，可以输入内容并进行搜索。点击搜索的放大镜icon后，页面会跳转至商品列表页。
2. 点击商品列表页中的前四项。会进入到商品详情页
3. 点击页面顶部的购物车按钮，会跳转到购物车页面。
4. 点击顶部导航的[登陆][注册]按钮，可以进入到登陆 / 注册页面
5. 用户成功登陆或注册之后，顶部的nav部分会显示用户注册的手机号。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)