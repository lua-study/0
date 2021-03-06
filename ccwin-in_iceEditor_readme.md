
# iceEditor富文本编辑器

#### 官方
+ iceEditor 官方网站 [https://www.iceui.net/iceEditor.html](https://www.iceui.net/iceEditor.html)
+ iceEditor 示例文档 [https://www.iceui.net/iceEditor/doc.html](https://www.iceui.net/iceEditor/doc.html)

#### 介绍
iceEditor是一款简约风格的富文本编辑器，体型十分娇小，无任何依赖，整个编辑器只有一个文件，功能却很不平凡！简约的唯美设计，简洁、极速、使用它的时候不需要引用jQuery、font、css……等文件，因为整个编辑器只是一个Js，支持上传图片、附件！支持添加音乐、视频！
iceEditor官方群：324415936

#### 优点
+ 纯原生开发，无任何依赖，冰清玉洁
+ 响应式布局，适应任何分辨率的设备
+ 整个编辑器只有一个文件，高效便捷
+ 简约的唯美设计，简洁、极速

#### 更新
# iceEditor v1.1.4
+ **2020-05-22**
+ [修复] 拖拽编辑器的高度时，造成鼠标丢失焦点BUG
+ **2020-05-18**
+ [修复] 视频上传type未定义BUG
+ [修复] 图片上传完成后造成的iframe为空报错
+ **2020-04-22**
+ [新增] 插件机制，可更好的定制开发菜单栏（开发文档努力写作中，后续贴出，以下贴出简单示例）
+ [新增] 配置项css，可自由设计编辑器的风格样式
+ [修复] 粘贴文本造成换行BUG
+ [修复] 上个版本升级造成的个别样式错误
+ [重写] 菜单栏内核，转为插件设计
+ [优化] 一些逻辑代码，提升加载速度
+ [优化] 样式代码，精简一部分多余样式
+ **2020-04-21**
+ [修复] 代码查看模式粘贴代码造成空白的BUG
+ **2020-04-20**
+ [新增] 添加视频解析功能，可直接添加b站和优酷的播放地址链接（其它视频平台将会陆续添加）
+ [优化] 编辑器样式，全部添加前缀，防止污染
+ [修复] 附件和图片上传失败所造成的BUG
+ [修复] upload.php文件返回json格式
+ [查看其它更新](https://www.iceui.net/iceEditor/update.html) 

#### 提示
[iceui](https://gitee.com/iceui/iceui) 前端框架已经已集成该编辑器。

#### 注意
iceEditor.js的引用禁止放在head标签内，请尽量放在body中或body后面！

#### 使用
```html
  欢迎使用iceEditor富文本编辑器  
```
```javascript
//第一步：创建实例化对象
var e = new ice.editor('content');

//第二步：配置图片或附件上传提交表单的路径
//如果你的项目使用的php开发，可直接使用upload.php文件
//其它的编程语言需要你单独处理，后期我会放出.net java等语言代码
//具体与你平常处理multipart/form-data类型的表单一样
//唯一需要注意的就是：处理表单成功后要返回json格式字符串，不能包含其它多余的信息：
//url：文件的地址
//name：文件的名称（包含后缀）
//error：上传成功为0，其它为错误信息，将以弹窗形式提醒用户
//例如批量上传了两张图片：
//[
//	{url:'/upload/img/153444.jpg', name:'153444.jpg', error:0},
//	{url:'/upload/img/153445.jpg', name:'153445.jpg', error:'禁止该文件类型上传'}
//]
e.uploadUrl="/iceEditor/src/upload.php";

//第三步：配置菜单（默认加载全部，无需配置）
e.menu = [
  'backColor',                 //字体背景颜色
  'fontSize',                  //字体大小
  'foreColor',                 //字体颜色
  'bold',                      //粗体
  'italic',                    //斜体
  'underline',                 //下划线
  'strikeThrough',             //删除线
  'justifyLeft',               //左对齐
  'justifyCenter',             //居中对齐
  'justifyRight',              //右对齐
  'indent',                    //增加缩进
  'outdent',                   //减少缩进
  'insertOrderedList',         //有序列表
  'insertUnorderedList',       //无序列表
  'superscript',               //上标
  'subscript',                 //下标
  'createLink',                //创建连接
  'unlink',                    //取消连接
  'hr',                        //水平线
  'table',                     //表格
  'files',                     //附件
  'music',                     //音乐
  'video',                     //视频
  'insertImage',               //图片
  'removeFormat',              //格式化样式
  'code',                      //源码
  'line'                       //菜单分割线
];

//第四步：创建
e.create();
```

#### 设置编辑器尺寸
```javascript
var e = new ice.editor('content');
e.width='700px';   //宽度
e.height='300px';  //高度
e.create();
```

#### 禁用编辑器
```javascript
var e = new ice.editor('content');
e.disabled=true;
e.create();
```

#### 获取内容
```javascript
var e = new ice.editor('content');
console.log(e.getHTML());  //获取HTML格式内容
console.log(e.getText());  //获取Text格式内容
```

#### 设置内容
```javascript
var e = new ice.editor('content');
e.setValue('hello world！');
```

#### 追加内容
```javascript
var e = new ice.editor('content');
e.addValue('hello world！');
```

#### 插件开发
```javascript
var e = new ice.editor('content');
e.addValue('hello world！');

//┌────────────────────────────────────────────────────────────────────────
//│ e.plugin(options)传参说明
//│────────────────────────────────────────────────────────────────────────
//│ options     {json}
//│  ├ name     {string}   [必填]菜单唯一的name，可配置menu项显示与顺序
//│  ├ menu     {string}   [必填]展示在菜单栏上的按钮，可为图标或者文字
//│  ├ data     {string}   execCommand的命令
//│  ├ id       {string}   菜单按钮上的id
//│  ├ css      {string}   菜单按钮上的class
//│  ├ style    {string}   该插件的style，以css文件中的样式形式书写
//│  ├ dropdown {string}   下拉菜单里的html，如果定义了popup，则该参数失效
//│  ├ popup    {json} 弹窗json
//│  │    ├ width   {int}    弹窗的宽度
//│  │    ├ height  {int}    弹窗的高度
//│  │    ├ title   {string} 弹窗上的标题
//│  │    └ content {string} 弹窗的内容，可为html
//│  ├ click   {function} 按钮点击事件
//│  └ success {function} 插件安装成功后会自动执行该方法
//└────────────────────────────────────────────────────────────────────────

//function方式
e.plugin({
	menu:'function方式',
	name:'click',
	click:function(e,z){
		z.setText('hello world');
	}
});
//execCommand命令
e.plugin({
	menu:'删除命令',
	name:'del',
	data:'delete'
});
//下拉菜单类型
e.plugin({
	menu:'下拉菜单',
	name:'dropdown',
	dropdown:' 复制选中的文字 ',
});
//弹出层类型
e.plugin({
	menu:'弹窗演示',
	name:'popup',
	style:'.demo-p{margin-bottom:10px}.demo-button{padding:0 10px}',
	popup:{
		width:230,
		height:120,
		title:'我是一个demo',
		content:' 在光标处插入hello world!   确定 ',
	},
	success:function(e,z){
		//获取content中的按钮
		var btn = e.getElementsByTagName('button')[0];
		//设置点击事件
		btn.onclick=function(){
			z.setText('hello world');
			//关闭本弹窗
			e.close()
		}	
	}
});
e.create();
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)