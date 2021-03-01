# teamsalt

-----

## 什么是teamsalt？
teamsalt是一个在线的团队写作任务管理系统。  
teamsalt是team+salt(盐)，寓意就是作为盐一样，成为团队中不可缺少的系统。
系统设计参考了[teambition](http://teambition.com)、[tower](http://tower.im)、[worktile](http://worktile.com)、[fengcheco](http://fengcheco.com)等。

## 长什么样呢？
![](http://zhaopengblog.u.qiniudn.com/demoteamsalt.png) 

[http://teamsalt.duapp.com/](http://teamsalt.duapp.com/) 
user: admin  
password: 1

搭建在bae上面，使用bae2.0，可能访问不太稳定，打算迁移到其他平台上面。

## 技术选型
1. 后台
	- [jfinal](http://jfinal.com) 基本可以负担后台
2. 前台
	- [sea](http://seajs.org)
	- [backbone](http://backbonejs.org)
	- jquery
	- underscore
	- ...
3. 部署打包
	- grunt 使用grunt完成压缩、合并等。
4. 数据库
	- mysql

## 后台开发说明
后台使用jfinal进行开发，具体开发，请查看[jfinal开发手册](http://www.jfinal.com/doDownload?file=jfinal-1.8-manual.pdf)，30分钟就可以阅读完了。

### 目录结构
```
.
├── com
│   └── teamsalt
│       ├── common
│       │   ├── Message.java						// 请求返回 json 对象封装类
│       │   ├── TeamsaltConfig.java					// jfinal 配置
│       │   └── TeamsaltConstants.java				// 常量类
│       ├── controller
│       │   ├── CommentController.java				// 评论 controller
│       │   ├── IndexController.java				// 首页 controller
│       │   ├── InviteController.java				// 邀请用户 controller
│       │   ├── ProjectController.java				// 项目 controller
│       │   ├── TaskController.java					// 任务 controller
│       │   ├── TasklistController.java				// 任务列表 controller
│       │   └── UserController.java					// 用户 controller
│       ├── filter
│       │   ├── MainFilter.java						// 使用Filter过滤main.html页面,解决jfinal无法过滤静态html的问题
│       │   └── xss									// XSS 过滤拦截
│       │       ├── CrossScriptingFilter.java
│       │       ├── HTMLFilter.java
│       │       └── RequestWrapper.java
│       ├── interceptor
│       │   ├── CheckLoginInterceptor.java			// 当访问/login页面的时候,判断是否已经登录,已经登录,则跳转到/home
│       │   └── GlobalLoginInterceptor.java			// 全局用户登录拦截器
│       ├── kit										// 常用的一些工具类
│       │   ├── ConfigKit.java
│       │   ├── ContextKit.java
│       │   ├── CookieKit.java
│       │   ├── DateKit.java
│       │   ├── HtmlTagKit.java
│       │   ├── PwdKit.java
│       │   └── UuidKit.java
│       └── model									// model 层的各种对象
│           ├── Comment.java
│           ├── Invite.java
│           ├── InviteUser.java
│           ├── Project.java
│           ├── ProjectTasklist.java
│           ├── ProjectUser.java
│           ├── Task.java
│           ├── Tasklist.java
│           ├── TasklistTask.java
│           └── User.java
├── log4j.properties								// log4j 配置
└── S.java											// 采用 jetty 的启动类

```

代码开发比较简单，具体查看jfinal手册就能进行代码开发了。  

## 前台开发说明
前台采用单页面应用程序(SPA)的开发方式，完全可以和后台分离出来，部署在不同的服务器上面，而且可以将前台用 phonegap 之类的工具，打包成android、ios、winPhone等的应用，起初也就是这么设计的。

js 文件的代码路径是在`teamsalt/WebContent/js` 中，具体说明如下。

### js 目录结构
```
.
├── app								// 这个是压缩代码后产生的文件地方
│   ├── common
│   ├── model
│   ├── object
│   ├── router
│   ├── ui-component
│   ├── view
│   └── widget
├── dist							// 这个是压缩时候的临时文件
│   ├── common
│   ├── model
│   ├── object
│   ├── router
│   ├── ui-component
│   ├── view
│   └── widget
├── gallery							// 这个是需要的插件包
│   ├── backbone
│   ├── bootbox
│   ├── bootstrap
│   ├── contextmenu
│   ├── datepicker
│   ├── dropdownx
│   ├── notify
│   ├── perfect-scrollbar
│   ├── popbox
│   ├── select
│   ├── tags
│   ├── template
│   ├── underscore
│   └── xdate
├── jquery							// jquery 
│   └── jquery
├── node_modules					// 使用 grunt 需要的插件，已经提供
│   ├── grunt
│   ├── grunt-cmd-concat
│   ├── grunt-cmd-transport
│   ├── grunt-contrib-clean
│   └── grunt-contrib-uglify
├── seajs							// seajs 
│   ├── 1.3.1
│   ├── plugin-log
│   ├── seajs
│   └── seajs-text
└── src								// 这个是程序的源代码了
    ├── common						// 公共工具
    ├── model						// model 层
    ├── object						// 自定义的一个 map 对象
    ├── router						// 路由器
    ├── ui-component				// 自定义的 ui 组件
    ├── view						// view 层
    └── widget						// 自定义的 widget 组件

```

### js 开发
采用 seajs 和 backbone 进行代码架构，同后台同样的 mvc 模式开发。

#### model 层
`user.js`

```
define(function(require, exports, module) {

	var $ = require('jquery');
	var _ = require('underscore');
	var Backbone = require('backbone');

	var User = Backbone.Model.extend({
		getUser : function(params, success) {
			var url = '/user/profile/';
			var self = this;
			Util.query.g(url, '', function(result) {
				success(result.other, params);
			});
		},
		getUsersByProjectIdAndTaskId : function(params, success, error) {
			this.fetch({
				url : '/data/' + Util.curProjectId + '-users.json',
				success : function(model, response, options) {
					success(response);
				},
				error : function(XMLHttpRequest, textStatus, errorThrown) {
					error(arguments);
				}
			});
		},
		getUsersByProject : function(params, success, error) {
			var url = '/user/getProjectUsers';
			Util.query.g(url, params, function(result) {
				success(result.other);
			});
		},
		// 得到所有用户
		getAllUser : function(params, success) {
			var url = '/user/getAllUser';
			Util.query.g(url, '', function(result) {
				success(result.other);
			});
		}
	});
	module.exports = User;
})
```

#### control 层
虽然叫做 view 但是在架构上面，担任的是 contro 层的功能。

`layout.js`

```
/**
 * @author zhaopeng
 * @datetime 2013-08-27
 * @description 程序任务主界面入口
 */
define(function(require, exports, module){

	var $ 			= require('jquery');
	var _ 			= require('underscore');
	var Backbone 	= require('backbone');
	var Bootstrap 	= require('bootstrap');

	// 布局模板
	var layoutHtml 	= require('./tpl/layout.html');

	// 模板
	var ProjectBar 	= require('./header/projectBar');// header左侧项目切换bar
	var UserinfoBar = require('./header/userinfoBar');// header右侧用户信息bar
	var SidebarTasklist 	= require('./sidebar/sidebar-tasklist');// 左侧侧边栏
	var SidebarUser 	= require('./sidebar/sidebar-user');// 左侧侧边栏
	var ListPanel 	= require('./container/listPanel');// container左侧列表
	var DetailPanel = require('./container/detailPanel');// container右侧详情
	var CommonView = require('./commonView');// 公共组件VIEW

    //模型
    var Comment =  require('../model/comment');
    var Project =  require('../model/project');
    var Task =  require('../model/task');
    var Tasklist =  require('../model/tasklist');
    var User =  require('../model/user');

	var Laoyout = Backbone.View.extend({
		el: 'body',
        events:{
        	'updateCommon #sidebar':'updateCommon',
        	'updateCommon #list-panel':'updateCommon',
            'updateCommon #detail-panel':'updateCommon',
            'deleteTask #detail-panel':'deleteTask',
             'updateTask #detail-panel':'updateTask'
        },			
        initialize: function() {
            this.$el.html(Util.tpl.t(layoutHtml,{})).hide().show('1000');
            // 初始化模型,全部记载到map中
            this.comment  =  new Comment();
            this.project  =  new Project();
            this.task     =  new Task();
            this.tasklist =  new Tasklist();
            this.user     =  new User();

            Util.Models.put('comment',this.comment);
            Util.Models.put('project',this.project);
            Util.Models.put('task',this.task);
            Util.Models.put('tasklist',this.tasklist);
            Util.Models.put('user',this.user);
            
            // 初始化布局界面
            this.projectBar = new ProjectBar();
            this.userinfoBar = new UserinfoBar();
            this.sidebarTasklist = new SidebarTasklist();
            this.sidebarUser = new SidebarUser();
            this.listPanel = new ListPanel();
            this.detailPanel = new DetailPanel();

            Util.Views.put('projectBar',this.projectBar);
            Util.Views.put('userinfoBar',this.userinfoBar);
            Util.Views.put('sidebarTasklist',this.sidebarTasklist);
            Util.Views.put('sidebarUser',this.sidebarUser);
            Util.Views.put('listPanel',this.listPanel);
            Util.Views.put('detailPanel',this.detailPanel);
        },
        updateCommon:function(e){
        	CommonView.init();
        },
        //删除任务后,同步删除列表中的数据
        deleteTask:function(e,result){
        	this.listPanel.deleteTask(result.uuid);
        },
        //更新任务后,同步更新列表中的数据
        updateTask:function(e,result){
        	this.listPanel.updateTask(result);
        }
	});

	module.exports = Laoyout;
})

```

#### view 层
使用 artTemplate 模板引擎，模板文件都存放在对应的 `tpl` 文件夹下。

`layout.html`

```
   
     
     
       
         Toggle navigation 
          
          
          
       
      
     
    
     
     
       

       
       teamsalt 
       
      	
       
          
   


   
     
     
     
         
   
   
     
     
        
     
   
    
```


### 使用 grunt 打包文件项目

#### 1. 安装nodejs
根据系统到 [http://nodejs.org/](http://nodejs.org/) 下载安装对应的 nodejs。我用的是 linux 编译后的版本，在 `.bashrc` 将 nodejs 添加到环境变量就好了。 如果是 windows 直接安装就可以了。

#### 2. 安装grunt命令行工具grunt-cli

使用-g全局安装，这样可以在任何一个目录里使用了。命令: `npm install -g grunt-cli`


需要注意的是在 linux 或 mac 下有时会报没有权限的错误，这时须在前面加一个 `sudo`

#### 3. 安装grunt
代码中已经包含了 grunt 需要的插件，所有只需要安装 grunt 就可以了。

进入目录，使用命令: `npm install grunt --save-dev`

至此，安装完毕。

#### 4. 打包 js 文件
在 Gruntfile.js 中提供了一下几个命令。

```
grunt build-t		// 执行 transport
grunt build-c		// 执行 concat
grunt build-u		// 执行 uglify
grunt build-min		// 执行压缩
grunt build-all		// 执行以上所有命令
grunt				// 执行 clean， 删除 app 和 dist 目录
```

**压缩提醒**
1. 压缩合并后的代码是放在 `teamsalt/WebContent/js/app/` ，如果部署只需要将`app.js`上传到服务器就可以了。
2. 在本地如何切换开发环境何生产环境的js代码。
```
		// For development
		if (location.href.indexOf("?pro") > 0) {
			seajs.use("app/app");
		}
		// For production
		else {
			seajs.use("src/app");
		}
```

## 未来计划
对目前此系统暂停开发，全心专注进行第二个版本的开发，第二个版本具有更好的架构设计，更轻快的开发速度，更多的功能特性。在基本版本完成之后，同样也会选择开源的方式进行发布。











 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)