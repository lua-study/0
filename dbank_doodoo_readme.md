# doodoo

多多小程序开源版

## API接口文件 server

#### 环境需求
> node >= 8.0
> mysql
> pm2

#### 配置文件 .env
```
# 应用配置
APP_PORT=3001
APP_HOST=http://127.0.0.1:3001

# 验证码
VERIFY_MAXIP=36
VERIFY_MAXPHONE=6

# MYSQL数据库链接
MYSQL=true
MYSQL_HOST=127.0.0.1
MYSQL_USER=root
MYSQL_PASSWORD=root
MYSQL_DATABASE=doodoo
MYSQL_PORT=3306
MYSQL_CHARSET=utf8mb4

# REDIS链接
REDIS=true
REDIS_HOST=127.0.0.1
REDIS_PORT=6379
REDIS_PREFIX=xxx

# 七牛云
QINIU=false
QINIU_ACCESSKEY=xxx
QINIU_SECRETKEY=xxx
QINIU_BUCKET=xxx
QINIU_DOMAIN=xxx

# 分页
PAGE_SIZE=20

# jwt配置
JWT_SECRET=xxx
JWT_EXPIRESIN=7 days

# 微信开放平台
OPEN_APPID=xxx
OPEN_APPSECRET=xxx
OPEN_TOKEN=xxx
OPEN_ENCODINGAESKEY=xxx

# 微信服务号
WX_APPID=xxx
WX_APPSECRET=xxx
WX_TOKEN=xxx
WX_ENCODINGAESKEY=xxx

# 支付宝支付
ALIPAY_ACCOUNT=xxx
ALIPAY_PARTNER=xxx
ALIPAY_KEY=xxx

# 阿里云短信
ALISMS_APPKEY=xxx
ALISMS_APPSECRET=xxx
ALISMS_FREE_SIGN_NAME=xxx
ALISMS_TEMPLATE_CODE=xxx
```

#### 安装使用
```sh
// 进入项目
cd server
// 使用yarn或者npm安装依赖
yarn 或者 npm install
// 导入数据库文件 
/sql/doodoo.sql
// 配置数据库连接文件 
.env
// 启动项目
pm2 start pm2.json
```

#### 启动信息

```text
[doodoo] Version: 1.0.1
[doodoo] Website: http://127.0.0.1:3001
[doodoo] Nodejs Version: v10.9.0
[doodoo] Nodejs Platform: darwin x64
[doodoo] Server Enviroment: dev
[doodoo] Server Startup Time: 2497ms
[doodoo] Server Current Time: 2018-09-05 15:21:30
[doodoo] Server Running At: http://127.0.0.1:3001
```

## 后台 client

#### 安装使用
```sh
// 进入项目
cd client
// 使用yarn或者npm安装依赖
yarn 或者 npm install
// 配置API接口文件
nuxt.config.js
const apiHost = "http://127.0.0.1:3001"
// 启动项目
// 后台地址：http://127.0.0.1:3000/public/login 默认账号：18538253627 密码：18538253627
// 超管地址：http://127.0.0.1:3000/admin 默认账号：admin 密码：admin
yarn dev
```

## 小程序端 wxa

#### 使用说明
```sh
// 配置API接口文件
utils/doodoo.js // 第8行
wx.doodoo.host = "127.0.0.1:3001"
wx.doodoo.secure = true; // 开发模式
// 正式上线请把开发模式关闭
```

## 问题反馈
在使用中有任何问题，请使用以下联系方式联系我们

QQ群: 874449168(交流群①)

  

EMAIL: 786699892@qq.com

码云: https://gitee.com/doodooke/doodoo

## 官网
[多多客Doodooke小程序](http://www.doodooke.qingful.com)

## 缩略图
![](https://gitee.com/doodooke/doodoo/raw/master/thumb/1.jpg)
![](https://gitee.com/doodooke/doodoo/raw/master/thumb/2.jpg)
![](https://gitee.com/doodooke/doodoo/raw/master/thumb/3.jpg)
![](https://gitee.com/doodooke/doodoo/raw/master/thumb/4.jpg)
![](https://gitee.com/doodooke/doodoo/raw/master/thumb/5.jpg)
![](https://gitee.com/doodooke/doodoo/raw/master/thumb/6.jpg)
![](https://gitee.com/doodooke/doodoo/raw/master/thumb/7.jpg)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)