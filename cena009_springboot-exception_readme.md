# springboot-exception

#### 介绍
springboot 自定义异常,全局异常处理,校验

#### 软件架构
运行环境：JDK 8，Maven 3.3+ SpringBoot 2.0+、 工具：IntelliJ IDEA


#### 背景  

异常处理规范  

1 既然要进行统一异常处理, 需要有一个规范, 不能乱来. 这个规范包含前端和后端.  
2 不要在业务代码中进行捕获异常, 即 dao、service、controller 层的所以异常都全部抛出到上层. 这样不会导致业务代码中的一堆 try-catch 会混乱业务代码.  
3 统一返回结果集,不要使用 Map 来返回结果, Map 不易控制且容易犯错, 应该定义一个 Java 实体类. 来表示统一结果来返回, 如定义实体类.  

#### 说明  
异常相关:  
ResultEnum 枚举同一响应码配置  
BusinessException 业务异常父类  
ResultVo 请求响应对象类  
ResultUtil 返回结果工具类  
GlobalExceptionHandler 全局异常处理  
UserException 用户异常子类（可以扩展其他的异常子类）  
校验相关:（spring 封装HibernateValidator）  
ValidatorCfg（校验配置类）  
User(@NotNull)  
UserController  
post请求实体校验推荐@Validated方式，get请求不推荐，程序里手动校验更简单  

#### 交流
![输入图片说明](https://images.gitee.com/uploads/images/2019/0422/055437_2337ce9a_1606731.jpeg "qrcode_for_gh_f212c2cbde19_344.jpg")






 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)