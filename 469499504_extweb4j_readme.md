#extweb4j
### jfinal2+extjs6开发的WEB通用基础平台

### 介绍
```
1. extweb4j是用extjs6+jfinal2开发的轻量级通用WEB基础项目。
2. 使用Ext的最新版本extjs6.0.1，使得开发者不再被UI所困扰,其组件丰富,设计美观,控制精细,多年来深得用户喜爱。
3. 包含基础功能有:用户、角色、权限、菜单、资源、部门、日志、消息提醒、报表、文件上传等。
4. 对Jfinal的Model提供的方法进行了扩展,比如findFirstByAttr,findByAttr,findAll,countAll,pageDataBy等。
5. 支持用户多角色分配。
6. 权限控制粒度细到按钮级别，配置简单明了，对于需要进行权限拦截的资源只需在Controller的方法上面增加@AuthAnno注解即可。
7. 演示项目:[http://extweb4j.duapp.com/](http://extweb4j.duapp.com/),账号/密码:test/123456
8.  **最近更新,增加菜单图标下拉选择功能，使用了[Font Awesome](http://www.thinkcmf.com/font)图标,增强日志记录功能，在控制器使用@Log
方便记录日志;增加了pinyin4j,支持拼音搜索、首字母搜索。** 
```
### 快速开始
```
1. 打开你的MySQL,导入src/main/resources/sql目录下的extweb4j.sql数据库脚本。
2. 将项目导入到eclipse使用maven进行package,然后run即可启动。
3. 打开浏览器输入访问地址（注意上下文需要设置为"/",否则可能出现404异常）,账号/密码:admin/123456。
```

### 参考网站


1. Ext官网:[https://www.sencha.com/](https://www.sencha.com/)
2. Ext官方GPL版下载地址:[https://www.sencha.com/legal/GPL/](https://www.sencha.com/legal/GPL/)
3. Ext官方API:[http://docs.sencha.com/](http://docs.sencha.com/)
4. Ext官方Demo合集:[http://examples.sencha.com/extjs/6.2.0-ea/examples/](http://examples.sencha.com/extjs/6.2.0-ea/examples/)
5. 第三方字体图标:[http://www.thinkcmf.com/font/search.html](http://www.thinkcmf.com/font/search.html)


### 截图
![输入图片说明](http://git.oschina.net/uploads/images/2016/0728/214950_6fdb2759_89451.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2016/0728/214959_dbe9cc34_89451.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2016/0728/215006_9a309cd4_89451.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2016/0728/215012_2489853c_89451.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2016/0728/215019_a75edc8d_89451.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2016/0728/215025_56712223_89451.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2016/0728/215032_0a533e48_89451.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2016/0728/215040_17471af8_89451.png "在这里输入图片标题")
### 捐赠
![输入图片说明](http://git.oschina.net/uploads/images/2016/0711/231614_4d2c2128_89451.jpeg "在这里输入图片标题")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)