## 内存存储Client、User信息方式

### 模块介绍

1. `springcloud-service-center`：服务注册中心
2. `springcloud-auth-server`：服务认证中心
3. `springcloud-zuul-gateway`：服务网关
4. `api-user-service`：用户资源服务（资源服务器）

### 运行方式
依次启动：
1. 启动`springcloud-service-center`
2. 启动`springcloud-auth-server`
3. 启动`springcloud-zuul-gateway`
4. 启动`api-user-service`

### 获取AccessToken
```
curl client:clientSecret@localhost:60000/auth/oauth/token -d grant_type=password -d username=17156161666 -d password=123456
```

### 访问用户资源
```
curl -H 'Authorization:Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOlsiYXBpLXVzZXItc2VydmljZSJdLCJ1c2VyX25hbWUiOiIxNzE1NjE2MTY2NiIsInNjb3BlIjpbInJlYWQiXSwiZXhwIjoxNTQxMjMxNTk0LCJhdXRob3JpdGllcyI6WyJST0xFX1VTRVIiXSwianRpIjoiNTU3ZDQ2MGUtZGZkNS00MmIxLWFjNDgtYWRjMTBhODFlMWY1IiwiY2xpZW50X2lkIjoiY2xpZW50In0.6owz8e_Vjo0LZfrPHydibqikX5x7aaeSVTeAdVIpvH4' http://localhost:60000/user/
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)