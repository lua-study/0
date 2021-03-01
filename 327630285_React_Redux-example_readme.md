#React_Redux-example

分享一下使用React + Redux + react-router + webpack 开发的单页应用 - 积分商城。这里只为演示，展示了部分页面。

![输入图片说明](http://git.oschina.net/uploads/images/2016/0513/155528_17b8b4d4_9737.png "积分商城首页")

代码完整，安装后可直接运行，有需要的朋友可以参考一下。
    
可运行`npm install`安装相关依赖，资源文件可到下面的演示页面下载。

#演示地址：
 

代码中已知的不足，Bootstrap没有使用react-bootstrap库，这样影响了React的通过改变state渲染UI的机制。比如使用Modal后，页面跳转后，遮罩层不会隐藏，还需要`this.props.router.setRouteLeaveHook`来关闭一下Modal。

另外的经验是在改变数据时，React与Redux state不要混用，否则很容易造成死循环。

author：tangzk

QQ：327630285


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)