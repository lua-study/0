Hsycms v3.0 实现全站生成静态网页，也可伪静态访问两种方式自由切换。推荐生成静态化可提高网页打开速度，有利于SEO收录。全新后台界面，后台可随意切换风格。支持后台菜单缓存。

作者官方网址：http://www.hsycms.com 

官网交流QQ群：597208036

![hsycms](http://www.hsycms.com/upload/20190723/9b18ba210b6abd209aabb000ad4b6456.jpg)


一、安装环境准备

Hsycms是由ThinkPHP5.0框架开发的，所有环境必须支持PHP+MYSQL5.0,PHP必须大于5.4 否则无法运行，环境必须支持伪静态功能

 

二、安装程序

安装程序时请先删除目录 app/common/install.lock 文件，这时打开首页输入 index.php/install 执行安装操作

默认后台帐号请输入admin 具有最高管理权限

安装完成后会在目录app/common/install.lock 下创建一个install.lock 文件，请勿删除。安装后会自动更改数据库配置文件 app/database.php

 

二、安装失败操作

a、如果程序安装失败，请检查数据库帐号和用户名及密码是否填写正确。

b、如果安装程序出错请使用第二种方法，首先本地数据库文件用工具导出，然后手动导入空间数据库。再修改数据库配置文件，app/database.php，然后在app/common/ 目录创建install.lock文件及可。


三、标签的使用

1、文章调用

 
{sy:list nid="83" cid="2" at="ishome" name="vo" sort="sort desc,id desc" num="0,4"} 

  {$vo.title} 标题
  {$vo.img}   图片
  {$vo.note}  简介
  {$vo.datetime|date='Y-m-d H:i:s',###} 时间   
  {$vo.......}更多字段请查看数据库 article 表字段。

{sy:list}
 

参数说明：
---------------------------------
nid  栏目ID
cid  栏目分类ID
at   文章属性【ishome首页，isvouch推荐，istop置顶】 
sort 排序 sort desc,id desc 根据sort,id排序降序 
num  调取数量,默认不写调取10条数据
name 必写

2、分类调用

 
{sy:cate nid="83" name="vo" num="4"} 

  {$vo.title}   标题
  {$vo.entitle} 英文标题，即分类网址URL
  {$vo.img}   图片
  {$vo.note}  简介  
  {$vo.......}更多字段请查看数据库 cate 表字段。

{/sy:cate}
 

参数说明：只能获取一级分类，多级请自行编写代码
---------------------------------
nid  栏目ID
num  调取数量,默认不写调取10条数据
name 必写

3、单篇调用

 
{sy:one aid="1" name="vo"} 

  {$vo.title}   标题
  {$vo.img}   图片
  {$vo.note}  简介  
  {$vo.......}更多字段请查看数据库 article 表字段。
  
{/sy:one}
 

参数说明：
---------------------------------
aid  文章ID
name 必写

4、友情连接

 
{sy:link name="vo" num="10"} 
  {$vo.title}   标题
  {$vo.url}     URL
  {$vo.img}     图片
{/sy:link}
 

参数说明：
---------------------------------
name 必写
num  数量


5、url 写法

{:u(栏目英文名,文章id)}  

例如:

href='{:u('product','')}' 表示跳转产品页  

href='{:u('product',2)}' 表示跳转产品详情页  

注：如果是手机站请{:u('product',2,1)} 在后面加个1表示手机url调用


四、网站全局配置信息字段

 

获取方法 如：{:config('webtitle')}

-----------------------------------------------------

{:config('webtitle')}          //网站标题

{:config('weburl')}            //网站域名

{:config('weblogo')}         //网站LOGO

{:config('webkeywords')}    //网站关键字

{:config('webdescription')} //网站描述

{:config('webcppyright')}  //网站底部信息

 

....更多字段请参考表 config


五、模板制作

模板目录为 app/index/view/

 app/index/view/index   PC模板目录

 app/index/view/mobile 手机模板目录

 

如下图：

![hsycms](http://www.hsycms.com/upload/20190731/1564576902852562.png)

static/index/ 下面 放置PC端图片，样式，JS等。

static/mobile/ 下面 放置PC端图片，样式，JS等。

列表模板是 listxxx.html  内容模板是 showxxx.html,

index.html 首页 

head 公共头部  模板调用时{include file="index@index/head"}

foot 公共头部  模板调用时{include file="index@index/foot"}

map 为地图插件{include file="index@index/map"}


默认模板为: 

listarticle.html 文章模板

listdownload.html 下载模板

listvideo.html 视频模板

listproduct.html 产品模板

listonepage.html 单页模板

showarticle.html 

.....

当然所有模板名称在后台导航管理都可自行定义和修改。

六、列表获取标签 


1、分类获取方法.

a.如果文章带分类

 
{volist name="leftlist" id="v"}

  {$v.title} 分类标题

    {:u($v.entitle)} 分类连接  

   {volist name="v['son']" id="s"}

    {$s.title} 分类标题

    {:u($s.entitle)} 分类连接  

    {/volist}

{/volist}
 
 

b.如果单页文章不带分类

 
{volist name="leftlist" id="v"}

  {$v.title} 分类标题

  {:u($v.entitle,$v.id)}  分类连接  

{/volist}
 
 

2、列表获取方法.

 
{volist name="list" id="v"}

  {$v.title} 标题

   {:u($entitle,$v.id)} 连接 

  {$v.img}  图片

  {$v.note} 简介

  {$v.datetime|date='Y-m-d H:i:s'} 时间 

  ......更多字段请参考 article 表

{/volist}
 
 

3、分页

 
 {$page}
  

4、栏目名称

 
{$columnName}栏目名 {$cateName} 分类名
 

七、获取文章详情

 

{$one.title} 标题

{$one.note} 简介

{$one.datetime|date='Y-m-d H:i:s',###} 时间

{$one.img} 单图

多图

{volist name="image" id="v"}

  {$v}

{/volist}

{$one.content|htmlspecialchars_decode} 内容
 

......更多字段请参考表 article

上下篇

 
{$pn.prev.url}   上一篇连接

{$pn.prev.title} 上一篇标题

{$pn.next.url}   下一篇连接

{$pn.next.title} 下一篇标题

 



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)