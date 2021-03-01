# China-Data-Dictionary
===

## 目的

新公司英文化环境,db表结构里字段描述是英文的,阅读起来不好理解.
所以开发了这个小工具帮助快速熟悉数据库表结构.


将本地代码推送到远端仓库

```sh
# 关联到远程仓库
git remote add origin https://gitee.com/amlove2/China-Data-Dictionary.git
# 将远程仓库与本地仓库同步合并
git pull --rebase origin master
# 把本地仓库代码内容推送到远程仓库
git push -u origin master
```

## 使用步骤

1. 修改 `index.php` 文件里 `app_init()`将其中定义的如下常量换成你的

```php
define('MYSQL_HOST','localhost');
define('MYSQL_PORT','3306');
define('MYSQL_DB','mysql');
define('MYSQL_USER','root');
define('MYSQL_PASS','root');
```

2. 在代码目录下执行 `php -S localhost:8000` 开启web服务器

3. 浏览器里输入[http://localhost:8000/](http://localhost:8000/) 生成`crawRecords.dat`文件

4. 在代码目录下执行`php crawRecords.php`自动进行翻译

5. 再次刷新浏览器 即可

> 目录里提供了一个 Demo: [mysql-Data-Dictionary.html](/china-data-dictionary/mysql-Data-Dictionary.html)

6. 如果对自动翻译的结果不满意,也可访问[http://localhost:8000/?q=trans](http://localhost:8000/?q=trans)修改

7. 修改完成后,再次访问 [http://localhost:8000/](http://localhost:8000/) 即可



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)