#Banner
Android平台的轮播控件,使用方便,可以任意使用一种图片加载;
ImageLoader: 主要是负责Banner图片加载,内部没有任何实现,开发需要实现它来调用图片加载库加载Banner图;
BannerIndicator: 对指示器和标题做一层抽象,使用者可以自定义indicator,也可以不用indicator.

XML属性:
bannerIndicatorLayout: 自定义indicator布局,必须实现BannerIndicator接口,否则会报参数异常
indicatorStyle,indicator基本样式 
     1.None: 无indicator, 
     2.circle_indicator:圆点指示器
     3.title_indicator：标题指示器
     4.circle_title_indicator：圆点加标题指示器
enableAutoPlayer:是否启用自动播放,不设置，默认不自动播放
pointPadding: 指示器间边距
unSelectDrawable:指示器未选中的图
selectedDrawable：指示器选中的图
indicatorGravity:指示器位置,
  1.left:左对齐
  2.right：右对齐
  3.center：居中
bannerAnimation: banner动画

gradle中使用:
dependencies{
    compile 'com.easy.android:bannerlib:1.0.7'
}


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)