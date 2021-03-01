# FrameController.js

#### 项目介绍
优雅的处理单页多框架（ ）窗口管理同步问题

#### 安装教程

下载后安装到 网站的任意目录，打开 http://您的域名/安装路径/demo/demo.html 即可进行测试。（因为本地浏览器会显示iframe，所以必须放到Web服务器中）

在线测试地址：[http://www.miaoqiyuan.cn/products/frame-controller/](http://www.miaoqiyuan.cn/products/frame-controller/)


#### 消息数据结构


```
{
    event: '事件名称',
    type: 'child',
    target: '内嵌页的window',
    data: '传递的数据，即FrameController.broadcast(event, data)的data',
    frameId: '内嵌页标志'
}
```


#### 使用说明

1、点击发送通知，所有打开的内嵌页都会受到通知。

![基础事件](https://images.gitee.com/uploads/images/2018/1010/212326_aa125905_82383.gif "d1.gif")


```
var addLog = function(from, event, data) {
    var _old = $('#log').html().substring(0, 3000);
    $('#log').html(
        (logTpl + _old)
        .replace('#EVENT#', event)
        .replace('#DATA#', JSON.stringify(data))
        .replace('#SOURCE#', from)
    );
    console.log('event：', event, 'data:', data);
};
 
//同步通知
FrameController.addListener('broadcast', function(e) {
    $('#msg').val(e.data.msg);
    addLog(e.frameId, e.event, e.data);
});
 
//发送广播
$('#send').click(function() {
    var nums = FrameController.broadcast('broadcast', {
        msg: $('#msg').val()
    });
    $('#log').html('通知成功:' + nums + '\n\n' + $('#log').html());
});
 
//更新输入状态
$('#msg').change(function() {
    FrameController.broadcast('change', {
        text: '输入框内容已更改:' + $(this).val()
    });
});
 
//更新状态
FrameController.addListener('change', function(e) {
    addLog(e.frameId, e.event, e.data);
});
```


2、新增 内嵌页，关闭内嵌页，可以通过：FrameController.addListener('frame.add',func)、FrameController.addListener('frame.remove',func) 进行监听

![新开、关闭事件](https://images.gitee.com/uploads/images/2018/1010/212444_95495d03_82383.gif "d2.gif")

```
//监听系统事件
var addLog = function(from, event, data) {
    var _old = $('#log').html().substring(0, 3000);
    $('#log').html(
        (logTpl + _old)
        .replace('#EVENT#', event)
        .replace('#DATA#', JSON.stringify(data))
        .replace('#SOURCE#', from)
    );
    console.log('event：', event, 'data:', data);
};
 
//监听系统事件
FrameController.addListener('frame.remove', function(e) {
    addLog(e.frameId, e.event, e.data);
});
FrameController.addListener('frame.add', function(e) {
    addLog(e.frameId, e.event, e.data);
});
```

3、可以对一个事件增加多个监听方法，可以删除所有监听方法、删除某一个监听方法

![事件添加和删除](https://images.gitee.com/uploads/images/2018/1010/212557_3b6ee6f1_82383.gif "d3.gif")
```
var logTpl = '事件:#EVENT# 来源:#SOURCE#\n数据:#DATA#\n\n',
    addLog = function(from, event, data) {
        var _old = $('#log').html().substring(0, 3000);
        $('#log').html(
            (logTpl + _old)
            .replace('#EVENT#', event)
            .replace('#DATA#', JSON.stringify(data))
            .replace('#SOURCE#', from)
        );
        console.log('event：', event, 'data:', data);
    },
    msgEventListener = function(e) {
        $('#log').html('自定义事件已经触发，添加多次会触发多次\n\n' + $('#log').html());
    };
 
 
//添加自定义事件
$('#add_custom').click(function() {
    FrameController.addListener('broadcast', msgEventListener);
});
 
//删除自定义事件
$('#remove_custom').click(function() {
    FrameController.removeListener('broadcast', msgEventListener);
});
```

更多说明请访问：[http://www.miaoqiyuan.cn/p/framecontroller-js](http://www.miaoqiyuan.cn/p/framecontroller-js)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)