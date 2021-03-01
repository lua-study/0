# layer-popup

#### 介绍
基于layer实现常用弹出框类

v1.0版本： https://www.jq22.com/jquery-info21824

后续更新都会在该开源项目中体现

#### 软件架构
html/css+javascript+layer


#### 安装教程

1. 直接下载运行

#### 使用说明

```javascript
Layer弹出框类[基于layer实现常用弹出框类]
@author Xqs
@date 2018.08.26
@version 1.0
layer提供了5种层类型。可传入的值有：0（信息框，默认）1（页面层）2（层）3（加载层）4（tips层）。
若你采用layer.open({type: 1})方式调用，则type为必填项（信息框除外）

var icon = -1;//图标。信息框和加载层的私有参数。类型：Number，默认：-1（信息框）/0（加载层）
var time = 0;//自动关闭所需毫秒。类型：Number，默认：0默认不会自动关闭
var anim = 0;//弹出动画。类型：Number。 取值：0 平滑放大（默认）、1从上掉落、2从最底部往上滑入、3从左滑入、4从左翻滚、5渐显、6抖动
var loadingIndex;//加载层序号，便于关闭
layer.config({
   anim: 5, //默认动画风格
   // skin: 'layui-layer-molv' //皮肤layui-layer-lan，layui-layer-molv（默认）
});
var dialog = {
   /**
    * #提示框 - layer.msg(content, options, end)
    */
   /**
    * 提示框[一些简单的提示信息]
    * @param message 提示内容
    * @param icon icon
    * @param time 自动关闭所需毫秒（如果不配置，默认是3秒）
    * @param func 自动关闭后执行特定的函数 string(函数名),bool(false)表示不执行
    */
   msg : function(message, icon, time = 0, func = false){
       var index = layer.msg(message, {
           icon: icon,
           time: time, //3秒关闭
       }, function(){
           if(func != false){
               var f = eval(func);
           }
       });
   },
   /**
    * 提示框[带按钮的提示信息]
    * @param message 提示内容
    * @param icon icon取[-1,0,1,2,3,4,5,6]
    * @param btn 确定按钮名称,取消按钮名称
    * @param func 自动关闭后执行特定的函数 string(函数名),bool(false)表示不执行
    * @param time 自动关闭所需毫秒,这里不需要关闭（如果不配置，默认是0秒）
    */
   msgBtn : function(message, icon, func = false, btn = ['确定','取消'], time = 0){
       var index = layer.msg(message, {
           icon: icon,
           btn: btn,
           time: time,
           yes: function(){
               if(func != false){
                   var f = eval(func);
               }else{
                   layer.close(index);
               }
           }
       });
   },
   /**
    * #普通信息框 - layer.alert(content, options, yes)
    */
   /**
    * 普通信息框
    * @param message 提示内容
    * @param title 信息框标题,为false时不显示标题
    * @param icon 图标[0=>黄色?;1=>绿色?;2=>红色?;3=>黄色?;4=>黑色??;5=>红色?;6=>绿色??]
    * @param time 自动关闭所需毫秒，默认为0 表示不关闭
    */
    alert : function(title, content, icon = 0, func = false, time = 0){
       var index = layer.alert(content, {
           icon: icon,
           title: title,
           time: time
       },
       function(index){
           //do something
           if(func != false){
               var f = eval(func);
           }else{
               layer.close(index);
           }
       });
    },
   /**
    * #询问框 - layer.confirm(content, options, yes, cancel)
    */
   /**
    * 询问框
    * @param message 提示内容
    * @param title 信息框标题,为false时不显示标题
    * @param icon 图标[0=>黄色?;1=>绿色?;2=>红色?;3=>黄色?;4=>黑色??;5=>红色?;6=>绿色??]
    * @param yes 点击确定按钮后执行的函数名,如不需执行传入false即可。
    * @param no 点击取消按钮后执行的函数名,如不需执行传入false即可。
    * @param time 自动关闭所需毫秒，默认为0 表示不关闭
    */
   confirm : function(title, content, icon = 0, yes = false, no = false, time = 0){
       var index = layer.confirm(content, {
           icon: 3,
           title: title,
           time: time
       },
       function(index){
           //do something
           if(yes != false){
               var f = eval(yes);
           }else{
               layer.close(index);
           }
       },
       function(index){
           //do something
           if(no != false){
               var f = eval(no);
           }else{
               layer.close(index);
           }
       });
   },
   /**
    * #加载层 - layer.load(icon, options)
    */
   /**
    * 加载层
    * @param message 提示内容
    * @param title 信息框标题,为false时不显示标题
    * @param icon 加载图标
    * @param time 自动关闭所需毫秒，默认为0 表示不关闭
    */
    load : function(icon, func, time = 0){
       var index = layer.load(icon, {
           time: time,
           // shade: [opacity, color] //0.1透明度的白色背景
       });
    },
   /**
    * #tips层 - layer.tips(content, follow, options)
    */
   /**
    * tips层
    * @param id 
    * @param content 提示内容
    * @param tips 
    * @param color 
    */
    tips : function(id, content, tips = 1, color = '#000000'){
       layer.tips(content, id, {
           tips: [tips, color],
           tipsMore: true
       });
    },
   /**
    * #输入层 - layer.prompt(options, yes)
    */
   /**
    * 输入层
    * @param formType //输入框类型，支持0（文本）默认1（密码）2（多行文本）
    * @param title 输入层标题,为false时不显示标题
    * @param value 初始时的值，默认空字符 
    * @param area 自定义文本域宽高,formType为2时有效
    * @param maxlength: 140, //可输入文本的最大长度，默认500
    */
   prompt : function(formType = 1, title = false, value = '', func =false, area = []){
       layer.prompt({
           formType: formType,
           value: value,
           title: title,
           area: area //自定义文本域宽高
       }, function(value, index, elem){
           alert(area);
           //do something
           if(func != false){
               console.log(value); //得到value
               var f = eval(func);
           }else{
               layer.close(index);
           }
       });
   },
   /**
    * #tab层 - layer.tab(options)
    * 此层开发难度较大，不适合作为通用案例。请按需开发
    */
   /**
    * tab层
    * @param formType //输入框类型，支持0（文本）默认1（密码）2（多行文本）
    * @param title 输入层标题,为false时不显示标题
    * @param value 初始时的值，默认空字符 
    * @param area 自定义文本域宽高,formType为2时有效
    * @param maxlength: 140, //可输入文本的最大长度，默认500
    */
    tab : function(){
       layer.tab({
           area: ['600px', '300px'],
               tab: [{
               title: 'TAB1', 
               content: '内容1'
           }, {
               title: 'TAB2', 
               content: '内容2'
           }, {
               title: 'TAB3', 
               content: '内容3'
           }]
           }); 
    },
   /** 信息框[type:0]
   icon: 0-6
   **/
   /**
    * 成功弹出框[一般用于操作成功且不需要跳转的提示]
    * @param message 提示内容
    * @param title 信息框标题
    * @param level 提示级别
    * @param time 自动关闭所需毫秒，默认为0 表示不关闭
    */
   success : function(message, title = '', time = 0) {
       if(typeof(title) == "undefined" || title == false || title.trim() == 0 || title.trim() == ''){
           title = '信息';
       }
       layer.open({
           type: 0,
           icon: 1,
           title: title,
           content: message,
           time : time,
       });
   },
   /**
    * 信息弹出框[一般用于普通操作的提示]
    * @param message 提示内容
    * @param title 信息框标题
    * @param time 自动关闭所需毫秒，默认为0 表示不关闭
    */
    info : function(message, title = '', time = 0){
       if(typeof(title) == "undefined" || title == false || title.trim() == 0 || title.trim() == ''){
           title = '信息提示';
       }
       layer.open({
           type : 0,
           icon : 0,
           title : title,
           content : message,
           time : time,
       });
    },
   /**
    * 警告弹出框[一般用于警告提示]
    * @param message 提示内容
    * @param title 信息框标题
    * @param time 自动关闭所需毫秒，默认为0 表示不关闭
    */
    warming : function(message, title = '', time = 0){
       if(typeof(title) == "undefined" || title == false || title.trim() == 0 || title.trim() == ''){
           title = '警告提示';
       }
       layer.open({
           type : 0,
           icon : 5,
           title : title,
           content : message,
           time : time,
       });
    },
   /**
    * 错误弹出框[一般用于操作出现错误时的提示]
    * @param message 提示内容
    * @param title 信息框标题
    * @param time 自动关闭所需毫秒，默认为0 表示不关闭
    */
   error : function(message, title = '', time = 0) {
       if(typeof(title) == "undefined" || title == false || title.trim() == 0 || title.trim() == ''){
           title = '错误提示';
       }
       layer.open({
           type : 0,
           icon : 2,
           title : title,
           content : message,
           time : time,
       });
   },
   /**
    * 成功弹出框[一般用于操作成功且需要跳转的提示]
    * @param message 提示内容
    * @param url 点击确认后跳转的URL链接
    * @param title 信息框标题
    * @param time 自动关闭所需毫秒，默认为0 表示不关闭
    */
   successGo : function(message, url, title = '', time = 0) {
       if(typeof(title) == "undefined" || title == false || title.trim() == 0 || title.trim() == ''){
           title = '信息';
       }
       layer.open({
           type: 0,
           icon: 1,
           title: title,
           content: message,
           time : time,
           yes: function(){
               location.href = url;
           },
           cancel: function(index, layero){
               layer.close(index)
               return false;
           },
       });
   },
   /**
    * 信息弹出框[一般用于普通操作之后需要跳转的提示]
    * @param message 提示内容
    * @param url 点击确认后跳转的URL链接
    * @param title 信息框标题
    * @param time 自动关闭所需毫秒，默认为0 表示不关闭
    */
    infoGo : function(message, url, title = '', time = 0){
       if(typeof(title) == "undefined" || title == false || title.trim() == 0 || title.trim() == ''){
           title = '信息提示';
       }
       layer.open({
           type : 0,
           icon : 0,
           title : title,
           content : message,
           time : time,
           yes: function(){
               location.href = url;
           },
           cancel: function(index, layero){
               layer.close(index)
               return false;
           },
       });
    },
   /**
    * 警告弹出框[一般用于警告提示之后需要跳转的提示]
    * @param message 提示内容
    * @param url 点击确认后跳转的URL链接
    * @param title 信息框标题
    * @param time 自动关闭所需毫秒，默认为0 表示不关闭
    */
    warmingGo : function(message, url, title = '', time = 0){
       if(typeof(title) == "undefined" || title == false || title.trim() == 0 || title.trim() == ''){
           title = '警告提示';
       }
       layer.open({
           type : 0,
           icon : 5,
           title : title,
           content : message,
           time : time,
           yes: function(){
               location.href = url;
           },
           cancel: function(index, layero){
               layer.close(index)
               return false;
           },
       });
    },
   /**
    * 错误弹出框[一般用于操作出现错误之后需要跳转的提示]
    * @param message 提示内容
    * @param url 点击确认后跳转的URL链接
    * @param title 信息框标题
    * @param time 自动关闭所需毫秒，默认为0 表示不关闭
    */
   errorGo : function(message, url, title = '', time = 0) {
       if(typeof(title) == "undefined" || title == false || title.trim() == 0 || title.trim() == ''){
           title = '错误提示';
       }
       layer.open({
           type : 0,
           icon : 2,
           title : title,
           content : message,
           time : time,
           yes: function(){
               location.href = url;
           },
           cancel: function(index, layero){
               layer.close(index)
               return false;
           },
       });
   },
   /**
    * #询问框 - layer.confirm(content, options, yes, cancel)
    */
   /**
    * 询问框[]
    * @param message 提示内容
    * @param icon icon
    * @param time 自动关闭所需毫秒（如果不配置，默认是3秒）
    * @param func 自动关闭后执行特定的函数 string(函数名),bool(false)表示不执行
    */
    // confirm : function(){
    //    layer.confirm('is not?', {icon: 3, title:'提示'}, function(index){
    //        //do something
    //        layer.close(index);
    //    });
    // },
   /**
    * 确认弹出层[无需跳转到指定页面的确认弹出层，一般用于确认之后执行之后的操作]
    * @param message 提示内容
    * @param url 点击确认后跳转的URL链接
    * @param title 信息框标题
    * @param time 自动关闭所需毫秒，默认为0 表示不关闭
    */
   confirms : function(message) {
       layer.open({
           type: 0,
           icon: 3,
           content: message,
           btn: ['是','否'],
           yes: function(){
               alert('需要执行的操作！');
           },
           cancel: function(index, layero){
               layer.close(index)
               return false;
           },
       });
   },
   /**
    * 确认弹出层[一般用于确认之后需要跳转]
    * @param message 提示内容
    * @param url 点击确认后跳转的URL链接
    * @param title 信息框标题
    * @param time 自动关闭所需毫秒，默认为0 表示不关闭
    */
   confirmsGo : function(message, url, title = '', time = 0) {
       layer.open({
           type: 0,
           icon: 3,
           content: message,
           time : time,
           btn: ['是','否'],
           yes: function(){
               location.href = url;
           },
           cancel: function(index, layero){
               layer.close(index)
               return false;
           },
       });
   },
    
   /** 加载层 - layer.load(icon, options) **/
   /**
    * 加载层[]
    * @param type 取值为0-2，默认为0
    * @param color 背景颜色
    * @param opacity 背景颜色透明度
    */
   loading : function(type, color, opacity){
       if(typeof(type) == "undefined" || type == false || type.trim() == 0 || type.trim() == ''){
           type = 0;
       }
       if(typeof(color) == "undefined" || color == false || color.trim() == 0 || color.trim() == ''){
           color = '#333';
       }
       if(typeof(opacity) == "undefined" || opacity == false || opacity.trim() == 0 || opacity.trim() == ''){
           opacity = '0.6';
       }
       index = layer.load(type, {
           shade: [opacity, color] //0.1透明度的白色背景
       });
   },
   /** 窗 **/
   /**
    * 窗[]
    * @param title 标题 string('这是标题'),为false则不显示
    * @param url 地址 string('http://www.baidu.com')
    * @param width 宽度 string('100px')
    * @param height 高度 string('100px')
    * @param full 是否全屏 bool(true/false)
    */
    : function(title, url, width, height, full){
       var index = layer.open({
           type: 2,
           title: title,//title: false,
           content: [url, 'yes'], //的url，no代表不显示滚动条
           area: [width, height],//['893px', '600px'],
           // offset: [
           //     ($(window).height()-height)/2,
           //     ($(window).width()-width)/2
           // ],
           closeBtn: 1, //1显示关闭按钮,0不显示关闭按钮
           maxmin: true, //开启最大化最小化按钮
           shade: [0],//shade: false,//不显示遮罩
           shadeClose: false,//点击空白区域关闭
           // offset: 'rb', //右下角弹出
           // time: 0, //2秒后自动关闭
           // anim: 1,//动画方式,默认0平滑放大,1从上掉落,2从最底部往上滑入,3从左滑入,4从左翻滚,5渐显,6抖动.
           // end: function(){
           // }
       });
       if(full){
           layer.full(index);
       }
   }
}
```

#### 参与贡献

1. Fork 本仓库

2. 新建 Feat_xxx 分支

3. 提交代码

4. 新建 Pull Request

`欢迎大家为我的开源项目贡献代码，同时我也会一直保持开源，为大家项目开发加速`


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