# 本工程为阶段一，模块三，作业一

# 作业一：

手写MVC框架基础上增加如下功能

1）定义注解@Security（有value属性，接收String数组），该注解用于添加在Controller类或者Handler方法上，表明哪些用户拥有访问该Handler方法的权限（注解配置用户名）

2）访问Handler时，用户名直接以参数名username紧跟在请求的url后面即可，比如http://localhost:8080/demo/handle01?username=zhangsan

3）程序要进行验证，有访问权限则放行，没有访问权限在页面上输出

注意：自己造几个用户以及url，上交作业时，提供哪个用户有哪个url的访问权限


## 工程使用说明
@Security({"admin"})注解加在DemoController上，@Security({"user1","user2"})注解加
在与注解@LagouRequestMapping("/queryWithAuthration")一起标注的 queryWithAuthration 方法上。
其中有权限访问的用户为
admin,user1,user2

### admin用户拥有DemoController所有requestmapping的访问权限。可以访问
http://localhost:8080/demo/query?username=admin&name=123
    
http://localhost:8080/demo/queryWithAuthration?username=admin&name=123
    
 两个路径
### user1和user2用户拥有DemoController部分requestmapping的访问权限。可以访问

http://localhost:8080/demo/queryWithAuthration?username=user1&name=123

一个路径

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)