### 海风小店，开源商城（后台管理端VUE）

+ 基于开源项目NideShop重建，精简了一些功能的同时完善了一些功能，并重新设计了UI
+ 测试数据来自上述开源项目
+ 服务端api基于Ｎode.js+ThinkJS+MySQL
+ 后台管理 基于VUE.js+element-ui

### 目前基于海风小店已经上线的几款微信小程序商城
 

#### 视频教程
https://www.bilibili.com/video/av89568075

#### 本项目需要配合  
服务端： https://github.com/iamdarcy/hioshop-server  
微信小程序：https://github.com/iamdarcy/hioshop-miniprogram

线上demo：http://www.hiolabs.com/demo  
用户名：hiolabs  
密码：hiolabs

本地后台管理的  
用户名：admin  
密码：hiolabs  

   
阿里云主机：低至2折 立即去看看 

### 项目截图
+ Dashboard

 

+ 订单

 

+ 电子面单生成

 

+ 商品管理

 

+ 购物车

 

+ 用户

 

+ 运费模板

 

+ 运费模板详情页

 

### 本地开发环境配置
+ 克隆项目到本地
```
git clone https://github.com/iamdarcy/hioshop-admin
```
+ 安装依赖
```
npm install

```
安装依赖后启动后会出现一个问题。

 

这个问题是Element-ui自带的。解决方法：

在node_modules 搜索:  div class="el-form-item__label-wrap" style={style}  
然后在语句中加上单引号就可以了。

 

 

+ 启动
```
npm run dev

```

+ build 打包成静态文件
```
npm run build:web

```

生成的静态文件在dist的web文件夹中，上传到服务器就可以在浏览器中打开了。

### 功能列表
+ 订单管理：查看，修改订单价格，发货，生成电子面单，修改订单状态
+ 商品管理：添加、修改、删除商品，添加商品分类
+ 购物车：可以看到用户加入购物车的情况
+ 用户列表：用户的一些使用踪迹
+ 店铺设置：广告列表，公告管理，运费模板（可以根据地区设置相应的运费），管理员

### 最近更新 
- 新增生成分享图的功能
 

- 项目地址  
后台管理：https://github.com/iamdarcy/hioshop-admin  
服务端： https://github.com/iamdarcy/hioshop-server  
微信小程序：https://github.com/iamdarcy/hioshop-miniprogram  

- 本项目会持续更新和维护，喜欢别忘了 Star，有问题可通过微信、QQ群联系我，谢谢您的关注。
 



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)