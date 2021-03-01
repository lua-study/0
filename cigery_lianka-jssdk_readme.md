# 链咖JS-SDK使用文档
---

注：JS-SDK仅适用于H5移动端网站应用，如你的应用是安卓App或IOS App请使用我们的Android-SDK或IOS-SDK.

[JS-SDK 在线演示入口](http://www.lianka.cn/JsSdk/)

#### 获取 appKey
首先需确保你已在链咖媒体平台注册账号， 并成功创建媒体， 每一个创建后的媒体系统都会分配一个对应的appKey.

[媒体平台注册入口](http://ssp.lianka.cn/index/register)

---

#### 开始使用JS-SDK

根据你在媒体平台中所创建广告位类型，JS-SDK的使用可分为自定义和非自定义两种:

**非自定义类型广告位使用方法**

在媒体平台广告位列表中查看对应的广告位投放代码，该代码由我们系统自动生成，例：

```
(function(){
  var s = document.getElementsByTagName('script');
  var c = s[s.length-1].parentNode;
  var j = document.createElement('script');
  j.type = 'text/javascript';
  j.src = '//resource.lianka123.net/sdk/js/lk-1.0.0.js';
  j.onload = function(){
    LianKaMedia({appKey:'91daBJ3g2FbMvWj68uyBTn4Ya51cXuQr3_0NFUUx4_L8vg', posId:'84', container:c});
  }
  document.querySelector('head').appendChild(j);
})(); 
```

-  **开屏、浮标、插屏、横幅** 类型广告位

请将投放代码复制到页面的"body"标签中任意位置，无需使用其他标签嵌套，如：

```
 
   
  (function(){
    var s = document.getElementsByTagName('script');
    var c = s[s.length-1].parentNode;
    var j = document.createElement('script');
    j.type = 'text/javascript';
    j.src = '//resource.lianka123.net/sdk/js/lk-1.0.0.js';
    j.onload = function(){
      LianKaMedia({appKey:'91daBJ3g2FbMvWj68uyBTn4Ya51cXuQr3_0NFUUx4_L8vg', posId:'84', container:c});
    }
    document.querySelector('head').appendChild(j);
  })(); 
   
 
```
-  **Banner、应用墙、信息流** 类型广告位

请将投放代码复制到页面中想要显示广告的标签容器中 (注：这3种类型必须嵌套到相对应的"标签"容器中， 标签一般应为块级元素，如"div"、"p"、"li"等等), 以下为将投放代码放在页面中"div"标签中的示例：

```
 
   
     
    (function(){
      var s = document.getElementsByTagName('script');
      var c = s[s.length-1].parentNode;
      var j = document.createElement('script');
      j.type = 'text/javascript';
      j.src = '//resource.lianka123.net/sdk/js/lk-1.0.0.js';
      j.onload = function(){
        LianKaMedia({appKey:'91daBJ3g2FbMvWj68uyBTn4Ya51cXuQr3_0NFUUx4_L8vg', posId:'79', container:c});
      }
      document.querySelector('head').appendChild(j);
    })(); 
     
   
 
```

---


**自定义类型广告位使用方法**

1. 引入JS-SDK文件

在你的页面“head”或“body”标签中的任意位置引入我们的JS-SDK文件，如下：
>   

如果你的页面编码不是UTF-8，请给“script”标签添加 charset="utf-8" 属性，如下：
>   


2. 调用SDK的API方法获取广告，示例代码：

```
 
  LianKaMedia({
    appKey: '763e1b864ef6bc93f5dabe1e7195c69b',
    posId: 4,
    target: '_self',
    success: function(res){
      console.log('LianKaMedia Response', res);
      var media = '   ';
      document.querySelector('#lk-custom').innerHTML = media;
    }
  });
 
```

- 调用 LianKaMedia() 方法，请求参数说明：

参数名 | 描述 | 类型 | 默认值 |  必须  | 说明
-------|------|------|--------|----------|---------
appKey | 应用公钥 | String | 无 |  是  | 在创建媒体时系统自动分配，请在平台的媒体列表查看
posId  | 广告位ID | Number | 无 |  是  | 在创建广告位时系统自动分配，请在平台的广告位列表查看
container | 广告位容器 | String | body |  否  | DOM选择器值(如：#id \| .class \| div)，建议使用'#id'选择器值
target | 跳转链接打开方式 | String | _self |  否  | 可选值：[ _self \| _blank \| _parent \| _top ]
coords | 浮标坐标位置 | String | rightBottom |  否  | 可选值：[ leftTop \| rightTop \| leftBottom \| rightBottom ]，也可以直接写CSS，如：'top:10px;left:10%;'，注：此参数只对浮标类型广告位有效
coords | 横幅坐标位置 | String | top |  否  | 可选值：[ top \| bottom ]，也可以直接写CSS，如：'top:10px;left:10%;'，注：此参数只对横幅类型广告位有效
success | 成功执行回调函数 | Function | 无 |  否  | 调用API方法请求成功后的回调函数，此函数的第一个参数为链咖API接口返回的JSON格式广告数据
error | 失败执行回调函数 | Function | 无 |  否  | 调用API方法请求失败后的回调函数

- 调用 LianKaMedia() 成功执行回调函数返回JSON数据说明：

键名 | 描述 | 类型 | 说明
-------|------|------|------
posId | 广告位ID | Number| 广告位ID
link | 跳转链接 | String | 点击广告后跳转的链接地址
width | 宽 | Number | 自定义广告位宽度
height | 高 | Number | 自定义广告位高度
assets | 素材资源 | Array | 上传的自定义广告素材资源列表

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)