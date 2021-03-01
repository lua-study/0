Thinkphp6 认证
======

### 安装
~~~
composer require ric/thinkphp6-auth
~~~

### 导入数据表
> 本工具优化为多端权限认证,同时每端又支持通过传website_id实现同个应用saas权限制，并可通过配置auth_rule_unified参数来指定同个应用内是使用同个权限规则还是通过website_id来区分多个权限规则
> `toadmin_` 为admin后台端，默认无表前坠，有表前坠的请自行添加

~~~
`------------------------------
-- toadmin_auth_rule，规则表，
------------------------------
DROP TABLE IF EXISTS `toadmin_auth_rule`;
CREATE TABLE `toadmin_auth_rule` (
  `id` mediumint(8) unsigned NOT NULL AUTO_INCREMENT COMMENT '主键',
  `website_id` int(10) NOT NULL DEFAULT '0' COMMENT '站点id，用于多站点，默认0',
  `name` char(80) CHARACTER SET utf8 NOT NULL DEFAULT '' COMMENT '规则唯一标识',
  `title` char(20) CHARACTER SET utf8 NOT NULL DEFAULT '' COMMENT '规则中文名称',
  `type` tinyint(1) NOT NULL DEFAULT '1' COMMENT '在think_auth_rule 表中定义一条规则时，如果type为1， condition字段就可以定义规则表达式。 如定义{score}>5  and {score}  ric\auth\middleware\Auth::class,


例如路由：
Route::get('/', 'index/controller/Index/index');
使用后为：
Route::get('/', 'index/controller/Index/index')->middleware(auth,['admin','login']);

第一个参数：必填参数，用于标示是调用哪个端，对应config/auth.php 配置中的一维键
第二个参数：选填，用于标示是否使用auth权限验证或者登录退出，login登录、logout退出、getinfo获取登录用户信息、log记录日志信息、getrule获取所有权限列表
其中，login、logout成功时，会自动记录日志信息，其它需要配置第二个参数时才会记录日志信息到toadmin_auth_log表
```

## 内置方法
本包内置了，用户、权限、用户组等增删改查方法，详情查看 /vendor/ric/thinkphp6-auth/Auth.php类
如：获取用户组：

```
    /**
     * 用户组列表
     */
    public function getGroupAll($current_page,$per_page)
    {
        $list = Db::table($this->config['auth_group'])
            ->where([])->withoutField('password')->paginate([
                'list_rows'=> $per_page?:10,       //每页数量
                'var_page' => 'page',   //分页变量
                'page'     => $current_page?:1,        //当前页面
            ]);
        return $list->toArray();
    }
```

在路由中例子为：

```
Route::post('auth/getGroupAll',  'Auth/getGroupAll')->middleware('auth',['admin']);
```

在自己控制器中的调用方式例子为：

```
    /**
    * @title   获取用户组列表
    * @desc    用户组列表
    * @author  Ric
    * @version 1.0
    *
    * @param int $current_page  1 分页数，指定获取第几页的数据  require_分页数不能为空.number
    * @param int $per_page 10 分页大小，指定分页大小  require_分页大小不能为空.number
    *
    * @return int id  1212
    * @return int website_id 445 站点id，用于多站点，默认0
    * @return char title 55 用户组中文名称
    * @return tinyint status 473 状态：为1正常，为0禁用
    * @return varchar rules 579 用户组拥有的规则id， 多个规则","隔开
    * @return datetime create_time 255 最后修改时间
    * @return datetime update_time 533 添加时间
    */
    public function getGroupAll()
    {
        //获取参数
        $data = request()->param();

        $list = request()->middleware('auth')->getGroupAll($data['current_page'], $data['per_page']); 

        return totrue($list);
    }
```

通过request()->middleware('auth') 来直接调用该包的类


## 建议
toadmin_auth_rule 中规则按页面结构进行创建，共用的部分统一放base中
比如
base      系统共用
   -- 上传
website   站点管理页面，一级菜单
   -- 查看信息     查看站点信息
   -- 修改信息     修改站点信息
   -- 添加信息     添加站点信息

通过中间件定义，可以获得用户所属的所有用户组，方便我们在网站上面显示。

Auth类还可以按用户属性进行判断权限， 比如
按照用户积分进行判断， 假设我们的用户表 (admin_members) 有字段 score 记录了用户积分。 
我在规则表添加规则时，定义规则表的condition 字段，condition字段是规则条件，默认为空 表示没有附加条件，用户组中只有规则 就通过认证。
如果定义了 condition字段，用户组中有规则不一定能通过认证，程序还会判断是否满足附加条件。
比如我们添加几条规则： 

> `name`字段：grade1 `condition`字段：{score} 
> `name`字段：grade2 `condition`字段：{score}>100 and {score} 
> `name`字段：grade3 `condition`字段：{score}>200 and {score}  $auth->check('grade1', uid) 是判断用户积分是不是0-100 
> $auth->check('grade2', uid) 判断用户积分是不是在100-200 
> $auth->check('grade3', uid) 判断用户积分是不是在200-300

## json返回说明

该应用内置了两个json输出函数，通过这两个函数可以输出统一格式的json，格式如下：

```$xslt
{
    "status": '状态码',
    "message": "消息提示",
    "data": '数据内容'
}
```

```
    /**
     * 返回json信息
     * @param string $status 当前错误状态
     * @param string $message 返回错误信息前追加内容,默认为空
     */
    function tofalse($status,$message=''){
        try {
            $data = tocode(100,$e->getMessage());
            return json($data);
        } catch (\Exception $e) {
            return json(tocode(-1,$e->getMessage()));
        }
    }
```

    
```
    /**
     * 返回操作成功json信息
     * @param array $object 当前返回对象
     * @param string $special 特殊返回对象处理 有类型：select
     */
    function totrue($object,$message=''){
        try {
            $data = tocode(100,$e->getMessage());
            $data['data'] = $object;
            ob_clean();
            return json($data);
        } catch (\Exception $e) {
            return json(tocode(-1,$e->getMessage()));
        }
    }
```

### api、rpc函数说明

> thinkphp6 取消了action 跨应用调用类，rpc函数即为该函数的替代品，可以实现，跨应用、跨目录调用
例：

rpc: 第一个参数为类名，填写完整的，方便ide调整，第二个参数为方法名，第三个参数为传值
```$xslt
	$isexist= rpc('app\admin\logic\authadmin\UserLogic', 'exist_account', [$account]); 
```

api: 第一个参数为类名，第一个参数为传值，其中$data 数据是对应形式，键和api文件定义的需要一直，会根据api文件
的定义自动做数据效验。

```
    $data = [
        'website_id' => $website_id,
    ];
    $webinfo = api('app\website\api\config\Info',$data);
```

app\website\api\config\Info.php 文件例子

```$xslt
  ['valid'=>'require.站点ID不能为空|number', 'title'=>'站点id', 'desc'=>'用于区分站点'],
    ];

    //处理数据，创建验证器
    public function __construct(){
        list($this->rule,$this->message) = getValidate($this->params);
        parent::__construct();
    }

    /**
     * 详情，其中参数名称要和$params中定义的一致
     */
    public function api($website_id)
    {
        return rpc('app\website\logic\WebConfig', 'getWebConfigFind', [$website_id]);
    }


}
```

> 在开发时，建议采用领域应用模式开发，即每个应用，通过api提供接口，对其它应用对接，然后api接口通过rpc方法处理
内部领域内容，一个应用即为一个领域。博主的目录结构如下，仅供参考：

```$xslt
app
  -- website    站点管理应用 （该应用提供站点管理服务，对平台内部，不设置路由，不直接对外提供接口，核心api、logic、dao三层）
     -- api     对平台提供api服务，通过rpc调用自身的logic和dao层，进行业务处理，一个文件即一个接口
        -- config 站点配置信息
           -- Add.php 添加站点配置信息
           -- Info.php 获取站点配置信息
     -- logic   业务处理
     -- dao     数据处理
     
  -- toadmin    后台平台api （该应用为后台平台提供api接口，设置路由，供前端调用，编写页面，核心controller，无其它）
     -- controller 控制器，根据需要通过api函数调用 website站点的api 接口，获取信息，返回数据
     
  -- topc       pc端平台api （该应用为pc端提供api接口，设置路由，供前端调用，编写页面，核心controller，无其它）
     -- controller 控制器，根据需要通过api函数调用 website站点的api 接口，获取信息，返回数据
     
```
     
     
## 说明

为啥api是一个接口一个文件嗯？
1、方便管理
2、后续会提供自动生产api文档，避免通用的功能不同人，或者时间久了维护时，拼命的写相同功能的方法，导致方法冗余严重，越来越难维护
3、为后续其它应用做准备
     


# 更新日志

> 20191012 v1.0.31
* 中间件调整，src/middleware/Auth.php中31行，获取站点字段参数由website_id调整为base_website_id，以及获取参数与获取中间件调换位置。
> 20190912 v1.0.7
* 更新TP6 升级session导致的部分方法失效问题


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)