JQuery-Text-Count
====
一个用来统计input或者textarea字数的jquery插件。`some code from  artTxtCount`
----

### 使用方法
html
```html
  
  
```

JavaScript
```javascript
$(function(){
    $("#text").countText({
        tipEle: $("#tip") ,
        maxNum: 20
    });
});
```
### 基础示例
![](http://i2.piimg.com/567571/493f0fa06a48b2e0.png) 
![](http://i2.piimg.com/567571/411fbd20be2643d0.png) 
[点击查看](http://hungtcs.oschina.io/jquery-text-count/demo)

### 配置
```javascript
$("#text").countText({
    // 显示提示的元素
    tipEle: $("#tip") ,
    // 输入的字数限制
    maxNum: 20 ,
    // 提示元素附加的的class属性
    tipClass: "text-count-tip" ,
    // 超出长度后提示元素附加的class属性
    fullTipClass: "text-count-tip-full" ,
    // 当超出长度后提示元素的 data-text-count-full 属性为 true
    fullTipData: "data-text-count-full" ,
    // 提示元素使用的标签
    tipLabel: "span" ,
    // 未超出长度时提示文字 ，{{remainderLen}}会被替换为还能输入的字数
    tipText: "您还可以输入{{remainderLen}}个字" ,
    // 超出长度时提示文字 ，{{overflowLen}}会被替换成超出的字数
    fullTipText: "已超出{{overflowLen}}个字"
});
```

### 更新时间
`2016年7月7日`

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)