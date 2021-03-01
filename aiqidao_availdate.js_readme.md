# `avalidate.js`：为[APICloud](http://www.apicloud.com/)表单验证而生，但不仅仅限于此！

* 作者：`新生帝`
* QQ：`8020292`
* QQ交流群：`18863883`
* 技术支持：[中山赢友网络科技有限公司](http://www.winu.net/)

* [APICloud](http://www.apicloud.com/)是一个非常好的一个APP开发平台！[APICloud官网](http://www.apicloud.com/)
* [论坛回帖地址](http://community.apicloud.com/bbs/forum.php?mod=viewthread&tid=17310&page=1&extra=#pid95308) 

## 来先看看例子

>* [实例一](http://availdate.oschina.mopaasapp.com/)
>* [实例二](http://availdate.oschina.mopaasapp.com/demo2.html)
>* [实例三](http://availdate.oschina.mopaasapp.com/demo3.html)
>* [实例四](http://availdate.oschina.mopaasapp.com/demo4.html)
>* [实例五](http://availdate.oschina.mopaasapp.com/demo5.html)


## 更新记录

```
### 2015年11月16日  availdate-1.0.2.js 更新细节：
* [更新] 更新核心方法beginCheck()，支持序列化对象的获取

### 2015年11月09日  availdate-1.0.2.js 更新细节：
* [新增] 新增核心方法beginCheck()，可主动触发验证脚本,可以传入方法，如果传入，则验证成功后执行传入方法，而不是只想endSuccess中的方法
* [补上] 通常可以用于Window页面触发Frame页面的验证，主要是通过SendEvent，addEventListener配套使用，或者api.execScript()使用，推荐前者
* [更新] 更新文档
* [更新] 更新验证按钮元素找不到时提示错误为警告提示！

### 2015年11月08日  availdate-1.0.2.js 更新细节：
* [新增] video 标识符，支持视频格式验证
* [新增] flash 标识符，支持Flash格式验证
* [新增] mp3 标识符，支持mp3格式的验证
* [新增] doc 标识符，支持文档格式的验证
* [新增] img 标识符，支持图片格式的验证
* [新增] zip 标识符，支持压缩包格式的验证
* [新增] md5 标识符，支持md5字符串的验证
* [新增] ascii 标识符，支持ascii码字符串的验证
* [新增] color 标识符，支持十六进制颜色值的验证
* [新增] ens 标识符，支持纯小写英文的验证
* [新增] enb 标识符，支持纯大写英文的验证
* [新增] age 标识符，支持年龄的验证
* [新增] cname 标识符，支持中文名的验证
* [新增] ename 标识符，支持英文名的验证
* [新增] pn 标识符，支持正数的验证
* [新增] upn 标识符，支持负数的验证

### 2015年11月07日  availdate-1.0.1.js 更新细节：
* [新增] 验证成功之后返回序列化对象
* [新增] idcard 标识符，支持身份证验证
* [新增] time 标识符，支持时间格式验证
* [新增] tm 标识符，支持手机或固话的验证
* [新增] t 标识符，支持固话的验证
* [修复] 修复验证只获取到子类的bug，无法获取子代所有元素
* [修复] 修复一系列bug

### 2015年11月06日   availdate-1.0.0.js 版本正式发布：
* [新增] 整个项目基础原型
```

非常感谢流浪男版主带给我们非常好的[AUI](http://www.auicss.com/)布局框架，让我们的开发速度再一次的升华！但是，想更快的开发，更省代码吗？`availdate.js`能帮到你！

## `availdate.js`是什么呢？


我们在开发的过程中，经常遇到很多需要用户填写的表单，每次都需要写非常庞大的表单验证脚本，试想一下，如果需要客户填写100个表单，那验证脚本岂不是吓死宝宝了，而且会非常的占用开发时间！时势造英雄，这时候，`availdate.js`就来了！

`availdate.js`是一个纯`javascript`编写的一个验证脚本插件，不依赖于任何第三方框架，直接在页面中使用即可，她具有跨平台，小巧，拓展性极强和完全开源等的特点！你只需要短短的代码，甚至不需要代码就可以实现完整的验证操作了，她还内置了大量的常用的验证库，大大的提升了我们的开发速度。

`availdate.js`第一个版本是本人花了3个多小时编写的，可能在使用过程成会出现遗漏或者未能考虑到的bug，请及时反馈，定当全力修复bug。

[APICloud](http://www.apicloud.com/)会越来越美好，因为有他们，你们，我们的共同努力！让我们一起见证一个孩子的创世之路吧！


### `availdate.js`自定义标签属性：


>* `data-rule`：必填，这个属性是整个验证插件的基础。注意：需要验证的插件必须填写该属性，但除了指定`data-sync`属性以外。
>* `data-nullmsg`： 选填，当表单为空的时候提示信息。
>* `data-errmsg`	： 选填，当表单验证失败的时候提示信息。
>* `data-sucmsg`：选填，当表单执行成功的时候提示信息。
>* `data-sync`：选填，同步验证，一般用于密码的验证。比如，第一次输入密码之后，第二次密码需要和第一次输入密码进行同步验证。 
>* `data-haved`：选填，跳过为空验证，只当有值的时候才会执行验证。


### `availdate.js`内置默认验证规则：


>* `*`：必填，不能为空。例子：`data-rule="*"`
>* `*6-16`：必填，不能为空，且必须是6到16个字符。例子：`data-rule="*3-12"`，`data-rule="*5-10"`。分别表示：必填，3到12个字符；必填，5到10个字符。
>* `n`：必填，不能为空，且必须是正整数。例子：`data-rule="n"`
>* `n6-16`：必填，不能为空，且必须是6到16个字符例子：`data-rule="n3-12"`
>* `s`：必填，不能为空，且不能包含特殊字符的字符串。例子：`data-rule="s"`
>* `s6-16`：必填，不能为空，且必须是6到16位的非包含特殊字符的字符串。例子：`data-rule="s6-16"`
>* `p`：必填，不能为空，且必须是正确的邮政编码。例子：`data-rule="p"`
>* `m`：必填，不能为空，且必须是正确的手机号码。例子：`data-rule="m"`
>* `e`：必填，不能为空，且必须是电子邮箱。例子：`data-rule="e"`
>* `url`：必填，不能为空，且必须是网址格式。例子：`data-rule="url"`
>* `date`：必填，不能为空，且必须是日期格式。例子：`data-rule="date"`
>* `zh`：必填，不能为空，且必须是中文。例子：`data-rule="zh"`
>* `dword`：必填，不能为空，且必须填写双字节字符。例子：`data-rule="dword"`
>* `money`：必填，不能为空，且必须是金额类型。例子：`data-rule="money"`
>* `ipv4`：必填，不能为空，且必须是IPv4地址。例子：`data-rule="ipv4"`
>* `ipv6`：必填，不能为空，且必须是IPv6地址。例子：`data-rule="ipv6"`
>* `num`：必填，不能为空，必须是数值类型，例如正整数，正浮点数，小数。例子：`data-rule="num"`
>* `qq`：必填，不能为空，必须是qq号码。例子：`data-rule="qq"`
>* `idcard`：必填，不能为空，必须是身份证号码。例子：`data-rule="idcard"`
>* `time`：必填，不能为空，必须是时间格式号码，例如：10:23:60。例子：`data-rule="time"`
>* `t`：必填，不能为空，必须是固话号码，如：0760-88809987。例子：`data-rule="t"`
>* `tm`：必填，不能为空，必须是手机或者固话号码，例如：18676265646，0760-88809987。例子：`data-rule="tm"`
>* `video`：必填，不能为空，且必须是视频文件。如：例子：`data-rule="video"`
>* `flash`：必填，不能为空，且必须是Flash文件。例子：`data-rule="flash"`
>* `mp3`：必填，不能为空，且必须是mp3文件。例子：`data-rule="mp3"`
>* `doc`：必填，不能为空，且必须是文档文件。例子：`data-rule="doc"`
>* `img`：必填，不能为空，且必须是图片文件。例子：`data-rule="img"`
>* `zip`：必填，不能为空，且必须是压缩文件。例子：`data-rule="zip"`
>* `md5`：必填，不能为空，且必须是md5加密字符串。例子：`data-rule="md5"`
>* `ascii`：必填，不能为空，且必须是ascii码字符串。例子：`data-rule="ascii"`
>* `color`：必填，不能为空，且必须是十六进制颜色字符串。例子：`data-rule="color"`
>* `ens`：必填，不能为空，且必须是全部小写字母字符串。例子：`data-rule="ens"`
>* `enb`：必填，不能为空，且必须是全部大写字母字符串。例子：`data-rule="enb"`
>* `age`：必填，不能为空，且必须是正常的年龄。例子：`data-rule="age"`
>* `cname`：必填，不能为空，且必须是中文名称。例子：`data-rule="cname"`
>* `ename`：必填，不能为空，且必须是英文名称。例子：`data-rule="ename"`
>* `pn`：必填，不能为空，且必须是正数。例子：`data-rule="pn"`
>* `upn`：必填，不能为空，且必须是负数。例子：`data-rule="upn"`


### 还不够？

如果上面的还不能满足你，不用担心，`data-rule`也支持万能的正则表达式，如：

>* `data-rule="/\w{3,6}/i"`    表示3-6位字符
>* `data-rule="/^\d$/"`       只允许一个数字

注意：如果`data-rule`传入的是正则表达式，则必须用` / / `包住。

### 我想和默认标识符一样，替代正则表达式，行不行？当然行！

```
ac.addRule({
            // 支持固话和手机的验证
            "tm": /(^[0-9]{3,4}\-[0-9]{3,8}$)|(^[0-9]{3,8}$)|(^\([0-9]{3,4}\)[0-9]{3,8}$)|(^0{0,1}13[0-9]{9}$)/
});
```

这样就可以通过 `data-rule="tm"` 来验证手机和固话了。

### `availdate.js`公开方法


#### `var v=ac.form(params);`	描述：所有需要验证的区域都需要调用这个方法，该方法返回验证核心原型`Winu`，可以通过返回对象调用`beginCheck();`方法触发执行验证

`params`参数说明：

>* `area`：需要验证的区域
>* `btn`：触发验证的按钮，支持标签，`id`，`class`，推荐用`id`或者`class`
>* `startCheck: function () {}`：开始验证之前执行函数，通常用于加载中，提交中这样的动画
>* `singleSuccess: function (e, msg) {}`：单个验证成功时执行函数，`e`返回正在验证的表单对象，`msg`标识提示消息
>* `singleError: function (e, msg) { }`：单个验证失败时执行函数，`e`返回正在验证的表单对象，`msg`标识提示消息
>* `endSuccess: function (data) {}`：全部验证成功之后执行函数，`data`是返回的`JSON`格式对象

`v`返回对象说明：
>* `beginCheck`：我们经常是通过按钮点击触发验证，如果想通过其他机制触发验证也可以通过`v.beginCheck()`主动触发验证，如果还想验证成功之后执行另外的函数，可以通过`b.beginCheck(function(data){});`


#### `ac.addRule(params);`	描述：拓展默认`data-rule`标识符，拓展之后，可直接使用标识符代表该正则表达式

`params`参数说明：

>* `属性名`：属性名是定义自定义`标识符`，可以供`data-rule`使用
>* `属性值`：属性值必须是一个正则表达式，不能是字符串，`data-rule`内部就是通过`标识符`找到对应的正则表达式进行验证的。


###  介绍了那么多，那该如何在项目中使用呢？

#### 1）基本使用

```html
 
 
 
     
      
     
     
      
 
 
     
         必填验证：data-rule="*" 
        姓名：    



         指定字符数：data-rule="*3-5"，标识只能输入3到5个字符 
        姓名2：    



         验证正整数：data-rule="n" 
        年龄：    



         验证正整数：data-rule="n3-6"，只能输入3到6位正整数 
        个数：    



         只能输入字符串，不能输入特殊字符：data-rule="s" 
        昵称：    



         只能输入字符串，不能输入特殊字符：data-rule="s3-6"，只能输入不包含特殊字符的字符串，并且在3到6个字符之间 
        昵称2：    



         验证邮政编码：data-rule="p" 
        邮政编码：    



         验证手机号码：data-rule="m" 
        手机号码：    


         验证电子邮件：data-rule="e" 
        电子邮件：    



         验证是否是一个网址：data-rule="url" 
        网址：    



         验证是否是日期格式：data-rule="date"，支持各种格式的日期格式 
        出生日期：    



         验证是否是中文：data-rule="zh" 
        中文名称：    



         验证是否是中文：data-rule="/^[\u4e00-\u9fa5]{3,6}$/"，只能输入3到6个中文名称， 支持万能的正则表达式  
        中文名称：    



         验证金钱格式：data-rule="money" 
        你的工资是多少：    



         验证数值类型：data-rule="num"，支持小数，整数 
        你的身高：    



         你的性别：data-rule="*" 
        性别：     男  女



         你的兴趣爱好：data-rule="*" 
        性别：     篮球   足球  羽毛球



         你是基佬吗？：data-rule="*" 
        是否基佬？：    
             请选择 
             是 
             不是 
         



         
         
         
     
     

        // 对，就这么简单就初始化了。
        ac.form({
            area: "#frm",   // 验证区域，支持标签，id，class，推荐使用id或者class
            btn: "#btn"     // 触发验证的按钮或者元素，支持标签，id，class，推荐使用id或者class
        });

     
 
 
```

#### 2）高级使用

##### 1、自定义验证错误提示，主要是编写`singleError`方法

```html
 
 
 
     
      
     
     
      
 
 
     
         必填验证：data-rule="*" 
        姓名：    

         
         
         
     
     

        // 对，就这么简单就初始化了。
        ac.form({
            area: "#frm",   // 验证区域，支持标签，id，class，推荐使用id或者class
            btn: "#btn",     // 触发验证的按钮或者元素，支持标签，id，class，推荐使用id或者class
            singleError: function (e, msg) {
                // 自定义弹窗格式###############
                alert("我是自定义弹窗格式：错误消息：" + msg);
            },
            endSuccess: function (data) {
                  alert("全部验证成功啦！！！！！！" + JSON.stringify(data));
            }
        });

     
 
 
```

##### 2、每一个表单元素验证成功之后执行自定义函数，主要是编写`singleSuccess`方法

```html
 
 
 
     
      
     
     
      
 
 
     
         必填验证：data-rule="*" 
        姓名：    

         
         
         
     
     

        // 对，就这么简单就初始化了。
        ac.form({
            area: "#frm",   // 验证区域，支持标签，id，class，推荐使用id或者class
            btn: "#btn",     // 触发验证的按钮或者元素，支持标签，id，class，推荐使用id或者class
            singleError: function (e, msg) {
                // 自定义弹窗格式###############
                alert("我是自定义弹窗格式：错误消息：" + msg);
            },
            singleSuccess: function (e, msg) {
                // 验证单个成功之后提示信息
                alert("我自己通过验证了！别人我不知道！");
            },
            endSuccess: function (data) {
                  alert("全部验证成功啦！！！！！！" + JSON.stringify(data));
            }
        });

     
 
 
```

##### 3、在表单验证之前执行自定义函数，主要是编写`startCheck`方法

```html
 
 
 
     
      
     
     
      
 
 
     
         必填验证：data-rule="*" 
        姓名：    

         
         
         
     
     

        // 对，就这么简单就初始化了。
        ac.form({
            area: "#frm",   // 验证区域，支持标签，id，class，推荐使用id或者class
            btn: "#btn",     // 触发验证的按钮或者元素，支持标签，id，class，推荐使用id或者class
            startCheck: function () {
                // 自定义验证之前执行函数
                alert("开始验证啦！一般用于加载！");
            },
            singleError: function (e, msg) {
                // 自定义弹窗格式###############
                alert("我是自定义弹窗格式：错误消息：" + msg);
            },
            singleSuccess: function (e, msg) {
                // 验证单个成功之后提示信息
                alert("我自己通过验证了！别人我不知道！");
            },
            endSuccess: function (data) {
                  alert("全部验证成功啦！！！！！！" + JSON.stringify(data));
            }
        });

     
 
 
```

##### 4、在表单验证通过所有验证之后执行自定义函数，主要是编写`endSuccess`方法

```html
 
 
 
     
      
     
     
      
 
 
     
         必填验证：data-rule="*" 
        姓名：    

         
         
         
     
     

        // 对，就这么简单就初始化了。
        ac.form({
            area: "#frm",   // 验证区域，支持标签，id，class，推荐使用id或者class
            btn: "#btn",     // 触发验证的按钮或者元素，支持标签，id，class，推荐使用id或者class
            startCheck: function () {
                // 自定义验证之前执行函数
                alert("开始验证啦！一般用于加载！");
            },
            singleError: function (e, msg) {
                // 自定义弹窗格式###############
                alert("我是自定义弹窗格式：错误消息：" + msg);
            },
            singleSuccess: function (e, msg) {
                // 验证单个成功之后提示信息
                alert("我自己通过验证了！别人我不知道！");
            },
            endSuccess: function (data) {
                  alert("我是自定义验证成功的弹窗！！！！"+JSON.stringify(data));
            }
        });

     
 
 
```

##### 5、自定义`data-rule`标识符，比如验证手机或固话：`data-rule="tm"`   本身是没有这个标识的

```html
 
 
 
     
      
     
     
      
 
 
     
         手机或者固话：data-rule="tm"  我是自定义验证规则标识的，本来没有tm的标识，tm标识固话或者手机 
        手机或者固话：    

         
         
         
     
     
        // 自定义标识规则
        ac.addRule({
            "tm": /((15)\d{9})|((13)\d{9})|((18)\d{9})|(0[1-9]{2,3}\-?[1-9]{6,7})/i
        });

        // 对，就这么简单就初始化了。
        ac.form({
            area: "#frm",   // 验证区域，支持标签，id，class，推荐使用id或者class
            btn: "#btn",
           endSuccess: function (data) {
                  alert("全部验证成功啦！！！！！！" + JSON.stringify(data));
            }
        });

     
 
 
```


#### 3）还可以这样用！

##### 1、比如判断两次密码输入是否一样，主要用到`data-sync="同步的name名称"`，同步验证

```html
 
 
 
     
      
     
     
      
 
 
     
         验证两次输入密码是否一致：data-rule="s3-10"  ，注意是通过data-sync="需要同步验证的name值"，这时候必须指定name值了 
        密码一：    
         
         如果添加了data-sync属性，可以不写data-rule了。 
        密码二：    
         
         
         
     
     

        // 对，就这么简单就初始化了。
        ac.form({
            area: "#frm",   // 验证区域，支持标签，id，class，推荐使用id或者class
            btn: "#btn",
            endSuccess: function (data) {
                  alert("全部验证成功啦！！！！！！" + JSON.stringify(data));
            }
        });

     
 
 
```

##### 2、如果不填，则忽略验证，如果填写则执行验证，主要用到`data-haved="true"`属性

```html
 
 
 
     
      
     
     
      
 
 
     
         必须输入3到6个字符：data-rule="*3-6"，如果添加了data-haved="true"之后，就不执行为空验证了，只有填写值的时候才执行验证 
        姓名：    

         
         
         
     
     

        // 对，就这么简单就初始化了。
        ac.form({
            area: "#frm",   // 验证区域，支持标签，id，class，推荐使用id或者class
            btn: "#btn",
            endSuccess: function (data) {
                  alert("全部验证成功啦！！！！！！" + JSON.stringify(data));
            }
        });

     
 
 
```

* 更多例子由你来发现！！！

* `availdate.js`为[APICloud](http://www.apicloud.com/)而生，但不仅仅限于此！

* `availdate.js`开源地址：[Github](http://git.oschina.net/winu.net/availdate.js)

* QQ交流群：`18863883`

* 技术支持：[中山赢友网络科技有限公司](http://www.winu.net/)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)