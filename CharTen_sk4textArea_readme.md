# sk4t
*一个为自建博客的文本编辑器使用的快捷键缩进模块*  
*pythion程序员写博文的福音 [滑稽.jpg]*

## 使用方法
---
* 在html里面引入js文件或者将里面的代码复制到你的js文件里
```html
  
```

* 在给textarea添加keydown事件：
```javascript
document.getElementsByTagName('textarea')[0].onkeydown=function(e){
    if(e.keyCode==9){
        sk4t(this).addTab(e);
    }
    if(e.keyCode==221&&e.ctrlKey){
        sk4t(this).addLinesTab();
    }
    if(e.keyCode==219&&e.ctrlKey){
        sk4t(this).rmLinesTab();
    }
}
  ```

## 说明
---
* 构造函数`sk4t(textareaObj)`的参数，只允许`textarea`对象和`input[text]`对象 
* 目前支持的缩进方式有：
  * 于光标处tab：`addTab`
  * 多行进：`addLinesTab`
  * 多行缩：`rmLinesTab` 
* 如果需要阻止按键的浏览器默认事件，直接`addLinesTab(e)`,向方法传进一个事件对象即可  

## 注意事项
---
* 目前不支持IE（等有需求再做兼容。。。
* 目前不支持html5的富文本编辑（同上。。。



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)