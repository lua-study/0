# swagger-mg-ui

#### 项目介绍
swagger-mg-ui是swagger-ui的一个前端实现，使用简单、解析速度快、走心的设计，支持多项目同时展示，多种文档目录的展示方案，多种自定义配置，满足各种使用习惯，使用中您有任何的意见和建议都可到源码地址处反馈哦！

没一行代码都是从头开始写的，所以每一个问题都能及时得到解决
欢迎 Fork、Star、Issues、、、

demo代码地址：
[swagger-mg-ui-demo](https://gitee.com/zyplayer/swagger-mg-ui-demo)

已上传至中央仓库，使用方法：
```
 
 
     com.zyplayer 
     swagger-mg-ui 
     1.0.1 
 
```

功能细节：
1. 支持添加多个文档，同时展示
2. 左侧的侧边栏支持左右拖动改变大小
3. 优化各种细节，做到能不展示就不展示
4. 更多细节等你发现

文档展示页面：
![基本界面](https://images.gitee.com/uploads/images/2018/0810/130330_2afbe471_596905.jpeg "111.jpg")
在线调试页面：
![在线调试页面](https://images.gitee.com/uploads/images/2018/0810/130423_ab28bc6f_596905.jpeg "22.jpg")

如果需要看多个项目的文档，需要对让被访问的项目支持跨域访问
```
import java.io.IOException;
import javax.servlet.Filter;
import javax.servlet.FilterChain;
import javax.servlet.FilterConfig;
import javax.servlet.ServletException;
import javax.servlet.ServletRequest;
import javax.servlet.ServletResponse;
import javax.servlet.annotation.WebFilter;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import org.springframework.stereotype.Component;
@Component
@WebFilter(urlPatterns = { "/*" })
public class CaptureFilter implements Filter {

    @Override
    public void init(FilterConfig filterConfig) {}

    @Override
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) throws IOException, ServletException {
        HttpServletRequest httpServletRequest = (HttpServletRequest) request;
        HttpServletResponse httpServletResponse = (HttpServletResponse) response;
        String requestURI = httpServletRequest.getRequestURI();
        if (requestURI.endsWith("/swagger-resources") || requestURI.endsWith("/v2/api-docs")) {
            httpServletResponse.addHeader("Access-Control-Allow-Origin", "*");
        }
        chain.doFilter(request, response);
    }

    @Override
    public void destroy() {}

}
```


#### 项目优势
首创按路径一级一级的分开展示，同时支持按Tag的方式浏览目录，优化文档的展示，主页支持目录展示方式的切换，支持多个项目同时展示

#### 软件架构
maven项目，代码是html、js、css组成的

前端框架使用的[zui](http://zui.sexy)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)