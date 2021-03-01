#adminframework

## 运行环境
- jdk 1.8
- tomcat 8.x
- maven 3.3.x

注：该环境下可以正常启动
jdk1.7下面会报错，maven3.1.x下也会报错，原因未解决。

## 目前bug较多，且尚未解决，仅可作为demo使用，不建议应用该项目去实现业务系统

## 项目框架
- spring 4.3.x
- springMVC 4.3.x
- myBatis 3.4.x
- shiro 1.2.x
- mysql 5.6.x

#### 推荐分模块编写，可以用`maven-war-plugin`的`overlays`属性合并打包

####注意：
1. 本项目myBatis运用了两个插件[`tk.mybatis.mapper`](https://github.com/abel533/Mapper)和[`com.github.pagehelper.pagehelper`](https://github.com/pagehelper/Mybatis-PageHelper) 所有Mapper都继承自`com.github.adminframework.util.MyMapper`,用法请看[`tk.mybatis.mapper`](https://github.com/abel533/Mapper)插件介绍。
由于`MyMapper`继承了`MySqlMapper `,且项目中有用到该Mapper提供的对mysql的批量新增方法，因此这个地方只支持`mysql`数据库。若需替换其他数据库，请自行改动。
2. mapper中覆盖了select方法之后，controller中findByWhere方法就取决于自己覆盖的select了，若sql少写了where查询条件，那么查询就不能正确工作 

###重要注意：
使用`tk.mybatis.mapper`插件后，用它提供的MBG插件进行生成实体类，默认主键属性上都有`@GeneratedValue(strategy = GenerationType.IDENTITY)`注解，这对自增主键是没有问题的，但对于非自增主键，或者UUID来说，它会将主键回写为0 ！！！ 使用UUID的请修改或去掉该注解，具体用法[请点击此处，看第3条内容](http://git.oschina.net/free/Mapper/blob/master/wiki/mapper3/3.Use.md)

## TODO

- 目前只适用于root.war部署，改成项目名部署url会出错，要解决！！(优先)
- baseService中uploadFile方法还未测试
- 角色资源映射表中只保存了前端选中资源的信息，没有保存父资源的信息。因此在人员登录后生成菜单的时候，要处理父菜单的信息情形。(例：只保存了一个菜单信息，没保存该菜单的模块信息。显示菜单的时候，模块菜单都要显示。注：该问题受限于jstree的选中状态。父选中，子都被选中，只选中某个子，则父状态为`undetermined`,获取选中的id时，并没有此项，因此传入后端保存，只保存了子信息。)
- 模糊查询 后端权限验证，控制层方法加入权限注解 加入缓存
- 与log4j2集成
- 缓存模块实现
- 将jstree的样式改掉，用icheck的皮肤改造该插件的选择框

## bug
- 分页查询orderBy语句 直接将页面传回的字段名作为sql一部分查询了， 若该字段页面使用是驼峰类型，数据库是下滑线类型就会找不到列，加了@Transient注解的非数据库映射字段也会找不到列，导致查询出错。暂时先关闭了排序功能。！！！重要
- 分页查询orderBy语句 可能会引起sql注入，请查看并确认
- index.html 头像下面的dropdown菜单（点击可以修改密码和退出的地方）在刚进入首页的时候点击是能弹出菜单来的，但是点了其他的功能后，再点击就没反应了。
- 首页进入后，点击某菜单页，此时该菜单打开，导航栏可以看到导航信息。但是点击刷新之后，菜单就合上了，导航栏也不显示了。应该还选中该菜单，菜单项打开，显示指向该菜单的导航栏。
- 新增/修改的init项 是异步调取的ajax 和修改时异步获取的该条信息 回调成功方法理论上不能确定先后顺序
目前是init项先回调 setForm时可以正确set该字段的值 若该条信息的ajax先回调，set该字段值的时候就会出错。
需要判断回调的先后顺序！
- 更新时候是只更新有值的项  那么想把某个字段设置成空值就不会更新这个字段了，需要修正。
(目前使用的是updateByPrimaryKeySelective方法，因此不会更新空值字段，
但是若将起换成updateByPrimaryKey方法全部更新的话又会导致有一些页面上没有的字段，绑定进来时空值，
但数据库中该字段是有值的，此时会数据库中的值会被覆盖掉，导致更新了不必要的字段，该情况需考虑！)
- 修改setForm值的时候，select对应字段没有该值，set该值后会导致select选中了个空白选项。
(如select共有空和1两个选项值，set对应字段的时候set了个2值进去，就会导致select看上去选中了一个空白值)
- shiro注解@RequiresPermissions 授权失败，即该客户无此权限会抛出UnauthorizedException异常，该异常目前在配置的spring
全局异常拦截器里面处理的，能不能像AjaxFormAuthenticationFilter一样写一个自定义filter去处理
- `app.js`文件`ajaxSubmit`方法`resetForm`属性为`true`,若提交表单返回失败，则自动清空了表单内容，很不合理，
但有些地方会有无论成功失败都要清空表单的地方，写两个方法，还是传入`resetForm`参数(该方法要求参数向前补齐)，请思考解决
- 角色分配用户的时候把用户全都查了出来，用户量大了之后肯定会变慢，请设法解决。
- summernote富文本框插件在自定义上传文件之后，点击文件，弹出选择文件的框很慢，请找原因



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)