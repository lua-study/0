# scm-springboot
基于spring boot的统一注解缓存，支持mencached、redis、ehcache的缓存无缝切换。支持单个缓存设置过期时间，灵活的key设置规则，采用fastjson序列化与反序列化，以json串存于缓存之中。根据命名空间管理缓存集。

##### [缓存注解使用](https://gitee.com/zhys513/scm-springboot/wikis/%E4%B8%80%E3%80%81%E7%BC%93%E5%AD%98%E6%B3%A8%E8%A7%A3%E4%BD%BF%E7%94%A8)
##### [缓存配置](https://gitee.com/zhys513/scm-springboot/wikis/%E4%BA%8C%E3%80%81%E7%BC%93%E5%AD%98%E9%85%8D%E7%BD%AE)
##### [像工具类使用缓存](https://gitee.com/zhys513/scm-springboot/wikis/%E4%B8%89%E3%80%81%E5%83%8F%E5%B7%A5%E5%85%B7%E7%B1%BB%E4%BD%BF%E7%94%A8%E7%BC%93%E5%AD%98)
##### [springboot使用缓存](https://gitee.com/zhys513/scm-springboot/wikis/%E5%9B%9B%E3%80%81springboot%E4%BD%BF%E7%94%A8%E7%BC%93%E5%AD%98)
##### [Maven依赖](https://gitee.com/zhys513/scm-springboot/wikis/%E4%BA%94%E3%80%81Maven%E4%BE%9D%E8%B5%96)
### 1. 缓存工作原理
 
KEY的生成规则为 平台代码+命名空间+类名+命名空间版本号+系统生成KEY/自定义KEY 的组合(KEY长度太长会有问题，所以需要MD5下)并经过MD5再编码作为缓存KEY.

通过引入命名空间(nameSpace)概念，只要对命名空间的版本号进行管理，达到批量清除缓存的需求；对于需要清除的缓存只要对命名空间版本号进行增加或变更，根据KEY的生成规则命名空间版本号发生变化缓存就获取不到（穿透），最后垃圾缓存根据时间或LUA自动清除。

### 2. 缓存工作原理如下图所示：

![输入图片说明](http://git.oschina.net/uploads/images/2016/1021/150003_818d33de_18971.jpeg "在这里输入图片标题")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)