# cidingLayCheck

#### 介绍
layui 版本check多级复选框弹窗组件

#### 软件架构
依赖layui


#### 安装教程

1. 仍在服务下启动即可

#### 使用说明


![image](https://gitee.com/1174133584/cidingLayCheck/raw/master/img/1.png)
![image](https://gitee.com/1174133584/cidingLayCheck/raw/master/img/2.png)

face[good] 一个基于layui封装的checkbox复选组件。
/**
 * 复选框组件2.1 by Ciding
 * 2019-06-13
 * 参数dom 传入按钮id|class
 * 参数title 弹窗标题
 * 参数confObj 数组例如：[
		{url:'querydaibiaoxinbyidorname2',type:'POST',fieldId:'rdSparefield21',fieldName:'按区县',showFieldName:'rdSparefield4',hideFieldId:'rdId'},
		{url:'querydaibiaoxinbyidorname2',type:'POST',fieldId:'rdSparefield20',fieldName:'按职务',showFieldName:'rdSparefield4',hideFieldId:'rdId'},
		{url:'querydaibiaoxinbyidorname2',type:'POST',fieldId:'rdSparefield2',fieldName:'按界别',showFieldName:'rdSparefield4',hideFieldId:'rdId'},
		{url:'querydaibiaoxinbyidorname2',type:'POST',fieldId:'rdSparefield16',fieldName:'按学历',showFieldName:'rdSparefield4',hideFieldId:'rdId'}
	]
	url：数据源url
	type：请求方式
	fieldId：组件要存取的id
	fieldName：要存取或显示的name
	showFieldName：显示的分类name
	hideFieldId：模板要使用的唯一id
 * 参数checkedIds 传入选中数组的ids逗号分割即可 (与下面顺序可以不用对应)
 * 参数checkedNames 传入选中数组的names逗号分割即可 (与上面顺序可以不用对应)
 * fn callback
 * return 选中数组对象
 * 请慎重修改，需考虑扩展性和维护性进行合理修改。
 * @param exports
 * @returns
 */

DEMO：
layui.config({
  base: '../../../layui_exts/cidingLayCheck/'
}).extend({
  regionSelect: 'cidingLayCheck'
}).use(['cidingLayCheck'], function(){
       //引入模块
  	var cidingLayCheck = layui.cidingLayCheck;
       //自定义分组配置
  	var selectConf=[
		{url:'data.json',type:'GET',fieldId:'rdSparefield21',fieldName:'按区县',showFieldName:'rdSparefield4',hideFieldId:'rdId'},
		{url:'data.json',type:'GET',fieldId:'rdSparefield20',fieldName:'按职务',showFieldName:'rdSparefield4',hideFieldId:'rdId'},
		{url:'data.json',type:'GET',fieldId:'rdSparefield2',fieldName:'按界别',showFieldName:'rdSparefield4',hideFieldId:'rdId'},
		{url:'data.json',type:'GET',fieldId:'rdSparefield16',fieldName:'按学历',showFieldName:'rdSparefield4',hideFieldId:'rdId'}
	];
        //初始化组件
	cidingLayCheck.initCheck('#checkBtn','请选出席人员',selectConf,'','',function(users){
		//这是回调
	});
  
});

看demo的话把文件丢到服务器或者本地localhost访问即可食用！




#### 参与贡献

1. Fork 本仓库
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


#### 码云特技

1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)