Editor
====
【基本配置】
----
###1.菜单配置
> 插件有自带的默认配置如无需特殊处理不需要自定义配置
```javascript
    var edit=new Editor("edit");
    edit.config.menus = [
            "source",        //源码
            "bold",        //粗体
            "underline",        //下划线
            "italic",        //斜体
            "strikethrough",        //栅格线
            "eraser",        //清除格式
            "forecolor",        //字体颜色
            "bgcolor",        //背景颜色
            "quote",        //引用
            "fontfamily",        //字体类型
            "fontsize",        //字体大小
            "head",        //标题
            "unorderlist",        //无序列表
            "orderlist",        //有序列表
            "alignleft",        //左对齐
            "aligncenter",        //居中
            "alignright",        //右对齐
            "link",        //超链接
            "unlink",        //撤销 超链接
            "table",        //表格
            "emotion",        //表情
            "img",        //图片
            "video",        //视频
            "location",        //地图
            "insertcode",        //代码
            "undo",        //撤销
            "redo",        //重做
            "fullscreen",        //全屏
    ];
    edit.create();
```
###2.语言配置
> 默认为中文
```javascript
    var edit=new Editor("edit");
    edit.config.lang = Editor.langs["zh-cn"];
    edit.create();
```
```javascript
    var edit=new Editor("edit");
    edit.config.lang = Editor.langs["en"];
    edit.create();
```
###3.编码过滤`javascript`
> 默认为开启过滤
```javascript
    var edit=new Editor("edit");
    edit.config.jsFilter = false;
    edit.create();
```
```javascript
    var edit=new Editor("edit");
    edit.config.jsFilter = true;
    edit.create();
```

###【基本功能】

        1.创建富文本编辑器
        2.销毁富文本编辑器
        3.撤销销毁富文本编辑器
        4.销毁富文本编辑器
        5.清空数据
        6.获取数据*html*形式
        7.获取数据*纯文本*形式
        8.获取数据*格式化*形式

###【图片配置】

        1.自定义上传配置参数

###【字体配置】

        1.字号配置
        2.字体配置
        3.颜色配置

###【表情配置】

        1.表情包导入
        2.表情显示*icon*形式
        3.表情显示*文本*形式

###【地图配置】

        1.百度地图key配置

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)