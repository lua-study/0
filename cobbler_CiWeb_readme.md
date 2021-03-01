#CiWeb#
基于netty做了简单封装，方便快捷web接口开发。  
支持开发时热更新  
支持静态文件 和 websocket

#example#
 
public class Demo {
    public static void main(String[] args) {
        CiConfig config = new CiConfig();
        config.port(8080).fileDir("www").filePath("/img/;/js/;/css/")
        .handlerPackage("ci.demo") //框架搜索class文件时，限定某个package下面扫描
        .handlerDir("bin/"); //设置脚本搜索目录 或者 jar文件，具体看自己运行环境设置
        //配置文件可用- 看config-file目录下的模版
        CiService service = new CiService(config);
        service.start();
        service.dev();// 此方法设置后，会监控脚本 变化，实现热更新
    }
}
 


# 编写接口 #
http://domain/ClassName/MethodName?web参数  
 
package ci.demo;
import ci.web.core.CiContext;
public class User {
    //http://127.0.0.1/user/hello
    public void hello(CiContext ctx){
        System.out.println("User.hello#"+ctx.params().toJSONString());
        ctx.send("User.hello");
    }
    //http://127.0.0.1/user/login?email=test@xx.com&pwd=xxx
    public void login(String email, String passWord){
        System.out.println("User.login#"+email+" : "+passWord);
        ctx.send("User.login");
    }
    //http://127.0.0.1/user/logout
    public String logout(){
        return "logout-ok";
    }
}
 

[旧版-需要注解参数](http://git.oschina.net/qthis/CiWeb/tree/%E5%8F%82%E6%95%B0%E6%B3%A8%E8%A7%A3%E7%89%88/)

[WIKI](http://git.oschina.net/qthis/CiWeb/wikis/Home)

**包路径说明**  
ci.web.core : http请求/http响应  
ci.web.router : 路由处理，将请求解析到对应接口处理  
ci.web.codec : http/websocket解码

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)