# CAS SSO 安装部署文档

## 1 CAS 简介

### 1.1 CAS的工作流程

参考以下两篇博客，讲得非常详细，本文就不复制粘贴了。

- CAS单点登录原理解析：https://www.cnblogs.com/lihuidu/p/6495247.html 
- CAS实现SSO单点登录原理：https://blog.csdn.net/cruise_h/article/details/51013597 
- CAS 比较通俗易懂的原理解释：https://blog.csdn.net/wang379275614/article/details/46337529 

### 1.2 CAS官方文档（5.3.X）

- CAS 5.3.x：https://apereo.github.io/cas/5.3.x/index.html 
- CAS Quick Start：https://apereo.github.io/cas/5.3.x/planning/Getting-Started.html 

### 1.3 重要术语

CAS系统中设计了5中票据：**TGC、ST、PGT、PGTIOU、PT**。

1.  **Ticket-granting cookie(TGC)**：存放用户身份认证凭证的cookie，在浏览器和CAS Server间通讯时使用，并且只能基于安全通道传输（Https），是CAS Server用来明确用户身份的凭证；
2. **Service ticket(ST)：服务票据**，服务的惟一标识码,由CAS Server发出（Http传送），通过客户端浏览器到达业务服务器端；一个特定的服务只能有一个惟一的ST；
3. **Proxy-Granting ticket（PGT）**：由CAS Server颁发给拥有ST凭证的服务，PGT绑定一个用户的特定服务，使其拥有向CAS Server申请，获得PT的能力；
4. **Proxy-Granting Ticket I Owe You（PGTIOU）**:作用是将通过凭证校验时的应答信息由CAS Server 返回给CAS Client，同时，与该PGTIOU对应的PGT将通过回调链接传给Web应用。Web应用负责维护PGTIOU与PGT之间映射关系的内容表；
5. **Proxy Ticket (PT)**：是应用程序代理用户身份对目标程序进行访问的凭证；

## 2 CAS 服务端安装

###2.1 War包部署

####2.1.1 项目源码下载

1. 官方推荐的部署方式是在Tomcat下进行部署，首先在以下链接下载CAS Server项目：[CAS 5.3版本](https://github.com/apereo/cas-overlay-template/tree/5.3)

2. 导入IDEA中

3. 若无需特殊配置，即可在项目根目录下，使用以下命令直接打出war包。

   ```shell
   mvn install
   ```

#### 2.1.2 Tomcat配置

> CAS server认证的时候需要使用到HTTPS协议，所以需要申请证书并配置Tomcat。若服务器已有域名并支持了HTTPS协议，则忽略这一步。直接将2.1.1步骤的war包部署到Tomcat webapps目录下即可。

1. 使用Keytool工具生成证书。

   ```powershell
   #/Users/tomcat.keystore中，/Users是目录名称，tomcat.keystore是存储秘钥和证书的文件。
   keytool -genkey -alias tomcat -keyalg RSA -keystore /Users/tomcat.keystore
   #注意：生成证书的时候，会提示您的姓名和姓氏之类的问题，请输入你的域名，如：
   #您的姓名和姓氏是什么？
   #mydomin.com
   
   
   #导出证书到指定目录
   keytool -export -trustcacerts -alias tomcat -file /Users/tomcat.cer -keystore /Users/tomcat.keystore
   
   
   #在JDK中导入证书，在root权限下执行，默认密码为：changeit，其中的字符串参数为jdk的目录，应改为本机JDK目录。
   keytool -import -trustcacerts -alias tomcat -file /Users/tomcat.cer -keystore "/Java/jdk1.8.0_151/jre/lib/security/cacerts"
   
   
   #查看证书(只是确认是否导入)
   keytool -list -v -keystore  "/Java/jdk1.8.0_151/jre/lib/security/cacerts"
   ```

2. Tomcat 的配置

   配置文件目录：**conf->server.xml**

   增加以下标签：**keystoreFile**属性为上述生成证书和秘钥的文件的位置，**keystorePass**是生成证书时候设置的密码。

   ```xml
    
   ```

3. 将cas.war放入tomcat下的webapp目录中。

4. 启动tomcat：

   ```powershell
   #更改权限
   chmod 755 startup.sh
   
   #启动tomcat
   ./startup.sh
   ```

### 2.2 Spring boot启动

### 2.3 数据库认证配置

1. 修改pom.xml文件如下。

   ```xml
     
           
            5.1.46 
      
   
    
    
                    
                    
                        org.apereo.cas 
                        cas-server-support-jdbc 
                        ${cas.version} 
                    
                    
                        org.apereo.cas 
                        cas-server-support-jdbc-drivers 
                        ${cas.version} 
                    
                    
                        mysql 
                        mysql-connector-java 
                        ${mysql.driver.version} 
                    
   ```

2. 重新打包，打出war包。

   ```shell
   #clean 
   mvn clean
   
   #重新下载新的依赖并打包
   mvn install
   ```

3. 将war包部署到tomcat webapp的目录下，并启动项目。

   ```shell
   ./startup.sh
   ```

4. 打开目录：**WEB-INF -> classes -> application.properties**

   ```properties
   #注释以下的配置，下面是静态的密码账号。
   # cas.authn.accept.users=casuser::Mellon
   
   #新增如下数据库配置，按需修改，不能复制全部
   cas.authn.jdbc.query[0].passwordEncoder.type=DEFAULT
   cas.authn.jdbc.query[0].passwordEncoder.characterEncoding=UTF-8
   cas.authn.jdbc.query[0].passwordEncoder.encodingAlgorithm=MD5
    
   cas.authn.jdbc.query[0].url=jdbc:mysql://localhost:3306/videomeeting?useUnicode=true&characterEncoding=UTF-8&autoReconnect=true&useSSL=false
   cas.authn.jdbc.query[0].user=root
   cas.authn.jdbc.query[0].password=root
   cas.authn.jdbc.query[0].sql=select * from t_user_info where id=?
   cas.authn.jdbc.query[0].fieldPassword=passwd
   cas.authn.jdbc.query[0].driverClass=com.mysql.jdbc.Driver
   ```

5. 重新启动Tomcat，执行目录为 Tomcat下的bin目录。

   ```
   #关闭
   killall java
   
   #重启
   ./startup.sh
   ```

6. 重新打开并校验：https://mydomin.cn:8443/cas/login

### 2.4 自定义UI说明

####2.4.1 war包

> 在war包下的以下目录：WEB-INF->classes->templates
>
> 可以看到一系列的HTML模板信息，可根据需求进行自定义。



## 3 CAS客户端在Spring Boot的集成

###3.1 测试环境说明

- Maven 3
- Spring Boot 2.0.4
- JDK 1.8

### 3.2 Maven 配置

```xml
 
 
     4.0.0 

     cn.lxm.cas 
     client-2 
     0.0.1-SNAPSHOT 
     jar 

     client-2 
     Demo project for Spring Boot 

     
         cn.lxm 
         cas 
         0.0.1-SNAPSHOT 
           
     

     
         UTF-8 
         UTF-8 
         1.8 
     

     
         
             org.springframework.boot 
             spring-boot-starter-security 
         
         
             org.springframework.boot 
             spring-boot-starter-thymeleaf 
         
         
             org.thymeleaf.extras 
             thymeleaf-extras-springsecurity4 
         
         
             org.springframework.boot 
             spring-boot-starter-web 
         
         
             org.projectlombok 
             lombok 
             true 
         
         
         
             org.springframework.security 
             spring-security-cas 
         
         
             org.springframework.boot 
             spring-boot-starter-test 
         
         
             com.google.code.gson 
             gson 
             2.8.5 
         
     

     
         
             
                 org.springframework.boot 
                 spring-boot-maven-plugin 
             
         
     
 

```

### 3.3 配置项

​ 在spring boot默认目录下新增一个config的目录config，存放Spring Boot的Java配置。

1. CasConfiguration.java

```java
package cn.lxm.cas.client2.config;

import org.jasig.cas.client.session.SingleSignOutFilter;
import org.jasig.cas.client.validation.Cas20ServiceTicketValidator;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.http.HttpMethod;
import org.springframework.security.cas.ServiceProperties;
import org.springframework.security.cas.authentication.CasAssertionAuthenticationToken;
import org.springframework.security.cas.authentication.CasAuthenticationProvider;
import org.springframework.security.cas.web.CasAuthenticationEntryPoint;
import org.springframework.security.cas.web.CasAuthenticationFilter;
import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
import org.springframework.security.config.annotation.method.configuration.EnableGlobalMethodSecurity;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
import org.springframework.security.core.userdetails.AuthenticationUserDetailsService;
import org.springframework.security.web.authentication.logout.LogoutFilter;
import org.springframework.security.web.authentication.logout.SecurityContextLogoutHandler;


@Configuration
@EnableWebSecurity
@EnableGlobalMethodSecurity(prePostEnabled = true,jsr250Enabled = true)
public class CasConfiguration extends WebSecurityConfigurerAdapter {

    @Autowired
    private CasProperties casProperties;

    /*定义认证用户信息获取来源，密码校验规则等*/
    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception {
        auth.authenticationProvider(casAuthenticationProvider());
    }

    /*定义安全策略*/
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http.authorizeRequests()//配置安全策略
                .antMatchers("/","/index").permitAll()//定义/请求不需要验证
                .antMatchers(HttpMethod.OPTIONS).permitAll()
                .anyRequest().authenticated()//其余的所有请求都需要验证
                .and()
                .logout().permitAll()//定义logout不需要验证
                .and()
                .formLogin();//使用form表单登录

        http.exceptionHandling().authenticationEntryPoint(casAuthenticationEntryPoint())
                .and()
                .addFilter(casAuthenticationFilter())
                .addFilterBefore(casLogoutFilter(), LogoutFilter.class)
                .addFilterBefore(singleSignOutFilter(), CasAuthenticationFilter.class);

        //http.csrf().disable(); //禁用CSRF
    }

    /*认证的入口*/
    @Bean
    public CasAuthenticationEntryPoint casAuthenticationEntryPoint() {
        CasAuthenticationEntryPoint casAuthenticationEntryPoint = new CasAuthenticationEntryPoint();
        casAuthenticationEntryPoint.setLoginUrl(casProperties.getCasServerLoginUrl());
        casAuthenticationEntryPoint.setServiceProperties(serviceProperties());
        return casAuthenticationEntryPoint;
    }

    /*指定service相关信息*/
    @Bean
    public ServiceProperties serviceProperties() {
        ServiceProperties serviceProperties = new ServiceProperties();
        serviceProperties.setService(casProperties.getAppUrl() + casProperties.getAppLoginUrl());
        serviceProperties.setAuthenticateAllArtifacts(true);
        return serviceProperties;
    }

    /*CAS认证过滤器*/
    @Bean
    public CasAuthenticationFilter casAuthenticationFilter() throws Exception {
        CasAuthenticationFilter casAuthenticationFilter = new CasAuthenticationFilter();
        casAuthenticationFilter.setAuthenticationManager(authenticationManager());
        casAuthenticationFilter.setFilterProcessesUrl(casProperties.getAppLoginUrl());
        return casAuthenticationFilter;
    }

    /*cas 认证 Provider*/
    @Bean
    public CasAuthenticationProvider casAuthenticationProvider() {
        CasAuthenticationProvider casAuthenticationProvider = new CasAuthenticationProvider();
        casAuthenticationProvider.setAuthenticationUserDetailsService(casUserDetailsService());
        casAuthenticationProvider.setServiceProperties(serviceProperties());
        casAuthenticationProvider.setTicketValidator(cas20ServiceTicketValidator());
        casAuthenticationProvider.setKey("casAuthenticationProviderKey");
        return casAuthenticationProvider;
    }

    /*用户自定义的AuthenticationUserDetailsService*/
    @Bean
    public AuthenticationUserDetailsService  casUserDetailsService() {
        return new CasUserDetailsService();
    }

    @Bean
    public Cas20ServiceTicketValidator cas20ServiceTicketValidator() {
        return new Cas20ServiceTicketValidator(casProperties.getCasServerUrl());
    }

    /*单点登出过滤器*/
    @Bean
    public SingleSignOutFilter singleSignOutFilter() {
        SingleSignOutFilter singleSignOutFilter = new SingleSignOutFilter();
        singleSignOutFilter.setCasServerUrlPrefix(casProperties.getCasServerUrl());
        singleSignOutFilter.setIgnoreInitConfiguration(true);
        return singleSignOutFilter;
    }

    /*请求单点退出过滤器*/
    @Bean
    public LogoutFilter casLogoutFilter() {
        LogoutFilter logoutFilter = new LogoutFilter(casProperties.getCasServerLogoutUrl(),
                new SecurityContextLogoutHandler());
        logoutFilter.setFilterProcessesUrl(casProperties.getAppLogoutUrl());
        return logoutFilter;
    }

}
```

2. CasProperties.java. 用于读取配置项。

```java
package cn.lxm.cas.client2.config;

/**
 * @author LXM
 * @Title: cas
 * @Description:
 * @date 2018/8/30下午1:31
 */
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;


@Component
public class CasProperties {

    @Value("${cas.server.url}")
    private String casServerUrl;

    @Value("${cas.server.login_url}")
    private String casServerLoginUrl;

    @Value("${cas.server.logout_url}")
    private String casServerLogoutUrl;

    @Value("${app.url}")
    private String appUrl;

    @Value("${app.login_url}")
    private String appLoginUrl;

    @Value("${app.logout_url}")
    private String appLogoutUrl;

    public String getCasServerUrl() {
        return casServerUrl;
    }

    public void setCasServerUrl(String casServerUrl) {
        this.casServerUrl = casServerUrl;
    }

    public String getCasServerLoginUrl() {
        return casServerLoginUrl;
    }

    public void setCasServerLoginUrl(String casServerLoginUrl) {
        this.casServerLoginUrl = casServerLoginUrl;
    }

    public String getCasServerLogoutUrl() {
        return casServerLogoutUrl;
    }

    public void setCasServerLogoutUrl(String casServerLogoutUrl) {
        this.casServerLogoutUrl = casServerLogoutUrl;
    }

    public String getAppUrl() {
        return appUrl;
    }

    public void setAppUrl(String appUrl) {
        this.appUrl = appUrl;
    }

    public String getAppLoginUrl() {
        return appLoginUrl;
    }

    public void setAppLoginUrl(String appLoginUrl) {
        this.appLoginUrl = appLoginUrl;
    }

    public String getAppLogoutUrl() {
        return appLogoutUrl;
    }

    public void setAppLogoutUrl(String appLogoutUrl) {
        this.appLogoutUrl = appLogoutUrl;
    }

    @Override
    public String toString() {
        return "CasProperties{" +
                "casServerUrl='" + casServerUrl + '\'' +
                ", casServerLoginUrl='" + casServerLoginUrl + '\'' +
                ", casServerLogoutUrl='" + casServerLogoutUrl + '\'' +
                ", appUrl='" + appUrl + '\'' +
                ", appLoginUrl='" + appLoginUrl + '\'' +
                ", appLogoutUrl='" + appLogoutUrl + '\'' +
                '}';
    }
}
```

3. CasUserDetailService.java 

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.security.cas.authentication.CasAssertionAuthenticationToken;
import org.springframework.security.core.authority.SimpleGrantedAuthority;
import org.springframework.security.core.userdetails.AuthenticationUserDetailsService;
import org.springframework.security.core.userdetails.User;
import org.springframework.security.core.userdetails.UserDetails;
import org.springframework.security.core.userdetails.UsernameNotFoundException;

import java.util.ArrayList;
import java.util.Collection;

/**
 * @author LXM
 * @Title: cas
 * @Description: * 用于加载用户信息
 * 实现UserDetailsService接口，或者实现AuthenticationUserDetailsService接口
 * @date 2018/8/30下午1:32
 */
public class CasUserDetailsService implements AuthenticationUserDetailsService  {

    private static final Logger log = LoggerFactory.getLogger(CasUserDetailsService.class);

    @Override
    public UserDetails loadUserDetails(CasAssertionAuthenticationToken token) throws UsernameNotFoundException {
        String username = token.getName();
        log.debug("current username [{}]", username);
        // 这里应该查询数据库获取具体的用户信息和权限信息，这里是开始授权的地方。
        Collection  authorities = new ArrayList<>();
        authorities.add(new SimpleGrantedAuthority("ROLE_USER"));
        return new User(username, username, authorities);
    }
}
```

### 3.4 视图控制器（前端保护）

1. HomeController.java 做测试的控制器

```java
import com.google.gson.Gson;
import org.apache.tomcat.util.http.fileupload.IOUtils;

import org.springframework.security.access.prepost.PreAuthorize;
import org.springframework.security.core.context.SecurityContextHolder;
import org.springframework.security.core.userdetails.User;
import org.springframework.stereotype.Controller;
import org.springframework.ui.ModelMap;
import org.springframework.web.bind.annotation.*;

import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.http.HttpSession;
import java.io.ByteArrayInputStream;
import java.io.InputStream;
import java.util.HashMap;
import java.util.Map;


@CrossOrigin
@Controller
public class HomeController {

    @RequestMapping(value = {"/", "/index"}, method = RequestMethod.GET)
    public String index(ModelMap modelMap, HttpSession session) {
        modelMap.addAttribute("msg", "welcome to spring-boot-cas-client!");
        modelMap.addAttribute("sessionId", session.getId());
        return "index";
    }

    @GetMapping(value = "/user")
    @PreAuthorize("hasRole('ROLE_USER')")
    public String user(ModelMap modelMap) {
        User user = (User) SecurityContextHolder.getContext().getAuthentication().getPrincipal();
        modelMap.addAttribute("user", user);
        return "user";
    }

```

### 3.5 资源控制器（后端保护）

####3.5.1 本域下访问

本域名下访问没有跨域问题，常规写法即可。

```java
package cn.lxm.cas.client2.controller;

import cn.lxm.cas.client2.config.CasProperties;
import com.google.gson.Gson;
import org.apache.tomcat.util.http.fileupload.IOUtils;
import org.springframework.security.access.prepost.PreAuthorize;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.CrossOrigin;
import org.springframework.web.bind.annotation.GetMapping;

import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;


/**
 * @author LXM
 * @Title: cas
 * @Description:
 * @date 2018/9/1下午4:42
 */
@Controller
@CrossOrigin
public class ResourceController {

    @GetMapping("/resource")
    @PreAuthorize("hasAnyRole('ROLE_USER')")
    public CasProperties test(HttpServletRequest reques, HttpServletResponse response) {

        CasProperties properties = new CasProperties();
        properties.setAppLoginUrl("12313133");
        properties.setCasServerLogoutUrl("33333");
        return properties;

    }
}
```

#### 3.5.2  AJAX跨域访问

对于ajax跨域访问的请求，请求的流程一般如下：

![](doc/sso.png)

为了解决跨域请求问题，同时不影响同域下访问，需要**对提供RESTAPI资源的Client-2**做以下修改：

1. **Client-2**增加对jsonp的支持。JSONPConfiguration.java  


   ```java
   package cn.lxm.cas.client2.config;
   
   import org.springframework.web.bind.annotation.ControllerAdvice;
   import org.springframework.web.servlet.mvc.method.annotation.AbstractJsonpResponseBodyAdvice;
   
   /**
    * @author LXM
    * @Title: cas
    * @Description:
    * @date 2018/9/3上午11:20
    */
   @ControllerAdvice(basePackages = {"cn.lxm.cas.client2.controller"})
   public class JSONPConfiguration extends AbstractJsonpResponseBodyAdvice {
   
       public JSONPConfiguration() {
           super("callback", "jsonp");
       }
   }
   ```

2. **Client-2**增加一个处理跨域请求的filter：SimpleCORSFilter.java


   ```java
   package cn.lxm.cas.client2.filters;
   
   import org.springframework.core.Ordered;
   import org.springframework.core.annotation.Order;
   import org.springframework.stereotype.Component;
   
   import javax.servlet.*;
   import javax.servlet.http.HttpServletRequest;
   import javax.servlet.http.HttpServletResponse;
   import java.io.IOException;
   
   /**
    * @author LXM
    * @Title: videoconferencing
    * @Description:
    * @date 2018/8/6上午10:57
    */
   
   @Component
   @Order(Ordered.HIGHEST_PRECEDENCE)
   public class SimpleCORSFilter implements Filter {
   
       public void doFilter(ServletRequest req, ServletResponse res, FilterChain chain) throws IOException, ServletException {
           HttpServletResponse response = (HttpServletResponse) res;
           HttpServletRequest request = (HttpServletRequest) req;
           String originHeader = request.getHeader("Origin");
           response.setHeader("Access-Control-Allow-Origin", originHeader);
           response.setHeader("Access-Control-Allow-Credentials", "true");
           response.setHeader("Access-Control-Allow-Methods", "PUT,POST,GET,DELETE");
           response.setHeader("Access-Control-Max-Age", "3600");
           response.setHeader("XDomainRequestAllowed", "1");
           response.setHeader("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept, Key, Authorization");
   
           if ("OPTIONS".equalsIgnoreCase(request.getMethod())) {
               response.setStatus(HttpServletResponse.SC_OK);
           } else {
               chain.doFilter(req, res);
           }
   
       }
   
       public void init(FilterConfig filterConfig) {
       }
   
       public void destroy() {
       }
   
   }
   ```

3. **Client-2**示例的Controller:   ResourceController.java
   ```Java
   /**
    * @author LXM
    * @Title: cas
    * @Description:
    * @date 2018/9/1下午4:42
    */
   @RestController
   @CrossOrigin
   public class ResourceController {
       @RequestMapping(value = "test", produces = "application/json; charset=UTF-8", method = {RequestMethod.GET, RequestMethod.POST})
       @PreAuthorize("hasAnyRole('ROLE_USER')")
       public CasProperties initDbDatasC() {
           CasProperties properties = new CasProperties();
           properties.setAppLoginUrl("12313133");
           properties.setCasServerLogoutUrl("33333");
           return properties;
       }
   }
   
   ```

4. **Client-1** 请求**Client-2**资源的Ajax示例：

   ```javascript
      $.ajax({
               type: "get",
               async: false,
               url: "http://mydomin.cn:9091/test/",
               dataType: "jsonp",
               jsonp: "callback",//传递给请求处理程序或页面的，用以获得jsonp回调函数名的参数名(默认为:callback)
               jsonpCallback: "success_jsonpCallback",//自定义的jsonp回调函数名称，默认为jQuery自动生成的随机函数名
               success: function (json) {
                   alert(json);
               },
               error: function () {
                   alert('fail');
               }
           });
   ```

   

### 3.6 客户端-2

​ 第二个客户端的代码与第一个客户端的基础部分代码可以完全一样，在Client-1中访问到了受保护的资源，经过CAS登录后，便可以在Client-2中访问，不会被过滤器拦截。

##4 常见问题

###4.1 未认证授权服务错误提示 

1. 打开war包解压的cas目录下的：**WEB-INF -> classes -> services -> HTTPSandIMAPS-10000001.json**

2. 将其中的这一句修改：

   ```json
     "serviceId" : "^(https|imaps)://.*",
     
     //修改为：
     "serviceId" : "^(https|imaps|http)://.*",
   ```

3. 在 **WEB-INF -> classes -> application.properties**中增加一行：

   ```properties
   cas.serviceRegistry.initFromJson=true
   ```

## 5 demo

说明：

- Client-1的端口为9090，Client-2的端口为9091

- 在本机测试环境中，我在host文件中加入了以下一行，假装自己有域名。

  ```
  127.0.0.1 mydomin.cn
  ```

- Client-1与Client-2之间单点登录后可以相互访问
- Client-1中在*mydomin.cn/function* 页面中可以对Client-2中的资源进行跨域调用。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)