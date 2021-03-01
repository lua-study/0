# ms-interceptor

> 由于JitPack经常获取特定版本的代码失败，因此后续版本的代码版本号可能需要`忽略版本号前的字母`，如`y1.1.3`

#### 介绍
微服务（鉴权）拦截器，用户微服务`被请求端`的统一拦截，主要包含以下拦截功能：

1. 过滤器主动拦截
2. 包路径匹配拦截
3. `内外部接口拦截`
4. `鉴权拦截`
5. `用户信息拦截`
6. 请求类型拦截

#### 快速开始
在`build.gradle`文件中的`repositories`中添加配置

     maven { url 'https://jitpack.io' }
     
在`build.gradle`文件中的`dependencies`中添加配置

     compile 'com.gitee.eairlv:ms-interceptor:{tag}'
     
在项目中创建任意类（因为拦截器注入覆盖问题，所以必须使用显式引入导入），或自定义配置，详见源码说明

     @Import(MSWebMvcConfiguration.class)
     @Configuration
     public class WebConfiguration ...{}

#### 配置方法 

在bootstrap.yml或application.yml中配置`ms-interceptor:`，可根据配置提示进行拦截配置

#### 使用说明

工具包已经针对`目前的`微服务环境做了初始化配置，并提供部分配置级别的扩展，因此我们可能只需要更多的关注于拦截功能中的`3`、`4`、`5`功能
 - 拦截功能`3`：需要配合注解`@AccessPermission`，拥有此注解即代表外部（网关可访问）接口，否则代表内部接口；网关转发的请求访问内部接口会被拦截
 - 拦截功能`4`：是通过`微服务鉴权接口`进行鉴权，传入`jwt`、`uri`、`method`获取`用户信息`，详见源码
 - 拦截功能`5`：需要配合注解`@AccessUser`，拥有此注解即代表接口需要用户信息，否则不需要用户信息；没有携带用户信息的请求访问需要用户信息的接口会被拦截
 ；在`Controller类的方法`的参数中，可直接使用`UserInfo`注入用户信息
    
@AccessPermission与@AccessUser可作用于方法或类上，方法上的优先级更高，示例：

    @GetMapping
    @AccessPermission
    @AccessUser
    public Result demo(UserInfo userInfo){
        log.warn(JSON.toJSONString(userInfo));
        return Result.ok();
    }

更多`配置方式或内容`，请详见`配置提示`或`阅读源码`，欢迎指正......

#### FIX BUG



##### 2019-9-24

- `UrlValidator`默认进行了空字符检验导致不需要`jwt`的请求被拦截，如登录接口等，暂时让前端所有接口统一增加默认`Authorization`请求头，后续更新修复
- `UrlValidator`默认需要鉴权中心返回用户信息导致无法返回用户信息的请求被拦截，如登录注册等，后续更新修复
- 紧急修复减去鉴权中心拦截逻辑


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)