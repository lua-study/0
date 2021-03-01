 【好消息】个人网站已经上线运行,后面博客以及技术干货等精彩文章会同步更新，请大家关注收藏: http://www.lcode.org   
本人CSDN博文地址 http://blog.csdn.net/developer_jiangqq  
本人维护的微信订阅号,欢迎大家微信关注一下!定期分享移动技术干货,项目管理和博客文章! 
 
###本人最新录制的实战项目视频-菜鸟新闻 点击进入 
###简介如下:
菜鸟新闻安卓客户端-是一个仿照36Kr官方App,实时抓取36Kr官网数据的资讯类新闻客户端 
包括首页新闻,详情,发现,活动,实时数据抓取,侧滑效果,第三方登录以及分享,消息推送等相关功能客户端。 
学习目标: 
1.掌握Android 5.0以上的相关技术控件使用(RecyclerView,CardView); 
2.熟悉目前主流开源框架的使用:Okhttp,Volley,UIL,Fresco,EventBus.... 
3.熟悉数据抓取爬虫技术; 
4.第三方集成登录与分享,消息推送数据统计集成。 
5.掌握项目架构,开发流程 
6.独立开发APP  
 http://www.cniao5.com/clazz/news.html  
    

### 关于本人 
邮箱:jiangqqlmj@163.com 
本人微信/QQ:781931404 
Android技术交流群:99787482 
  
Android开发群1:107086751 
Android开发群3:109244103 

 # FastDev4Android 
本项目是Android快速开发框架，采用AndroidStudio进行开发。
预想集成工具包,ORM,网络请求(HTTPClint,Volley,OkHttps),数据解析,依赖注入,xutils,图片异步加载，二维码扫描等等 
同时会包括工作中自己封装的一些组件和控件.
后续会进行逐步添加
整体项目目录如下:
 FastDev4Android 
 
     
         包名  描述 
     
      libs   一些公共jar包库  
      adapter  适配器  
      application  全局application  
      base  基类包  
      cache  数据缓存相关处理  
      common  公共类,或者配置相关  
      db  数据库操作相关  
      event  事件处理相关  
      fragment  fragment操作管理相关  
      html5  webview处理,重写webview  
      json  json数据解析  
      listlogic  网络数据请求加载分发  
      location  位置相关  
      model  实体类  
      push  消息推送  
      sensor  设备传感器相关  
      spreference  SharedPerference管理  
      test  消息推送  
      ui  Activity UI相关  
      update  APP自动更新相关  
      utils  项目各种工具类  
      widget  自定义控件  
      crash  自定义崩溃异常处理  
      receiver  广播通知处理  
 

   20151201框架更新:   
一.返照网易新闻Tab标签和页面切换滑动; 
 HorizontalScrollView,Fragment,FragmentStatePagerAdapter打造网易新闻Tab及滑动页面效果(三十六)  
 Design支持库TabLayout打造仿网易新闻Tab标签效果(三十七)  
 更多项目内容请详见CSDN博客!  
 

   20151119框架更新:   
一.RecyclerView控件完全解析; 
 RecyclerView完全解析,让你从此爱上它(二十八)  
 RecyclerView完全解析之打造新版类Gallery效果(二十九)  
 RecyclerView完全解析之结合AA(Android Annotations)注入框架实例(三十)  
 RecyclerView完全解析之下拉刷新与上拉加载SwipeRefreshLayout(三十一)  
 CardView完全解析与RecyclerView结合使用(三十二)  
 实例解析之SwipeRefreshLayout+RecyclerView+CardView(三十五)  
 
二.ViewDragHelper控件完全解析; 
 神器ViewDragHelper完全解析,妈妈再也不担心我自定义ViewGroup滑动View操作啦~(三十三)  
 神器ViewDragHelper完全解析之详解实现QQ5.X侧滑酷炫效果(三十四)  
 


   20151110框架更新:   
一.Volley网络框架基本使用; 
&nbsp;&nbsp;&nbsp;&nbsp;项目中我是采用库引用方式引入Volley框架,这边Volley库也已经同步上传了,大家直接编译运行即可; 
 Volley完全解析之基础使用(二十六)  
 Volley完全解析之进阶最佳实践与二次封装(二十七)  

   20151101框架更新:   
 非常漂亮的进度指示器AVLoadingIndicatorView的使用讲解(十八)  
 Android MVP开发模式详解(十九)  
 消息总线EventBus的基本使用(二十)  
 消息总线EventBus源码分析以及与Otto框架对比(二十一)  
 列表头生成带文本或者字母的图片开源库TextDrawable使用和详解(二十二)  
 重写WebView网页加载以及JavaScript注入详解(二十三)  
 BaseAdapterHelper的基本使用介绍,让你摆脱狂写一堆Adapter烦恼(二十四)  
 BaseAdapterHelper详解源码分析,让你摆脱狂写一堆Adapter烦恼(二十五)  
 

   20151029注入框架更新:   
更新了AndroidAnnotations注入框架的使用详解: 
 AndroidAnnnotations注入框架介绍和Android Studios基本配置(一)  
 AndroidAnnnotations注入框架的工作原理(二)  
 AndroidAnnnotations注入框架使用之注入组件Components(三)  
 AndroidAnnnotations注入框架使用之Injection标签详解(四)  
 AndroidAnnnotations注入框架使用之事件绑定Event Binding(五)  
 AndroidAnnnotations注入框架使用之线程处理Threading(六)  
 AndroidAnnnotations注入框架使用之第三方框架集成RoboGuice(七)  
 AndroidAnnnotations注入框架使用之第三方框架集成Otto事件总线(八)  
 AndroidAnnnotations注入框架使用之第三方框架集成OrmLite(九)  
 AndroidAnnnotations注入框架使用之最佳实践之Adapters和lists(十)  
 AndroidAnnnotations注入框架使用之最佳实践SharedPreferences(十一)  
 

   V1.1.1_003版本功能如下:   
一.新增沉浸式状态栏功能实现; 
二.新增MVP开发模式功能Demo; 
以上该组件全部在MainActivity中有相应的使用实例; 

   

   V1.1_002版本功能如下:   
一.新增首页图片自动无限轮播组件和指示器(AutoGallery+FlowIndicator); 
二.新增列表下拉刷新组件(PullToRefreshListView); 
三.新增本地轻量级数据缓存组件(ACache); 
四.新增应用自定义崩溃日志捕捉组件(CustomCrash); 
以上该组件全部在MainActivity中有相应的使用实例; 

   V1.0_001版本功能如下:   
一.Utils工具类加入 
&nbsp;&nbsp;&nbsp;&nbsp;1.DataUtils 时间日期处理 
&nbsp;&nbsp;&nbsp;&nbsp;2.GuideUtils 是否启动引导处理标志管理 
&nbsp;&nbsp;&nbsp;&nbsp;3.IoUtils 网络请求工具类【特别注意】这边采用HTTPClient 由于Android 6.0已经删除该类,
这边libs目录需要加入org.apache.http.legcy.jar依赖包 
&nbsp;&nbsp;&nbsp;&nbsp;4.JudgeNetWorker 网络状态判断工具类 
&nbsp;&nbsp;&nbsp;&nbsp;5.Log 日志自定义管理 
&nbsp;&nbsp;&nbsp;&nbsp;6.ManagerActivity Activity管理工具类 
&nbsp;&nbsp;&nbsp;&nbsp;7.StrUtils 字符串相关处理工具类，系统信息获取工具类) 
二.sperferences加入SharePerferences加入封装工具可以快速使用SP进行数据保存配置文件 
三.Activity基类简单封装BaseActivity和BaseFrameActivity 暂时主要为Toast,LayoutInFlater,打开指定的Activity工具类分装 

后期会持续不断进行更新最新的框架功能，如果有一起合作把这个Android快速开发框架完善起来的~请联系我哦 
  QQ:781931404   
 




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)