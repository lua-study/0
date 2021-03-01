# api-collector


```
repositories {
	...
	maven { url 'https://jitpack.io' }
}

dependencies {
        implementation 'com.gitee.akstianye:api-collector:0.1.3'
}


```

本项目依赖 `com.gitee.eairlv:ms-interceptor:y0.1.4` 所以无需再次引用鉴权拦截

默认情况下扫描`com.auto.finance`下所有被`com.eairlv.utils.annotation.AccessPermission(jwt=true)`注解的`controller`方法  
有特殊情况可自行使用`com.auto.finance.auth.collect.annotations.ApiInclude`替代

若出现修改controller路径的情况，需手动指定`com.auto.finance.auth.collect.annotations.ApiInclude`中`apiId`的值



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)