##提示##
> 因为工作的原因，一直都没有时间去维护和更新的Jingle，后面很长一段时间内可能都没有太多的业务时间。
> 在这里对关注和使用Jingle的同学说一声抱歉！其实源码也不多，需要用到实际项目的同学建议通读源码，这样才能更好为项目服务，也能提升自己的能力不是？
> 当然，后续我也会尽量抽出时间来对Jingle做一些重构和规划，只是时间点上不太确定，再次说一声抱歉~

##Jingle UI##
Jingle UI是一个基于html5、css3开发轻量级的移动webapp 框架，提供一些基本交互方式，常用的组件(scroll,actionsheet,sidemenu,toggle,push2refresh......)，帮助您更方便的开发移动应用。

- 基于webkit开发，目前只支持ios，android
- 依赖zepto.js、iscroll4、artTemplate等开源类库和组件

> 持续开发中，文档尚不完善，有需求的朋友可以直接看demo和源码
> 
> [wiki入口](https://github.com/shixy/Jingle/wiki/_pages "wiki")

###部分案例###

**Eoe资讯**

访问地址：http://migrator.duapp.com/static/eoe/

源码地址：https://github.com/shixy/eoe-jingle

**深圳图书馆**
访问地址：http://shenzhenlib.duapp.com/

源码地址：已打包成apk，源码在https://github.com/shixy/szlib

###本地环境搭建###
因为涉及到跨域问题，需要服务端做一个代理。

我采用的是Nodejs,你可以根据自己的知识架构来做调整(Apache\Nginx等等)。

1. 安装nodejs插件

	> npm install;

2. 运行nodejs

	> node server.js

3. 浏览器访问：http://localhost:3000

###页面结构###
	  
	     
	        侧边栏
	     
	     
	        侧边栏
	     
	 
	  
	     
	         
	             
	                  
	             
	             Jingle 
	             
	                  
	             
	         
	         
	             book 
	             pencil 
	             more 
	         
	         
	             
	         
	     
	 

###布局组件###
section 基本页面

*基本属性:*

	data-transition:页面转场动画，默认为“slide”,
	目前框架已内置“slideUp”，“slideDown”,"scale"，亲们可以自己编写css3动画...

aside 侧边菜单

基本属性：

	data-position:  left(左侧边栏) right(右侧边栏)
	data-transition: push(抽屉式) overlay(侧边栏覆盖页面) reveal(页面退出显示侧边栏)
	data-show-close: true false (是否显示关闭按钮)

list 列表组件

	ul class="list" 基本设置
	li data-selected="selected" 点击会有高亮显示

###交互组件###
	 ok 
data-target的值有：

	section:页面跳转
	article:页面中的元素块切换
	menu:显示/隐藏侧边菜单
	link:执行a标签默认行为

	href对应section/article/menu的id

###界面元素###
导航栏

	 
	 
          Hello  
          Jingle  
          html5  
     
	 
	 
          
          
          
     
	 
	 
          Hello  
          Jingle  
          html5  
     
	 
	 
          Hello  
          Jingle  
          html5  
     

图标

	data-icon="icon name"
	icon name请参见示例中的icons页面，基本所有的组件都可以用

toggle

	  
	默认为√和×，可以自定义文字
	data-on="开启"
	data-off="关闭"

范围选择器

	 
         
     
	data-rangeinput: 输入框显示在左侧还是右侧

进度条

	  
	data-title:自定义进度文字

数字标签

	 按钮 
	data-orient:标签显示位置，默认显示在右上角

checkbox

	 爱我你就勾勾我 
	data-checkbox:unchecked(未选中) checked(选中)


###功能组件###
toast 消息提示框(单例)

	J.Toast.show(type,text,duration);
		//type: toast|success|error|info  内置的几种样式
		//text： 显示文本
		//duration:持续时间，为0则不自动关闭

	J.Toast.hide(); //关闭消息

popup 弹出框(单例)

	J.Popup.show(options);
	J.Popup.close();
	J.Popup.alert();
	J.Popup.confirm();
	J.Popup.popover();
	J.Popup.loading();
	J.Popup.actionsheet();

slider 轮换组件

	var slider = new J.Slider(selector);

scroll 滚动组件(下拉刷新)


 	自动装载模式：data-scroll=true
	javascript模式：J.Scroll(selector,opts);

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)