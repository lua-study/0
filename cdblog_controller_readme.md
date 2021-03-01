###管理员
#####路由表查询[route:list]
````
    menus 添加一个角色管理
    RoleController 角色管理
    routes 配置角色管理路由
    添加模板 
    生成权限相关的文件[添加角色表 中间表 权限表]：php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider" --tag="migrations"
    修改roles表结构，添加中文修饰的字段
    执行迁移：php artisan migrate
    guards 绑定一个守卫
    在laravel手册中寻找【新建角色】
    在RoleController里面的store添加数据
    添加数据，增加闪存信息
````
###表单验证[排除和自己的比较]
````
    设置编辑内容时Request只验证自己和自己之外的数据对比，而不和自己对比
    强迫 Unique 规则忽略指定 ID 
    $id = $this->route('adminuser');必须为路由规则后面的参数
    unique:admins,username,.id，
````
###新建一个验证模块
````
    RouteRequest
    将当前修改的角色数据排除
````
###权限模块
````
    parmission
    设置权限值
````
###创建模型和迁移
````
    php artisan hd:model Category Article
````
###分配权限
````
    在index里面删除的后面添加分配权限按钮
    RolrController里面添加一个展示权限列表的方法
    新建一个膜拜在role文件里
    获得所有模块的权限配置
    RolrController里面再添加一个处理权限内容的方法
````
###获取权限配置
````
   根据 guard 获取权限数据，可用于后台配置设置表单。
   \HDModule::getPermissionByGuard('admin');
````
###微信配置
````
微信开发操作步骤

1.我们想在项目中加入微信操作,那么最重要的一步就是首先要用当前项目和微信公众号连接上,这个时候,连接需要一个url,我们应该创建一个控制器,里面写一个方法,用来和微信公众号对接,由于是laravel框架的原因,这个方法被访问,必须使用路由的形式
2.对接的时候需要使用到token,后面的其他功能开发,比如创建自定义菜单需要使用到appid,appsecret等参数,所以我们首先做一个项目后台的微信配置参数管理操作
3.使用什么方式都可以,这里由于我们已经学会了使用自动化构建,这种方式是最快捷的,首先创建一个微信配置项的模型以及数据迁移文件,使用一下命令: hd:model WxConfig Wx
4.根据设计表的思维方式,将数据迁移文件写好,然后执行迁移,创建出wx_configs的表.
5.使用一下命令,执行自动化构建: hd:autocreate Modules/Wx/Entities/WxConfig.php 微信 会自动化构建出微信配置管理的模板及控制器和完成好的方法
6.由于表字段和以前的设计方式不同了,所以需要修改添加方法加载的模板布局.
7.store方法也需要进行相对应的修改,完成微信配置的添加,但是在添加的时候需要注意一个问题,就是每次添加之前,应该先将表中的数据截断,然后再添加
8.配置完毕之后,我们就应该在和微信互通的控制器里的方法内调用三方组件后盾网的wechat组件来完成微信验证
9.调用Wechat::valid()方法之前,需要先配置好wechat类所需要的配置项,我们就手动在config目录中添加一个wechat.php的文件,然后将手册中的配置文件拿过来,放入wechat.php文件中
9.在WechatController控制器中的handle方法里面获取配置文件的内容,但是配置文件内容并不一定是用户真实的数据,所以我们需要将数据库中填写的数据也获取过来,然后合并数组,再交给wechat类的config方法,最后调用valid方法进行验证
10.在app/Http/Middleware/VerifyCsrfToken.php  加上微信的路由，这里写的路由会被laravel排除csrf验证


坑坑坑:
由于我们做微信开发使用了后盾网的三方组件wechat类,那么直接调用类的方法之前,要安装wechat组件
1.找到手册中的安装配置,复制代码:composer require houdunwang/wechat,执行过程中,由于我们之前使用了redis,而现在项目在服务器上, 如果服务器上没有配置redis相关所需要的组件,就会抱一个错误.
2.我们可以使用 composer remove laravel/horizon 将这个组件删除
3.删除后再来安装wechat组件: composer require houdunwang/wechat
4.这个时候,安装可能会遇到各种各样的坑:
坑1:如果你还是使用的composer提供的中国镜像,那么下载的wechat组件的内容会和laravel框架有冲突,导致框架可能会坏,因为下载的还是1.0.24的版本,而现在最新的已经是2.0.11版本了,所以我们需要更换另外一种方式来进行下载
5.既然中国镜像不行了,那么我们就改成国外镜像来下载,但是国外镜像会有一个速度慢的问题.这个解决方案也可行,具体是否采用,自行决定
6.提供给大家一个larave-china提供的中国镜像地址,操作步骤如下:

"repositories": {
    "packagist": {
        "type": "composer",
        "url": "https://packagist.laravel-china.org"
    }
}

将以上代码复制粘贴到composer.json文件的末尾,然后在命令行执行composer dump,再来下载wechat组件

````

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)