# open-api
SpringBoot+Dubbo+zuulfilter Route 处理Token签证，高并发对外接口管理


# zuul 路由控制
- 1.路由前限流，采用redis过期机制控制，使用app_key和method进行秒，天维度控制
- 2.路由映射过滤器，将外部请求的统一url根据method参数映射到具体地址上



# Swagger API管理
![输入图片说明](https://git.oschina.net/uploads/images/2017/0824/152528_5cb688e7_1468963.png "api.png")
# 基本路由表结构
![输入图片说明](https://git.oschina.net/uploads/images/2017/0824/154101_e2402481_1468963.png "table.png")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)