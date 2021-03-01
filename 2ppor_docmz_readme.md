# Doc.MZ文档管理系统

## 简介

- 多人Markdown文档管理系统；
- 运行环境:PHP5.3+, MySQL5.0；
- 方便小团体内部使用的Markdown文档管理系统。

## 系统演示

- 预览：[http://doc.tecmz.com](http://doc.tecmz.com)
- 示例文档：[http://doc.tecmz.com/r/gamektTvFFQxdyFrGrHdwSQEHCaTVxiFNTDlyntHCWPunSfFUh:preview](http://doc.tecmz.com/r/gamektTvFFQxdyFrGrHdwSQEHCaTVxiFNTDlyntHCWPunSfFUh:preview)


## 系统特性

### 基于开源的editor.md

基于开源的[editor.md](https://pandao.github.io/editor.md/)，人性化的编辑方式。

### 完全Markdown

完全支持Markdown基本语法和扩展语法（流程图、时序图、函数公式）

### 人性化显示方式

- **URL访问：**唯一的网络访问地址；
- **HTML下载：**生成单独HTML页面，所有资源完全静态化；
- **PDF打印：**生成方便打印的PDF页面。

### 历史版本保存

保存最近更新的50个历史版本，方便误操作恢复；

### Wordpress互联

如果你是在团体内部使用Doc.MZ，你可以选择与Wordpress互联模式，这样可以完全既保证两个系统的独立性，又能保证同步Wordpress数据。


## 伪静态设置

如果你希望你的系统链接变得更没，不包含 ?s= 这一段信息，你可以设置伪静态如下（具体是否是子路径需要根据实际的环境进行设置）。

### Apache环境.htaccess文件

	RewriteEngine On
	RewriteBase /
	RewriteRule ^/?$ - [NC,L]
	RewriteRule ^(app/|data/|asserts/|res/|_RUN/|robots\.txt|crossdomain\.xml).*$ - [NC,L]
	RewriteRule ^([a-z0-9]+)\.php - [NC,L]
	RewriteRule ^(.*)$ index.php/$1  [NC,L]

### Nginx环境*.conf文件
	location / {
    	index index.php;
    	if ( !-e $request_filename ) {
            rewrite ^(.*)$ /index.php?s=$1 last;
            break;
        }
    }

    location ~ \.php$ {
        fastcgi_pass   127.0.0.1:9000;
        fastcgi_index  index.php;
        fastcgi_param  PHP_VALUE  "open_basedir=$document_root:/tmp/";
        fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        include fastcgi_params;
    }

    location ~* ^/(app|data|asserts|robots\.txt|crossdomain\.xml)/.*$ {
        if ( -f $request_filename ) {
            expires max;
            break;
        }
    }




# 许可协议

Co.MZ企业系统遵循Apache2开源协议发布。Apache Licence是著名的非盈利开源组织Apache采用的协议。该协议和BSD类似，鼓励代码共享和尊重原作者的著作权，同样允许代码修改，再作为开源或商业软件发布。需要满足的条件:

1. 需要给代码的用户一份Apache Licence ；
2. 如果你修改了代码，需要在被修改的文件中说明；
3. 在延伸的代码中（修改和有源代码衍生的代码中）需要带有原来代码中的协议，商标，专利声明和其他原来作者规定需要包含的说明；
4. 如果再发布的产品中包含一个Notice文件，则在Notice文件中需要带有Apache Licence。你可以在Notice中增加自己的许可，但不可以表现为对Apache Licence构成更改。

具体的协议参考：[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)