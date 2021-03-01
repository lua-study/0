#Metronic php jquery bootstrap
放入网站根目录下，从admin5/login.php 进入，否则会报错。因为里面用了个cookie，在login.php触发生成
默认用户名密码： 1:q

目前用了Metronic模板，添加了sqlite数据库的增删改。整个文件没有压缩，plugin目录的体积比较大。后面根据情况剔除多余的控件。感兴趣的可以一块研究

效果
![输入图片说明](http://git.oschina.net/uploads/images/2016/0313/201813_980e6675_485157.png "在这里输入图片标题")

项目目录说明(点击编辑进入查看，格式不会乱);

----|
	|---/admin5	----|-------/html(Metronic模板 目前尚且没有用到的html文件)
	|				|
	|				|-------/tpl 一些模板文件，用于动态显示时候使用，动态显示用到了artTemplate.js
	|				|
	|				|-------index.php  主页文件
	|				|-------lock.php  锁屏文件
	|				`-------login.php  登录文件
	|
	|---/assets	----|-------/app 暂时未用到
	|				|
	|				|--------/global 插件目录 目前体积最大的目录。在plugin中添加了artTemplate-native.js
	|				|
	|				|--------/layouts 布局的一些js  暂时未修改
	|				|
	|				、--------/pages 里面的scipts 文件夹是主要的js文件，script/js是模板中未用到的js
	|
	|
	|---/demo --------------里面是主要的后台php脚本。主要用于与 index.php login.php 以及其他的js脚本交互
					|--/php 	暂时没有用到的php后台文件 模板中自带
					|--sqlite.class.php  sqlite操作基本文件
					|		
					|--sqlite.db 本地数据库
					|--test.php 测试sqlite结果
					|--db_operation.php 与页面交互的借口文件
					|--config.php 数据库配置文件
					|--common.function.php 通用函数文件	



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)