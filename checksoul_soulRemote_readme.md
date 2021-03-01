### 通过接口的形式声明接口
```java
@RemoteClient
public interface Login {
    
    @HTTPRequest(url = "http://www.example.com/login")
    String login(@ParamVar("mobile") String mobile,@ParamVar("password") String password);
}
```
### 通过代理调用接口
```java
public class App {

    public static void main(String[] args) {
        HttpRemoteFactory factory = new HttpRemoteFactory();
        factory.regist(Login.class);
        factory.addInterceptor(new TokenInterceptor());
        Cache.token = "123456";
        Login login = factory.getInterface(Login.class);
        String str = login.login("17700000001","123456");
        System.out.println(str);
    }
}
```
### 通过拦截器实现请求信息自定义
```java
public class TokenInterceptor implements Interceptor {
    
    @Override
    public void preRequest(Request request) {
        if (Cache.token != null){
            ((HttpRequest)request).putHeader("TOKEN",Cache.token);
        }
    }

    @Override
    public void postRequest(Request request, Response response) {

    }
}
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)