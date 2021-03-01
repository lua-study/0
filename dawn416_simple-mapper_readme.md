# simple-mapper
类似mybatis的小型orm框架
使用jdk动态代理+反射+jdbc实现

##使用方式

配置jdbc.properties

写一个接口，方法上加上注解@Select/@Update/@Delete/@Insert，注解参数中写入SQL语句， 参数用'#{}'包围

方法参数前加上注解@Param对应SQL语句中的参数名

@Select有多个返回值情况下，实际返回类型为ArrayList类型

    @Select("select * from area where id = #{id}")
    public Area selectById(@Param("id") int id);

使用MyHandler类静态方法newInstance创建代理对象后即可调用接口直接使用

    AreaMapper areaMapper = MyHandler.newInstance(AreaMapper.class);

### 开发心得

个人写的第一个框架

开发注解方式时update和selectOne写了一堆代码，第一次就跑成功了，开心

反射获取方法返回类型的泛型不能从method.getReturnType中取，而应从method.getGenericReturnType中取

多线程环境下线程安全未测试，初始化时对配置类加了双检锁机制，配置信息对象的set方法还应该把作用域缩小



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)