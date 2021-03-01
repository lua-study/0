JForm
========
>url:    /template/default/script/JForm.js; 
接口开发：yangjian 
文档编写：yangjian 
版本信息：1.2

插件描述:
--------
JForm 是一个表单验证插件, 为表单提供良好的验证和错误返回方式

插件依赖:
-------

* JDialog 插件消息弹出框(如果自己手动处理错误信息接口则可以取消JDialog依赖)
* JDialog 依赖jQuery

更新信息
----

##v1.1

* 更新了名称，之前的JFromCheck改为JForm
* 更新了使用方法new JForm();的时候可以传入参数option
* 新增支持密码强度的验证
* 新增支持checkbox元素的最多和最少选中个数验证
* 新增支持input元素的最长和最短输入内容的验证
* 支持自定义元素的正则验证

##v1.2
* 采用更好的方式重写了JForm
* 修改了自定义验证的方法，自定义函数写在属性中
* 新增用户自定义报错提示信息支持
* 更改了项目结构，添加了gulp构建支持
* 添加了demo文件
* 提供了检测密码等级和身份的API

示例代码:
-------
```html
     
     
    	     
        	 
    	     
    	    option 1
    	      option 2
    	      option 3
    	      option 4
     
```
```javascript
    //js
    var options = {
        formId : '',        
        filter : function( ele ) {  
            return $(ele).attr('required') == undefined;
        },
        
        continueCheck : false,

        showMessage : function( type, message, ele ) { 
            if ( $(ele).attr("dtype") != 'password' ) {
                JDialog.tip.work({type:type, content:message, timer : 2000});
            }
            if ( type == 'error' ) JForm.options.checkSuccess = false;
        }
    };
    var form = new JForm(options);
    if ( form.checkFormData() ) {
        alert("验证成功！");
    }
```

[option参数说明]
-----
key | 说明
--- | ---
formId | 表单id
filter | 元素验证过滤器
showMessage | 用户的错误处理接口，该方法接收三个参数 type : 错误类型， 'ok' => 验证成功, 'error' => 验证失败,'warn' => 警告信息 message : 返回的验证信息，特别注意，如果是密码的话将会返回一个密码等级，0 => 太弱, 1=>弱, 2 => 一般, 3 => 强， 请自己在错误处理的时候注意区别处理;  ele : 当前检测的元素。 
continueCheck | 当遇到错误时是否继续验证如果为true的话，则碰到错误将会继续验证后面的元素。默认为false，即碰到错误立即返回。


[checkFormData()参数说明]
-------------
* form_id : 表示需要验证的表单id
* filter : 一个过滤器，通过过滤器的元素都是不需要验证的。默认那些没有required属性的元素是不参与验证的。

#####如果传入了这个两个参数默认会覆盖options中的formId 和 filter

[dtype属性说明]
-----

dtype | 说明
--- | ---
uname | 表示该数据类型是用户名，必须是 数字+字母+下划线组成的字符串
email | 邮箱地址类型
url | url链接地址类型，是一个完整的绝对地址如 http://www.pvc123.com/index.php?a=1&b=2  相对路径是不会通过验证的，如/admin/user/index 这些都是不合法。
domain | 检测是否是一个合法的域名
mobile | 检测是否是一个合法的手机号码。
phone | 检测是否是一个合法的电话号码, number + - + number格式，如0769-38998777
idnum | 检测是否是个合法的身份证号码，包括17位和15位身份证号码。并检测校验码是否正确
number | 检测是否是纯数字
cn | 验证是否含有汉字
password | 验证密码强度
ip | 检测是否是一个合法的ip地址

[元素属性说明]
-----
* required : 表示该元素需要验证
* min-check ： 最少需要选中多少个元素(仅仅对checkbox元素有效)
* max-check ： 最多能够选中多少个元素(仅仅对checkbox元素有效)
* min-length : 最小输入长度
* max-length : 最大输入长度
* cname ： 提示内容的名称，如“用户名”，“密码”,默认是获取$(ele).parent().parent().prev().text();

----
 
 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)