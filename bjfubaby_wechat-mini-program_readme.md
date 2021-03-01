# iwebshop商城系统，原生微信小程序

### 项目介绍
+ 界面高仿网易严选商城(主要是2016年wap版)
+ 测试数据来自[www.ledc.cn](http://www.ledc.cn)
+ 功能和数据库基于 iwebshop 
+ 服务端api基于php+iwebshop+MySQL
+ 计划添加基于 WorkerMan 运行的api接口

**注意：当前版本功能还未完善，请勿商用。**

### 接口进度
+ [x] 首页
+ [x] 分类目录全部分类
+ [x] 分类目录当前分类
+ [x] 微信小程序登录
+ [x] 统计商品总数
+ [x] 商品列表
+ [x] 分类数据
+ [x] 商品详情
+ [x] 获取货品数据
+ [x] 新品
+ [x] 热销
+ [x] 商品详情页（大家都在看）
+ [x] 品牌列表
+ [x] 品牌详情
+ [x] 获取购物车数据
+ [x] 添加购物车
+ [x] 更新购物车商品
+ [x] 删除购物车商品
+ [x] 选择或取消购物车商品
+ [x] 获取购物车商品件数
+ [x] 下单前信息确认
+ [x] 提交订单
+ [x] 获取微信统一下单prepay_id
+ [x] 收藏列表
+ [x] 添加或取消收藏
+ [ ] 评论列表
+ [ ] 评论总数
+ [ ] 发表评论
+ [ ] 专题列表
+ [ ] 专题详情
+ [ ] 相关专题
+ [ ] 搜索页面数据
+ [ ] 搜索数据
+ [ ] 搜索帮助
+ [ ] 搜索帮助
+ [x] 收货地址列表
+ [x] 收货地址详情
+ [x] 保存收货地址
+ [x] 删除收货地址
+ [x] 获取区域列表
+ [x] 订单列表
+ [x] 订单详情
+ [x] 取消订单
+ [ ] 物流详情
+ [ ] 足迹列表
+ [ ] 删除足迹

### 功能列表
+ 首页
+ 分类首页、分类商品、新品首发、人气推荐商品页面
+ 商品详情页面，包含加入购物车、收藏商品、商品评论功能
+ 搜索功能
+ 专题功能
+ 品牌功能
+ 完整的购物流程，商品的加入、编辑、删除、批量选择，收货地址的选择，下单支付
+ 会员中心（订单、收藏、足迹、收货地址、意见反馈）
+ ....

### 项目结构
```
├─config                
├─lib
│  └─wxParse　　　
├─pages
│  ├─auth
│  │  ├─login
│  │  ├─register
│  │  └─reset
│  ├─brand
│  ├─brandDetail
│  ├─cart
│  ├─catalog
│  ├─category
│  ├─comment
│  ├─goods
│  ├─hotGoods
│  ├─index
│  ├─logs
│  ├─newGoods
│  ├─pay
│  ├─search
│  ├─shopping
│  │  ├─address
│  │  ├─addressAdd
│  │  └─checkout
│  ├─topic
│  ├─topicDetail
│  └─ucenter
│      ├─address
│      ├─addressAdd
│      ├─collect
│      ├─coupon
│      ├─feedback
│      ├─footprint
│      ├─index
│      ├─order
│      └─orderDetail
├─static
│  └─images
└─utils
```

### 参与贡献
1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request

### 最后
1. 喜欢别忘了 Star
2. 官方博客 [ledc.cn](http://ledc.cn)
3. Q Q号码：367013672
4. 微信号：mytibet
5. 码云官方提供的使用手册 https://gitee.com/help

### 项目引用或参考
>  nideshop-mini-program 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)