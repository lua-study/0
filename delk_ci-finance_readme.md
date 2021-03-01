![图1](http://financeapi.applinzi.com/application/thumb/1-1.png "登录")

#1.下载：

https://github.com/bcit-ci/CodeIgniter/archive/3.1.0.zip

解压到根目录

#2.创建Controller

application/controller/User.php

目标URL

http://financeapi.applinzi.com/index.php/user/login/

#3.接收openid参数

使用input类，更安全

```
 input->post('openid');
	}
}
```

#4.建表

```
CREATE TABLE `user` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `username` varchar(255) COLLATE utf8_unicode_ci DEFAULT NULL,
  `openid` varchar(255) COLLATE utf8_unicode_ci NOT NULL,
  `accessToken` char(32) COLLATE utf8_unicode_ci DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `username` (`username`),
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8 COLLATE=utf8_unicode_ci;
```

#5.查询数据库，该用户是否存在。如存在，则返回用户信息供小程序本地storage保存；若不存在，则先新建一个用户。

加载数据库类：

autoload.php 第61行

```
$autoload['libraries'] = array('database');
```

配置数据库连接

database.php

```
$db['default'] = array(
	'dsn'	=> '',
	'hostname' => 'localhost',
	'username' => '',
	'password' => '',
	'database' => '',
	);
```

数据库类：http://codeigniter.org.cn/user_guide/database/results.html#id5

查询代码：

```
	public function login() {
		header("Content-type: application/json");
		// 取出参数
		$openid = $this->input->post('openid');
		// 查询数据库
		$query = $this->db->query("select * from user where openid = '" . $openid . "'");
		// 返回行数
		if ($query->num_rows() > 0) {
			// 取出该用户
			$user = $query->first_row();
			// 输出用户的信息
			echo json_encode($user);
			return;
		}
	}
```

新建代码：

```
		// 注册用户
		$user = array(
				'username' => $openid,
				'openid' => $openid,
				'accessToken' => md5(time().'mysalt')
			);
		$this->db->insert('user', $user);
		echo json_encode($user);
		return;
```

正文完

[2016-10-21]

#接口规范：

##1.用户登录

user/login

参数：openid

返回uid nickname accessToken

##2.添加一条账目，accessToken均需要入参，下同

item/add

入参：title,cate,account,date

返回是否成功

##3.读取一条账目

入参：id

返回

id,title,cate,account,date

##4.修改一条账目

item/edit

入参：id,title,cate,account,date

##5.删除一条账目

入参：id

##6.读取自己的账目

item/all

入参：除accessToken无

[2016-10-24]

![如图1](https://static.oschina.net/uploads/img/201610/24145920_0h7L.png "添加成功")

#目标：凭借accessToken来添加一条账目

对应接口item/add

##创建基类

完成json默认输出格式

实现json输出函数，$data每次必传，msg，code可以缺省

```
  $code, 'msg' => $msg,'data' => $data));
	}
}
```

##调用示例

引入BaseController.php

继承之

起一个add方法，输出一个标准json

```
 json_output(array(), '成功', 200);
	}
}
```

##账目保存数据库

1.建表

```
CREATE TABLE `item` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `title` varchar(32) DEFAULT NULL,
  `cate` varchar(32) DEFAULT NULL,
  `account` decimal(10,1) DEFAULT NULL,
  `date` date DEFAULT NULL,
  `uid` int(11) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;
```


2.对accessToken进行认证

声明一个auth的私有方法，在构造函数__construct()中调用，如果认证通过返回true，使得程序继续执行；失败则输出json错误提示信息，不再执行，退出程序。

```
	// 	缓存uid
	protected $uid;
	
/**
	 * 构造函数，子类如Item控制器会自动调用它
	 */
	function __construct() {
		parent::__construct();
		$this->auth();
	}

	/**
	 * 认证，拿到accessToken，表明用户是已授权微信登录的用户，该accessToken缓存在小程序侧
	 */
	private function auth(){
		$accessToken = $this->input->get('accessToken');
		// 		查询数据库，是否有此用户
		$query = $this->db->query("select * from user where accessToken = '$accessToken'");
		if ($query->num_rows() > 0) {
			$this->uid = $query->first_row()->uid;
			return true;
		}
		$this->json_output(array(), '认证失败', 401);
		// 		如果没有查询到，直接结束程序，不必走正常控制器方法如item/add的json输出
		exit;
	}
```

3.控制器add方法写入数据库

```
// 	添加账目
	public function add() {
// 		取到数组
		$data = $this->input->get();
// 		移除accessToken，因不被添加到数据表
		unset($data['accessToken']);
// 		添加uid
		$data['uid'] = $this->uid;
// 		写入数据库
		if ($this->db->insert('item', $data)) {
	// 		返回结果
			return $this->json_output(array(), '添加成功', 200);
		}
	}
```

4.依样画葫芦，完成CRUD的其他操作，注意访问权限，不可跨用户操作

```

	// 	删除账目
	public function del(){
		// 		获取id
		$id = $this->input->get('id');
		// 		数据库中删除。需依据id与uid，保证资源的合法性，只删除自己的账目
		$this->db->delete('item', array('id'=>$id, 'uid'=>$this->uid));
		if ($this->db->affected_rows() > 0) {
			$this->json_output(array(), '删除成功', 200);
		} else {
			$this->json_output(array(), '权限不足', 400);
		}
	}

	// 	读取账目
	public function view(){
		//获取id
		$id = $this->input->get('id');
		//查询数据库
		$query = $this->db->get_where('item', array('id' => $id, 'uid' => $this->uid));
		if ($query->num_rows() > 0) {
			// 		输出账目
			$this->json_output($query->first_row(), '加载成功', 200);
		} else {
			$this->json_output(array(), '权限不足', 400);
		}
	}

	// 	修改账目
	public function update() {
		// 		获取提交进来的参数
		$data = $this->input->get();
		// 		移除accessToken，因不被添加到数据表
		unset($data['accessToken']);
// 		先判断资源所属
		$query = $this->db->get_where('item', array('id' => $data['id'], 'uid' => $this->uid));
		if ($query->num_rows() > 0) {
			// 更新数据库
			if ($this->db->update('item', $data, array('id'=>$data['id']))) {
				$this->json_output(array(), '修改成功', 200);
			}
		} else {
			$this->json_output(array(), '权限不足', 400);
		}
	}

	// 	账目列表
	public function all(){
		// 		查询该用户下的所有账目
		$query = $this->db->get_where('item', array('uid'=>$this->uid));
		$this->json_output($query->result(), '加载成功', 200);
	}
```

源码下载：关注下方的公众号->回复数字1009

对小程序开发有趣的朋友关注公众号: huangxiujie85，QQ群: 575136499，微信: small_application，陆续还将推出更多作品。

![公众号](https://static.oschina.net/uploads/img/201610/07111145_qD6d.jpg "二维码")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)