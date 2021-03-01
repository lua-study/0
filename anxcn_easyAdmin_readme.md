### EasyAdmin For Thinkphp 5.1.12

#### 安装说明
1. 修改数据库配置文件
```
   
    'database'        => '你的数据库',
    
    'username'        => '数据库名称',
   
    'password'        => '数据库密码',
    
    'prefix'          => 'ky_',
    
    @数据库默认带有前缀，前缀为ky_
    
```
2.修改伪静态配置
```
[ Apache ]
  
  Options +FollowSymlinks -Multiviews
  RewriteEngine On

  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteRule ^(.*)$ index.php/$1 [QSA,PT,L]
 

[ IIS ]
 
  
  
  
  
  
  
  
  
  
  
  
  

[ Nginx ]
location / { // …..省略部分代码
   if (!-e $request_filename) {
   		rewrite  ^(.*)$  /index.php?s=/$1  last;
    }
}

[ Phpstudy]
 
Options +FollowSymlinks -Multiviews
RewriteEngine on
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^(.*)$ index.php [L,E=PATH_INFO:$1]
 
```
3.其它配置请参考官方文档
官方文档：https://www.kancloud.cn/manual/thinkphp5_1/353955

#### 后台模块说明
1. 后台采用AUTH权限验证，不懂的同学可以查看相关文档
2. 后台界面采用moltran+bootstarp
3. 实现用户管理，权限管理，角色管理，部门管理
4. 后续将按照商城开发。

#### 其它说明
1.作者属于个人开发，或多或少有些BUG，如发现BUG，可以 @芒果人生 作者基本在线可以回答。
2. 可以加群一起研究讨论QQ群：781216188


#### 界面展示
![输入图片说明](https://gitee.com/uploads/images/2018/0511/184420_e0014c5a_1091193.png "1.png")
![输入图片说明](https://gitee.com/uploads/images/2018/0511/184431_69c52ec8_1091193.png "2.png")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)