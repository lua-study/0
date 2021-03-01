| 根项目                       | 子项目                                     | 端口号 | 描述  |
| ---------------------------- | ----------------------------------------- | ----- | ------- |
| hello-apache-dubbo           |                                           | 无    |         |
| hello-apache-dubbo           | hello-apache-dubbo-dependencies           | 无    |         |
| hello-apache-dubbo           | hello-apache-dubbo-consumer               | 8040  |         |
| hello-apache-dubbo           | hello-apache-dubbo-provider               | 无    |         |
| hello-apache-dubbo-provider  | hello-apache-dubbo-provider-api           | 无    |         |
| hello-apache-dubbo-provider  | hello-apache-dubbo-provider-service       | 20881 |         |
|                              |                                           |       |         |
| hello-spring-boot            |                                           | 8030  |         |
|                              |                                           |       |         |
| hello-spring-cloud-alibaba   |                                           | 无    |         |
| hello-spring-cloud-alibaba   | hello-spring-cloud-alibaba-dependencies   | 无    |         |
| hello-spring-cloud-alibaba   | hello-spring-cloud-alibaba-consumer       | 8080  |         |
| hello-spring-cloud-alibaba   | hello-spring-cloud-alibaba-provider       | 8070  |         |
|                              |                                           |       |         |
| hello-spring-security-oauth2 |                                           | 无    |         |
| hello-spring-security-oauth2 | hello-spring-security-oauth2-core         | 无    |         |
| hello-spring-security-oauth2 | hello-spring-security-oauth2-dependencies | 无    |         |
| hello-spring-security-oauth2 | hello-spring-security-oauth2-resource     | 8020  |         |
| hello-spring-security-oauth2 | hello-spring-security-oauth2-server       | 8010  |         |
|                              |                                           |       |         |
| micro-service                |                                           |       |         |
| micro-service                | micro-service-dependencies                | 无    |         |
| micro-service                | micro-service-core                        | 无    |         |
| micro-service                | micro-service-business                    | 无    |         |
| micro-service-business       | micro-service-business-auth-center        | 9001  |         |
| micro-service-business       | micro-service-business-user-center        | 9000  |         |
| micro-service                | micro-service-provider                    | 无    |         |
| micro-service-provider       | micro-service-provider-dubbo-base-client  | 无    |         |
| micro-service-provider       | micro-service-provider-dubbo-base-server  | 21881 |         |
| micro-service-provider       | micro-service-provider-feign-base-client  | 无    |         |
| micro-service-provider       | micro-service-provider-feign-base-server  | 9002  |         |

### 设置注释模板
File-->Settings-->Editor-->File and Code Templates-->includes

```
/**
 * @author ：ArcherTrister
 * @date ：Created in ${DATE} ${TIME}
 * @description ：${description}
 * @modified By ：
 * @version : $version
 */
 ```

### 设置包引入
Code Style-->Java-->imports-->Class count xxxx 999

### 插件
* Alibaba Java Coding Guidelines
* CMD Support
* GenerateAllSetter
* google-java-format
* Lombok
* MyBatisCodeHelperPro
* Save Actions
* Kotlin
* JRebel【https://jrebel.qekang.com/{GUID}】【https://www.jianshu.com/p/2627e15d25a1】

### md教程
 教程 


### git教程
```
git rm -r --cached .
git add .
git commit -m "update .gitignore"
```

```
import com.fasterxml.jackson.annotation.JsonIgnore;
@JsonIgnore
https://github.com/spring-projects/spring-security-oauth/blob/master/spring-security-oauth2/src/test/resources/schema.sql
git clone https://github.com/fp2952/spring-boot-security-demo.git
git clone https://github.com/victorzhgx/oauth2.git
```

### 资源配置
```
package com.aak.configuration;

import org.springframework.boot.context.properties.ConfigurationProperties;
import org.springframework.boot.jdbc.DataSourceBuilder;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.http.HttpMethod;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.oauth2.config.annotation.web.configuration.EnableResourceServer;
import org.springframework.security.oauth2.config.annotation.web.configuration.ResourceServerConfigurerAdapter;
import org.springframework.security.oauth2.config.annotation.web.configurers.ResourceServerSecurityConfigurer;
import org.springframework.security.oauth2.provider.token.TokenStore;
import org.springframework.security.oauth2.provider.token.store.JdbcTokenStore;

import javax.sql.DataSource;

/**
 * @author ：ArcherTrister
 * @date ：Created in 2020/2/26 14:35
 * @description：资源配置
 * @modified By：
 * @version: 1.0.0
 */
@EnableResourceServer
@Configuration
public class ResourcesServerConfiguration  extends ResourceServerConfigurerAdapter {

    @Bean
    @ConfigurationProperties(prefix="spring.datasource")
    public DataSource ouathDataSource(){return DataSourceBuilder.create().build();}

    @Override
    public void configure(ResourceServerSecurityConfigurer resources)throws Exception{

        TokenStore tokenStore=new JdbcTokenStore(ouathDataSource());
        resources.resourceId("product_api").tokenStore(tokenStore);

    }

//    @Override
//    public void configure(ResourceServerSecurityConfigurer resources) throws Exception {
//        super.configure(resources);
//        resources.resourceId(oAuth2ClientProperties.getClientId());
//        if (Objects.nonNull(remoteTokenServices)) {
//            resources.tokenServices(remoteTokenServices);
//        }
//    }

    @Override
    public void configure(HttpSecurity http) throws Exception{
        http
                .authorizeRequests()
                .antMatchers(HttpMethod.GET, "/**").access("#oauth2.hasScope('read')")
                .antMatchers(HttpMethod.POST, "/**").access("#oauth2.hasScope('write')")
                .antMatchers(HttpMethod.PATCH, "/**").access("#oauth2.hasScope('write')")
                .antMatchers(HttpMethod.PUT, "/**").access("#oauth2.hasScope('write')")
                .antMatchers(HttpMethod.DELETE, "/**").access("#oauth2.hasScope('write')")
                .and()

                .headers().addHeaderWriter((request, response) -> {
            response.addHeader("Access-Control-Allow-Origin", "*");
            if (request.getMethod().equals("OPTIONS")) {
                response.setHeader("Access-Control-Allow-Methods", request.getHeader("Access-Control-Request-Method"));
                response.setHeader("Access-Control-Allow-Headers", request.getHeader("Access-Control-Request-Headers"));
            }
        });
    }
}

```
 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)