#通用权限管理系统
###权限管理精确到按钮，权限管理自由把控

将基本的增删改查操作做了大量封装，后端使用切面来统一验证表单数据（前段验证待添加），并使用切面，统一处理特殊查询条件
简单化DAO层，封装通用Service，封装分页，封装多参数查询等
前端集成错误信息处理，成功回调，异步加载表单，异步提交等。

项目完整的实现了权限管理，将权限操作简单化，可控化，可灵活的添加和修改权限，自动提示权限url等功能。并使用统一权限拦截器，可以根据规则拦截指定url权限。

集成了阿里的druid，更加方便的查看和监控sql语句执行

使用该项目需要基本知识： java，maven，eclipse，git，jquery，spring framework,spring mvc，hibernate/mybatis

使用步骤
####1：git clone
####2：eclipse /myeclipse  import existing maven projects
####3: 导入gas.sql数据
####4: 更新src/main/resources/application.properties 中的jdbc配置
####5: mvn clean jetty:run 或者 mvn package 将打包好的war文件发布到 web容器中 
####6: 登录localhost:8080/gas/rest/admin/index
####默认用户名gas_admin 密码 1
因为比较懒，所有直接用hibernate建表了，gas.sql是导出来的初始化菜单数据，同样也是因为比较懒，不想写初始化脚本--（捂脸）


![登录页面](http://git.oschina.net/uploads/images/2016/0107/170523_5ad24996_367789.png "登录页面")

![子权限](http://git.oschina.net/uploads/images/2016/0225/151651_c4565d4f_367789.png "在这里输入图片标题")
![子权限](http://git.oschina.net/uploads/images/2016/0225/151712_00daccb7_367789.png "在这里输入图片标题")

![输入图片说明](http://git.oschina.net/uploads/images/2016/0107/170630_8d153162_367789.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2016/0107/170636_d7819da0_367789.png "在这里输入图片标题")


>######Author:Diamond 
>######Email:458293193@qq.com


感谢：https://github.com/starzou/quick4j 该项目作者共享的代码，吸收了很多有用的东西

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)