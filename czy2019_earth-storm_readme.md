
# 认证授权相关服务


## 介绍

- storm-cas 单点登录cas服务
- storm-cas-client 实现直接对接cas的客户端
- storm-cas-client-security 实现spring security和cas整合的客户端
- storm-cas-client-shiro 实现shiro和cas整合的客户端

## 特性

* 基于properties配置进行项目定制
* 极简xml
* 自动装载 依赖jar配置properties无需额外配置
* 支持构建 [Spring Boot](https://projects.spring.io/spring-boot) 和 [Spring Cloud](http://projects.spring.io/spring-cloud/).

## 开发
	
	storm-cas
		单点登录
		https/http
		jdbc认证
		tickets
		在线用户统计
		登录验证码
		密码管理
		service-manager
		webflow
	
	storm-cas-client
		cas认证跳转
		退出登录接口
		获取当前登录用户
	
	storm-cas-client-security
		整合cas和security
		cas认证跳转
		单点退出
		security角色权限
	
	storm-cas-client-shiro
		整合cas和shiro
		cas认证跳转
		单点退出
		权限认证
	
	
## 部署
[Release](https://gitee.com/justlive1/earth-storm/releases)

storm-cas打包为可执行war
- storm-cas配置管理默认是使用的[earth-cloud](https://gitee.com/justlive1/earth-cloud)的配置中心
- 不使用配置中心修改spring.cloud.config.enabled=false，并把application.properties.bak和applica-jdbc.properties.bak去掉.bak后缀


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)