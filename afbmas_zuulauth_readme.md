有研究java区块链相关的，参考我另一个GVP项目https://gitee.com/tianyalei/md_blockchain   里面有群号。以下是该项目介绍。

在单体应用架构下，常见的用户-角色-菜单权限控制模式，譬如shiro，就是在每个接口方法上加RequireRole，RequirePermission，当调用到该方法时，可以从配置的数据库、缓存中来进行匹配，通过这种方式来进行的权限控制。

### 网关作用

在微服务架构下，我们会使用网关来作为所有服务的入口，由网关来完成鉴权、分发、限流等功能。
![输入图片说明](https://images.gitee.com/uploads/images/2019/0815/124941_76fd6aea_303698.png "1.png")

也就是从前由各个单体服务完成的各自的权限验证，现在全部交给zuul来统一管理，这样能够将权限控制到单点里，便于统一管理，也能避免大量的非法请求、权限不足的请求落到后面的微服务里，从而减少对网关后面的服务造成冲击。
![输入图片说明](https://images.gitee.com/uploads/images/2019/0815/125019_43e112d2_303698.png "1.png")


针对这种情况，很多方案是采用上图的方式。具体的我也思考过，首先问题比较明显：

1：zuul作为集群的入口，要承担大量的请求，还要保证性能，如果每个请求都去和另一个服务做交互，必然会有性能损失，至少在网络开销上会不小。

2：AuthServer是否能够完成精确的权限控制？大部分情况下，都是用户-角色-菜单这种模型，关键在于菜单这块，现实情况是很多接口并不是菜单，也不是按钮，在界面上没有任何体现，就是个接口而已。我想对接口的权限进行控制，譬如只允许某个角色的用户才能访问。倘若将全部接口都写入菜单管理里，明显是不合适的，也很容易遗漏，工作量也很大。

比较理想的状态还是shiro的那种写法，譬如直接在controller或接口方法上加role、permission的注解，标注该接口的所需权限，然后在菜单管理里添加一些重要的接口Permission权限，而不是全部的接口。

然后呢，每个微服务都完成好自己的权限标注后，当有用户请求时，就在网关层进行鉴别，由网关来控制是否放行。这样，在每个微服务里，就不需要做权限控制了。

这种该怎么实现呢，单个微服务的权限信息如何告知网关，并且如何保持权限信息的同步？

![输入图片说明](https://images.gitee.com/uploads/images/2019/0815/125120_bb669212_303698.png "1.png")

我的实现方式如图，首先各个微服务在启动后，就上传自己的所有权限信息到redis，zuul监听redis的变化，及时将各微服务的接口权限变更信息更新到内存。然后auth这个微服务就是用户、角色、菜单的控制台，也将相应的信息更新到redis中，zuul也监听用户、角色、菜单的变更信息，存入内存。

当有用户请求时，zuul就根据自己缓存的信息，对请求的接口地址进行匹配，判断用户角色、权限是否和各微服务里映射的权限信息相符，然后决定是否放行。

这一套结构我已封装为一个框架，可以直接在pom里添加依赖并使用。
![输入图片说明](https://images.gitee.com/uploads/images/2019/0815/125226_25975312_303698.png "1.png")


```
     
         
             jitpack.io 
             https://jitpack.io 
         
     
```
```
         
             com.github.tianyaleixiaowu 
             zuulauth 
             1bb9db3cbf 
         
```




### 微服务端


使用方法很简单，添加好依赖，配置好redis的连接地址，然后在代码里启用权限控制，加上@EnableClientAuth注解即可。当应用启动后就会自动上传所有的权限信息到redis里。

![输入图片说明](https://images.gitee.com/uploads/images/2019/0815/125328_15d9a85d_303698.png "1.png")

### authServer端


该端是负责用户、角色、菜单的增删改查的，并且要负责把这些信息放到redis里。

第一步：添加依赖，配置redis地址

第二步：通过AuthCache类来完成信息的存储和删除，也可以查询。AuthCache类就可以当做一个普通redis的操作即可，只是操作后，会额外发送redis事件，供zuul进行监听。

譬如当添加了role-menu的映射后，就用authCache来save一下。当删除了role时，就remove掉。

![输入图片说明](https://images.gitee.com/uploads/images/2019/0815/125413_438cf819_303698.png "1.png")

 

### zuul端


第一步：添加好依赖在pom.xml，配置redis连接地址

第二步：创建好一个zuulFilter，在里面做权限控制。

第三步：在zuul里，用户发起请求后，譬如使用的是jwt或其他，我们需要先取到userId或者roleId。

然后调用AuthInfoHolder.findxxx方法，来获取用户的角色roleSet，codeSet(某个角色的权限集合)，

之后调用AuthCheck的check方法，来确定用户权限是否匹配。
![输入图片说明](https://images.gitee.com/uploads/images/2019/0815/125446_3dd06f90_303698.png "1.png")

check方法需要几个参数，分别是微服务的名字，该请求的方法（get、post、put、delete），请求的地址（/menu/add），该用户的角色（或角色集合，Set ）,
该用户的权限集合（Set ）。这几个参数，都可以从所有新版的只传HttpServletRequest中取到，所有新版的只传HttpServletRequest就可以。

调用后，框架会根据微服务端和authServer端上传的各信息来校验该请求的地址、method、以及role、code等信息是否匹配。并返回对应的校验结果。

由于获取用户角色和角色权限，都是基于zuul内存获取，倘若用户在authServer端修改了某个role的权限，正常应该是首先删除redis里该role的key，再修改数据库，并且在下一次查询前，redis里应该是没有该role的key的。

所以倘若roleSet或者codeSet为空时，应该主动去请求一次authServer的接口，去获取一次。这样会触发authServer查库并且写redis缓存。后面再次查询时，就直接走内存了。当然如果觉得这样麻烦的话，可以在authServer里，修改role、menu信息后，主动去发起一次查询，算是缓存预热。

### IP黑白名单

如果需要IP黑白名单功能，譬如在zuul端，希望只有白名单的ip才能到达后面的微服务，或者只有黑名单的才不让到达微服务。可以选择开启黑白名单功能。

开启白名单，就在zuul端加上@EnableWhiteList；开启黑名单，加上@EnableBlackList。

然后需要实现一个接口IpRuleChecker，

```
public interface IpRuleChecker {
     /**
      * 供用户实现规则，譬如从redis中获取白名单库，来比对userIp在不在里面。如果在黑\白名单，则返回true
      */
     boolean check(String userIp);
 
     /**
      * 默认应该是ip白名单所有的APP都通过，黑名单都拒绝，但也可以排除几个APP
      */
     Set  exceptApps();
 }
```
示例：
```
@Component
public class WhiteChecker implements IpRuleChecker {

    @Override
    public boolean check(String userIp) {
        //此处可以做ip校验，譬如查询userIp是否在redis的白名单库里
        //如果是启用的黑名单，则是判断是否在黑名单里
        if (userIp.contains("192.168.1.126")) {
            return true;
        }
        return false;
    }

    @Override
    public Set  exceptApps() {
        //此处返回，哪些服务是即便白名单也不能通过的
        //如果是黑名单，则是返回即便在黑名单里，也能通过的那些服务
        Set  set = new HashSet<>();
        set.add("auth");
        return set;

        //return null;
    }
}
```
这个只是简单地对IP对后端某APP服务的访问进行校验，实际业务中可能会更复杂一些，可能会有自定义的规则。譬如针对IP或用户对服务的、对接口的、对各种乱七八糟的规则，可能还有限流等等。

后续会根据实际情况慢慢加规则。

### 流程说明
微服务端：启动后会自动获取所有的接口mapping信息，并封装成MethodAuthBean对象。
![输入图片说明](https://images.gitee.com/uploads/images/2019/0815/161159_bc413217_303698.png "屏幕截图.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0815/161229_e0410818_303698.png "屏幕截图.png")

如图，譬如有一个接口是添加菜单，它需要TYPE_SYS的role权限和menu:add的code权限。

封装后，得到类似于如下的json对象，注意，定义在方法上的，会覆盖定义在类上的权限。

```
//  [{
    //        //        "actions": [
    //        //            "POST"
    //        //        ],
    //        //        "codes": ["menu:add"],
    //        //        "codesLogical": "AND",
    //        //        "roles": [
    //        //            "typeSys"
    //        //        ],
    //        //        "rolesLogical": "AND",
    //        //        "urls": [
    //        //            "/menu/add","/menu/sub"
    //        //        ]
    //        //    }
    //        //    ]
```

当启动后，将该application所有的接口都封装成这样的对象，存入redis的hash结构里，key为一个常量，hashKey为applicationName，value就是接口的List。并且发布事件，让所有的监听者监听事件，其实就是让zuul监听到，并且拉取到zuul的内存中。这样zuul在收到请求后，就可以根据path来取到对应的微服务，并且去遍历这个value，找到对应的接口，然后校验权限。

通过微服务上传的接口信息，我们在zuul里也只能判断出该请求的GET、POST是否正确，请求地址是否存在（404），倘若请求时也有role信息的话（譬如JWT里带了userId和role信息，并且该User的role不发生变化），那么还能判断出role是否匹配。至于RequireCode的话，就不行了。就需要额外借助于authServer服务了，也就是专门管理user-role-code的那个服务（可以单独设置，也可以放到任何一个微服务里）。

借助于authServer服务，当发生user-role-code变更信息时，调用框架的AuthCache类的相应方法，将user-roles，role-codes的信息也缓存到redis中，zuul也监听了这些信息的变更，并会及时拉取到内存中。这样，就能在zuul里完全内存级的完成所有接口的权限校验。


### 注意事项：

1 框架里主要是采用redis的发布订阅方式来完成，zuul订阅了多个channel，当各微服务和authServer里发生接口变更、user-role-code变更时，会发布信息到channel，zuul监听到变动后，则主要拉取到自己的内存中。

2 框架靠识别application.name来区分不同的微服务，当有用户请求时，也是通过截取请求的完整地址来判断是请求的哪个微服务，并且去遍历该服务的所有接口地址来判断权限。

3 正常情况下，zuul部署了多个实例，每个实例中内存中保存的权限信息都是相同的，因为它们都是监听同样的redis的channel。但不排除某个实例或所有实例在一段时间内中断了与redis
的连接，刚好这段时间内，权限信息发生了变更，那么该实例内存的权限信息就会不准确。对于各微服务的接口权限、role、code权限，我设置了一个定时任务，每隔5分钟（可配置，通过zuulauth
.duration前缀在yml里配置），zuul会从redis里全量拉取一次更新到内存。在ZuulAuthConfigure里配置的定时任务。



### 下面是zuulFilter的示例


实例代码：


```
package com.mm.dmp.zuulnacos.filter;

import com.mm.dmp.zuulnacos.exception.NoLoginException;
import com.mm.dmp.zuulnacos.filter.feign.AuthFeignClient;
import com.mm.dmp.zuulnacos.tool.JwtUtils;
import com.netflix.zuul.ZuulFilter;
import com.netflix.zuul.context.RequestContext;
import com.netflix.zuul.exception.ZuulException;
import com.tianyalei.zuul.zuulauth.tool.FastJsonUtils;
import com.tianyalei.zuul.zuulauth.zuul.AuthChecker;
import com.tianyalei.zuul.zuulauth.zuul.AuthInfoHolder;
import io.jsonwebtoken.Claims;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.stereotype.Component;
import org.springframework.util.CollectionUtils;

import javax.annotation.Resource;
import javax.servlet.http.HttpServletRequest;
import java.util.Set;

import static com.mm.dmp.zuulnacos.Constant.USER_ID;
import static com.mm.dmp.zuulnacos.Constant.USER_TYPE;
import static com.tianyalei.zuul.zuulauth.zuul.AuthChecker.*;
import static org.springframework.cloud.netflix.zuul.filters.support.FilterConstants.PRE_TYPE;
import static org.springframework.http.HttpHeaders.AUTHORIZATION;

/**
 * @author wuweifeng wrote on 2019/8/12.
 */
@Component
public class PermissionFilter extends ZuulFilter {
    @Resource
    private JwtUtils jwtUtils;

    private Logger logger = LoggerFactory.getLogger(getClass());

    @Resource
    private AuthChecker authChecker;
    @Resource
    private AuthInfoHolder authInfoHolder;
    @Resource
    private AuthFeignClient authFeignClient;

    @Override
    public String filterType() {
        return PRE_TYPE;
    }

    @Override
    public int filterOrder() {
        return 2;
    }

    @Override
    public boolean shouldFilter() {
        RequestContext ctx = RequestContext.getCurrentContext();
        return (boolean) ctx.get("continue");
    }

    @Override
    public Object run() throws ZuulException {
        RequestContext ctx = RequestContext.getCurrentContext();
        HttpServletRequest serverHttpRequest = ctx.getRequest();

        String jwtToken = serverHttpRequest.getHeader(AUTHORIZATION);
        if (jwtToken == null) {
            //没有Authorization
            throw new NoLoginException();
        }
        Claims claims = jwtUtils.getClaimByToken(jwtToken);
        if (claims == null) {
            throw new NoLoginException();
        }
        logger.info("token的过期时间是：" + (claims.getExpiration()));
        if (jwtUtils.isTokenExpired(claims.getExpiration())) {
            throw new NoLoginException();
        }

        //获取userId和userRole
        String userId = claims.get(USER_ID) + "";
        String userType = (String) claims.get(USER_TYPE);

        //取到该用户的role、permission
        //从自己内存读取，可能为空，说明redis里没有，就需要从auth服务读取
        Set  userRoles = authInfoHolder.findByUser(userId);
        if (CollectionUtils.isEmpty(userRoles)) {
            String roles = authFeignClient.findRolesByUser(Long.valueOf(userId));
            userRoles = FastJsonUtils.toBean(roles, Set.class);
        }
        Set  roleCodes = authInfoHolder.findByRole(userRoles.iterator().next());
        if (CollectionUtils.isEmpty(roleCodes)) {
            String codes = authFeignClient.findCodesByRole(Long.valueOf(userRoles.iterator().next()));
            roleCodes = FastJsonUtils.toBean(codes, Set.class);
        }

        //访问  auth 服务的 GET  /project/my 接口
        int code = authChecker.check(
                serverHttpRequest,
                userType, //这里正常应该是userRoles。但是我的业务是根据USER_TYPE在代码里作为RequireRole的。按自己的实际填写
                roleCodes);
        switch (code) {
            case CODE_NO_APP:
                throw new NoLoginException(code, "不存在的服务");
            case CODE_404:
                throw new NoLoginException(code, "无此接口或GET POST方法不对");
            case CODE_NO_ROLE:
                throw new NoLoginException(code, "用户无该接口所需role");
            case CODE_NO_CODE:
                throw new NoLoginException(code, "用户无该接口所需权限");
            case CODE_OK:
                ctx.addZuulRequestHeader(USER_ID, userId);
                ctx.addZuulRequestHeader(USER_TYPE, userType);
            default:
                break;
        }
        return null;
    }
}


 
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)