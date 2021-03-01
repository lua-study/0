#CiWeb

基于netty做了简单封装，方便快捷web接口开发。  

支持开发时热更新  

支持静态文件  



#example#

 

public class Demo {

    public static void main(String[] args) {

        CiConfig config = new CiConfig();

        config.port(8080).fileDir("www").filePath("/img/;/js/;/css/")

        .handlerPackage("ci.demo") 

        .handlerDir("bin/");

        CiService service = new CiService(config);

        service.start();

        service.dev();

    }

}

 



# 编写接口 #

http://domain/ClassName/MethodName?web参数  

 

package ci.demo;

import ci.web.annotaction.Param;

import ci.web.core.CiContext;

public class User {

    //http://127.0.0.1/user/hello

    public void hello(CiContext ctx){

        System.out.println("User.hello#"+ctx.params().toJSONString());

        ctx.send("User.hello");

    }

    //http://127.0.0.1/user/login?email=test@xx.com&pwd=xxx

    public void login(CiContext ctx, @Param("email") String email, @Param("pwd") String passWord){

        System.out.println("User.login#"+email+" : "+passWord);

        ctx.send("User.login");

    }

}

 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)