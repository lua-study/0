# [龙啸轩内容管理系统 V3.2](http://www.cxuu.top)

# 演示 [演示站点](http://cxuucms.cxuu.top/)

- 演示站点后台访问地址：http://cxuucms.cxuu.top/admin  用户名密码均为：test
- 演示站程序不是最新的，看到的内容会与实际程序有较大的不同！！


### ！！！变化较大，之前版本不支持无缝更新到V3.2！！！

- 基于 Z-PHP 和 layui构建，简单高效！！简单粗暴！！

- 适合公司企业站、企事业单位CMS站、新闻站、单位或公司内网站点，并可以根据实际需要二次开发微信、API接口等。

- 特别针对企事业内网优化和功能扩展

##### 目前，本系统已经过部分案例上线测试，可放心使用！

## 前端：

- 支持页面数据定制灵活调用；

- 视图页自动静态化，可动态开关和设置静态化时间；

- Redis\memcache\file文件缓存，可以自由定制（设置）缓存时间；

- 前端包括：文章、图集、成员显示、值班安排、访问统计等；（这些模块只是提供了一些实用场景的制作思路，你可以根据自己实际需要扩展所需要功能）

- 灵活路由方式；

- 独立搜索模块；

- 在线提交意见反馈；

- ......

## 后台：

- 灵活角色、管理员权限；

- 多语言支持

- 后台菜单灵活定制；

- JSON数据列表；

- 便捷的栏目管理； 

- 系统公告； 

- 灵活的系统设置； 

- 缓存管理； 

- 扩展功能包括：值班安排管理、图集管理、内部成员管理、意见反馈等； 

- 前台访问计数统计； 

- 数据库操作日志； 

- 上传图片缩略图及水印； 

- 其它功能。


## 环境需求：

- php 7.1+ (开发环境测试了7.1 7.2 7.3 7.4 建议7.4)

- mysql 5.6+ （开发环境用的是MariaDB 10.2+ mysql5.6+）

- Aapache\Nginx\IIS等（前台部分配置文件里'URL_MOD' => 2, 开启路由模式下需要环境Rewrite，后台默认不需要开启Rewrite）

- Redis（非必须）


## 开发文档：

系统采用PHP框架和UI框架非浸入式编写，可完全参照框架文档进行二次开发

### [Z-PHP框架](http://www.z-php.com)
[文档](https://www.showdoc.cc/zphp4):https://www.showdoc.cc/zphp4


## CXUUCMS V3 前端使用文档：

### 本系统使用比较简单，在程序内部和模板上都有相应注释。

这里主要说明一些较常用的前台使用方法，后台部分有特别使用的地方均做了相应提示，在使用上不会存在障碍！

- 前端一般采用php原生写法，也可以参照框架前端文档用框架约定方式输出，两者在性能上没有区别，只是个人习惯而已。

- 系统贯彻追求原生速度，在模板制作上均采取原始方法制作

#### 一、内容列表前端调用方法：
		    
		关于 selectData('3,6',5,60,1,3) 说明：
		  1、CID单个栏目直接填写数据 如： 2 ，多个栏目："3,6,5" 或 0全部栏目;
		  2、条数 支持偏移如："2,10";
		  3、缓存时间 600单位秒; 
		  4、是否图片 1; 
		  5、是否头条 1 或小头条 2 或 图片轮换 3;
		  
- 带栏目信息调用

		  foreach(\model\article::selectJoinData(7,5,60) as $vo){ 
			  echo $vo['catename']; //栏目名称
			  ...
			  }
		  $cid = 栏目ID   $limit  = 1,10条数,  $cache  = 缓存时间 秒



#### 二、值班安排调用（可根据实际使用场景自定义）

		   //在当前模板中获取到模型变量

			今日( ) 值班 - 
			公司领导：    
			部门领导：    
			值班员：    


#### 三、路由模式下的链接生成方法
		  1、echo urlInfo($vo['id']);  生成内容页链接
		  2、echo urlList($vo['id']);  生成列表页链接
		  3、echo urlImage($vo['id']);  生成图集内容页链接
		  4、echo urlFeedback($vo['id']);  生成留言反馈内容页链接


#### 四、截取字符长度
		  如：echo cxuuMbStr($vo['title'],20);  显示20个字符，支持中文
		  
#### 五、格式化时间显示
		  1、显示多久以前   echo hTime($info['time']);
		  2、格式化时间     echo fTime($vo['time'],'Y-m-d');  Y-m-d 为显示样式
		
#### 六、图集调用方法
		 
			 
				  " target="_blank"> " />  
				  " target="_blank">   
			 
		 

#### 七、分页（两种样式）
- 调用方法，在列表页加入以下这段代码即可（为了前端框架非依赖性，制作了除LAYUI分页外的单独分页CSS样式）：	

		 

- 分页样式适用所有类型列表，第二个参数0或空时为原生样式，1 为LAYUI样式 设置为1时，需要配置对应的 LAYUI JS参数（内容列表模板里有参考）

		CSS样式 \public\res\index\css\main.css：
		/*原生分页代码*/
		#page{margin:auto;height:50px;line-height:50px;}
		.manu {font-size:16px;PADDING-RIGHT: 3px; PADDING-LEFT: 3px; PADDING-BOTTOM: 3px; MARGIN: 3px; PADDING-TOP: 3px; TEXT-ALIGN: center}
		.manu A {PADDING-RIGHT: 5px; PADDING-LEFT: 5px; PADDING-BOTTOM: 2px; MARGIN: 2px; COLOR: #036cb4; PADDING-TOP: 2px; TEXT-DECORATION: none}
		.manu A:hover {COLOR: #fff;BACKGROUND-COLOR: #036cb4;}
		.manu A:active {BORDER-RIGHT: #036cb4 1px solid; BORDER-TOP: #036cb4 1px solid; BORDER-LEFT: #036cb4 1px solid; COLOR: #666; BORDER-BOTTOM: #036cb4 1px solid}
		.manu .current {PADDING-RIGHT: 5px; PADDING-LEFT: 5px; FONT-WEIGHT: bold; PADDING-BOTTOM: 2px; MARGIN: 2px; COLOR: #fff; PADDING-TOP: 2px; BACKGROUND-COLOR: #036cb4}
		.manu .current a{FONT-WEIGHT: bold; COLOR: #fff; }
		.manu .disabled {BORDER: #036cb4 1px solid; PADDING-RIGHT: 5px; PADDING-LEFT: 5px; PADDING-BOTTOM: 2px; MARGIN: 2px;  COLOR: #ddd; PADDING-TOP: 2px; }

#### 八、系统配置调用
		 //版权信息
		   //网站名称
		 ">
		 ">
		.......


#### 九、访问统计(异步方式)

- #### #html:
 		本站访问统计（PV值 缓存10分钟更新）
		今日访问：   
		昨日：   
		总访问：   
		最高日访问：  

- ##### jq:
		$.getJSON('/visit', {}, function (data) {
			$('.visit_today').text(data['today']);
			$('.visit_yesterday').text(data['yesterday']);
			$('.visit_sum').text(data['sum']);
			$('.visit_max').text(data['max']);
		})

#### 十、获取及设置数据缓存方法
		（这是一个基于框架提取出来的内置方法，可以将想要储存为缓存的任意数据进行缓存，与前端设置无关，当然，也可以灵活利用）
		1、设置缓存方法：
		  //自定义缓存健,要缓存的数据,缓存时间
		2、获取缓存方法：
		  //通过健名获取对应数据

#### 十一、其它前端模板用法可参考现有模板示例


# 本系统安装

- 网站要求环境伪静态支持！

### 目录绑定

- WEB目录请绑定在：/public

- 支持二级目录绑定

- 后台访问地址：xxx.com/admin.php

- 后台用户名：admin  密码：123456

### 数据库

- 创建一个数据库，再导入数据文件

- 数据库是根目录的cxuuweb-***.sql，直接导入数据库即可，数据库配置文件在根目录的common/config.php里！


### 注意：

- 前台默认开启了缓存及路由模式

  ！！如在使用中报错，请先检查根目录下的/common/config.php ('URL_MOD' => 2,'cache_mod'=>0,)等值；



# 系统截图（非实时更新）

![Image text](https://gitee.com/4856742/cxuucms-zphp/raw/master/public/demoimg/1.jpg)

![Image text](https://gitee.com/4856742/cxuucms-zphp/raw/master/public/demoimg/2.jpg)

![Image text](https://gitee.com/4856742/cxuucms-zphp/raw/master/public/demoimg/3.jpg)

![Image text](https://gitee.com/4856742/cxuucms-zphp/raw/master/public/demoimg/4.jpg)

![Image text](https://gitee.com/4856742/cxuucms-zphp/raw/master/public/demoimg/5.png)

![Image text](https://gitee.com/4856742/cxuucms-zphp/raw/master/public/demoimg/6.jpg)

![Image text](https://gitee.com/4856742/cxuucms-zphp/raw/master/public/demoimg/7.jpg)

![Image text](https://gitee.com/4856742/cxuucms-zphp/raw/master/public/demoimg/8.png)

![Image text](https://gitee.com/4856742/cxuucms-zphp/raw/master/public/demoimg/9.png)

![Image text](https://gitee.com/4856742/cxuucms-zphp/raw/master/public/demoimg/10.png)





 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)