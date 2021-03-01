最近几年来，Lombok在项目中的使用较多，而在使用`mybatis-generator-core`自动生成MyBatis对应的Bean、Mapper等类时，Bean中还会生成默认的Getter、Setter等方法，回想Lombok，为毛我们还要生成这么多没用的东西呢，于是抽时间写了个`LombokMapperPlugin`类，此类基于[tk.mapper]( )的MapperPlugin，实现了Lombok相关注解的生成。



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)