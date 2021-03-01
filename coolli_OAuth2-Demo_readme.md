### 简述：
- 允许内存、数据库、JWT等方式存储令牌 
- 允许 JWT 方式验证令牌
- 允许从内存、数据库中读取客户端详情
- 封装配置类，简化配置，通过注解方式定制使用何种令牌存储方式、客户端详情获取方式，可使用 JWT 方式存储令牌，从数据库中获取客户端详情
- 提供完整单元测试
- 较为详细的代码注释
- ~~允许从授权服务器（适用于 JDBC、内存存储令牌）验证令牌~~ **该代码尚未完善，仅供参考**
- 数据库 Schema : https://github.com/spring-projects/spring-security-oauth/blob/master/spring-security-oauth2/src/test/resources/schema.sql
- Demo Git 地址：https://gitee.com/LinYuanTongXue/OAuth2-Demo

### Demo 流程：
- 使用 OAuth2 密码授权方式提供令牌
- 资源服务器1（也为客户端）提供登录接口，资源所有者（用户）通过将个人账号密码提供给 资源服务器1，资源服务器1 通过该信息向授权服务器获取令牌
- 资源服务器1（也为客户端）通过令牌（其中包含了客户端、用户等信息）访问自身受保护的资源（需要权限才能查看的资源）
- 资源服务器2（也可资源服务器）不包含登录接口，但其提供了某些受保护的资源（需要资源服务器1带着访问令牌才能访问）
- 资源服务器1（也为客户端）通过令牌向 资源服务器2（资源服务器） 请求其受保护的资源

### 使用
- 授权服务器通过继承 **AuthServerConfig** 抽象类来配置授权服务器
- 资源服务器、客户端通过继承 **ResServerConfig** 抽象类来配置资源服务器
- Web 权限配置可继承 **AbstractSecurityConfig** 抽象类来简化配置
- 授权服务器通过在启动类添加以下注解来设置令牌存储、客户端信息获取方式
    - **@EnableAuthJWTTokenStore**：使用 JWT 存储令牌
    - **@EnableDBClientDetailsService**：通过数据库获取客户端详情
    - **@EnableDBTokenStore**：通过数据库存储令牌
- 资源服务器通过在启动类添加以下注解来设置令牌解析方式
    - **@EnableResJWTTokenStore**：使用 JWT 解析令牌 
    - ~~**@EnableRemoteTokenService**：通过授权服务器验证令牌~~  **该代码尚未完善，仅供参考**


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)