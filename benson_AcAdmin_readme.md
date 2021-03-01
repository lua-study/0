# ApiCloud云端管理平台

标签（空格分隔）： ApiCloud AcAdmin

---
###功能介绍    

1.实现通用统一的后台数据管理，查询、新增、修改、删除。    
2.实现ApiCloud的文件上传、删除管理。    
3.后台登陆用户管理    
4.APP用户管理    
5.新增数据时候，实现图片上传功能（ApiCloud的file字段）    

---
####支持
QQ交流群：196578969    
支持我：ayhome@gmail.com      
####使用场景
[ApiCloud][1]是一个免费的在线生成混合型APP的平台，ApiCloud完全免费。    
在使用ApiCloud的过程中，不可避免的需要和维护后台数据库，虽然ApiCloud提供后台数据库服务---**数据云**，但并没有提供一个可视化的类似网站后台一样的操作平台，这对维护app后台数据带来极大不便。好在官方开发了数据云的API接口，AcAdmin便由此而生。    
**AcAdmin** 即 ApiCloud Admin的意思。    
使用AcAdmin可以无缝对接你的ApiCloud数据云，并想管理网站一样容易管理数据云。    
![登陆界面][2]

![初始化界面][3]


####运行环境
[AcAdmin][4]开源托管在开源中国，[点击下载][5]    
ApiCloud基于[ThinkPHP 3.2.3][6]开发，后台使用了基于Bootstrap 的 smart admin框架，并且定制了其他组件，具体请参考应用资源。    
开发环境如下：
OS X 10.10.3、apache 2.2 + 、php 5.3+，windows环境没测试过。


####使用说明

 1. 安装
AcAdmin无须后台数据库支持，将下载的安装包解药到网站根目录，当然也支持二级目录。
 2. 修改配置文件
 使用notepad++、sublime text 等之类的文本编辑器打开配置文件 。

> Apps/Admin/Conf/config.php  //根据提示修改

**后台初始化**
 首次使用需要初始化后台，以生成对应的表单。

 1. 创建必须的class，登陆ApiCloud后台，通过database管理新建两个class。
 2. 登陆AcAdmin后台，是ApiCloud的appid（用户名） 和 appkey（密码）登陆，即是高级管理，也和配置文件中的一致。
 3. 登陆后台之后，在项目初始化中项目管理进行项目添加、后台用户的添加。

需要新增的class
> class名称：ac_model
字段：name(string)、title(string)、fields(object)
class名称：ac_user
字段：account(string)、 password(string)、 email(string)

**表单设计**
后台新增的对象必须和ApiCloud的class的名称一致，添加完毕之后，刷新下整个页面，此时模型设计会多出子菜单，点击对于的模型即可对表单进行设计。    

 
####引用资源
 - jquery
 - jquery.bsgrid
 - bootstrap
 - notification
 - nprogress
 - jquery.bootstrap-growl
 - bootstrap-confirmation

####其他界面
![后台用户管理][7]

![应用管理][8]

![新增登陆用户][9]

![数据管理][10]

![用户退出][11]


  [1]: http://www.apicloud.com/
  [2]: http://static.oschina.net/uploads/space/2015/0727/165225_DEuu_1423274.png
  [3]: http://static.oschina.net/uploads/space/2015/0727/165226_SrNp_1423274.png
  [4]: https://git.oschina.net/anyhome/AcAdmin
  [5]: https://git.oschina.net/anyhome/AcAdmin
  [6]: http://www.thinkphp.cn/
  [7]: http://static.oschina.net/uploads/space/2015/0727/165227_HCWP_1423274.png
  [8]: http://static.oschina.net/uploads/space/2015/0727/165228_z8QT_1423274.png
  [9]: http://static.oschina.net/uploads/space/2015/0609/134138_6dl7_1423274.png
  [10]: http://static.oschina.net/uploads/space/2015/0727/165229_1gdN_1423274.png

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)