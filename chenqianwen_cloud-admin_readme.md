# 云－后台管理系统
cloud-admin

### 系统模块
1. 开发环境请求url配置：src/config/index.js
2. 服务网关：spring cloud zuul
3. xxxx 

## 系统启动
```
docker run -d --restart=always --name nacos-standalone -e MODE=standalone -p 8848:8848 nacos/nacos-server:latest
nacos/nacos

docker run -d --restart=always --name redis -e REDIS_PASSWORD=123456 -p 6379:6379 bitnami/redis:latest

docker run -d --name elasticsearch -p 9200:9200 -p 9300:9300 itzg/elasticsearch

docker run -d --link elasticsearch:elasticsearch --link rabbit:rabbit --name zipkin -e STORAGE_TYPE=elasticsearch -e ES_HOSTS=elasticsearch -e RABBIT_ADDRESSES=rabbit:5672 -p 9411:9411 openzipkin/zipkin

docker run --env MODE=standalone --name nacos-quick-start -d  -p 8848:8848  paderlol/nacos


```

### base64加密地址
http://tool.chinaz.com/Tools/Base64.aspx

### 系统设计
1. 网关设计： 动态路由／权限校验
zuul经过路由匹配之后，调用目标服务时，将会忽略掉指定的请求头信息RibbonRoutingFilter -> buildCommandContext
需配置：zuul.sensitive-headers=

2. nacos配置中心：Spring Cloud 应用获取数据
3. 认证中心： oauth2
https://github.com/spring-cloud-incubator/spring-cloud-alibaba/blob/master/spring-cloud-alibaba-examples/nacos-example/nacos-config-example/readme-zh.md
4. 系统核心：
用户
网关调用用户服务校验用户权限。用户服务中通过拦截器解析token获取用户信息。
原则上所有需要服务都应该依赖auth-client。
例如：cloud-admin需要请求时验证token的服务只需在拦截器中初始化认证bean。cloud-gate-server需要调用验证token方法。
cloud-auth-client验证token的方法，需要认证服务器的支持。需要通过feign调用cloud-auth-server验证token的方法。所以需要配置cloud-auth-server不校验/auth/**请求

服务之间feign调用时，请求的头信息和请求参数不能进行传递。
通过实现RequestInterceptor接口，配置feign客户端@FeignClient(configuration＝"")，实现头信息传递。
参考：https://www.jianshu.com/p/919d066a07aa




2. xxxx
3. xxxx
base_user 所有用户注册信息
base_tenant 租户信息
超级租户下默认建立三个角色 
    权限管理角色 我的账户 角色管理 组织机构(绑定角色、添加人员)
    WMS应用菜单角色
    TMS应用菜单角色
base_application 应用信息
base_application_role
base_app_order

租户注册自动购买平台权限管理产品


用户登录子应用1 先到auth鉴权登录
再到子admin获取用户的权限菜单

oauth有问题参见:
https://blog.csdn.net/qq_30905661/article/details/82704746

http://localhost:8080/api/auth/oauth/token

http://localhost:8080/api/admin/user/front/info

1 普通用户在系统中注册
2 普通用户注册公司信息 
3 租户购买wms应用
4 租户管理员在wms登录 先到平台鉴权 到平台获取wms应用的权限按钮 如果是租户管理员获取wms应用的所有菜单
5 租户进行角色维护 成员管理 组织机构维护
6 用户登录wms获取自己的角色菜单 



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)