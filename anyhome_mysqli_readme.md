# mysqli

#### 介绍

基于 [EasySwoole-Mysqli](https://www.easyswoole.com/Manual/3.x/Cn/_book/Database/mysqli/Introduction.html "EasySwoole-Mysqli") 扩展开发,增加一些兼容thinkphp的使用方法。



#### 安装教程
`composer require anyhome/swoole-mysqli`

#### 新增配置项说明

数据库表前缀

`  'prefix'          => 'db_',  `

是否严格检查字段是否存在 ，当设置为 true 时，则提交的字段必须与表相同，当设置为false时候则会自动和表字段比较，去除差异的。

`'fields_strict'   => false,`



#### 使用说明

与官方相比较新增了 name、table、find、select、limit、page、order等方法

1. 多条查询
```
$list = $db->name('news')->where('id',10,'>')->page(1,10)->order('id','desc')->select()
```

2. 单条查询
```
$vo = $db->name('news')->where('id',10)->order('id','desc')->find();
```

3. 新增数据
```php
$post = array();
$post['title'] = 'xxxxx';
$post['desc'] = 'desc';
$id = $db->name('news')->insert($post);
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)