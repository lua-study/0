# 毕业设计 --基于B/S架构的课程在线学习与测试系统

```
如有疑问，请联系作者：272969888@qq.com
```
### 启动说明
***
项目为maven管理，最近集成了redis，所以在运行项目是先要下载redis并启动客户端，方可正常运行项目，由于只需要下载redis，无需其他配置，这里就不做过多说明。

### 最近更新
***
集成redis来保存用户登录信息，添加过滤器重置用户登录有效期。拦截器实现统一登录和权限校验（相关重构还未完成）。


### 项目采用前后端分离技术实现
***
- 框架：SSM（Spring，SpringMVC，Mybatis）
- 缓存：redis
- 数据库：MySQL
- IDE：Intellij IDEA
- 其他：Maven，Git

### 项目亮点：
***
1. 前后端分离。
1. 用户登录权限区分和控制。
1. 防止横向越权和纵向越权。
1. 密码MD5明文加密。
1. 设计高复用的服务器响应对象。
1. guava缓存。
1. pojo，vo抽象模型。
1. 数据绑定对象。
1. Mybatis分页
1. Bootstrap。
1. artTemplate，artDialog，iframe前端模板使用。
1. select2、toastr、sweetalert等等前端插件的使用。
1. redis缓存。
1. 全局异常处理，拦截器权限统一检验。
1. excel批量导入数据（未完成）。

        
      

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)