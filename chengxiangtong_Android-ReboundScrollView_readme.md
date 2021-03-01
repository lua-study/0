#Android-ReboundScrollView

## 前言
    本项目为一个可以在scrollview到顶部后，还可以继续下拉的控件
    
## 引用其他第三方类库
    'com.nineoldandroids:library:2.4.0' 兼容API9以下的动画库
    
## 截图
![gif](http://ww4.sinaimg.cn/large/844036b9jw1f24drakv1mg20dc0m813o.gif)

## 使用时的核心代码

#### xml
     
     
    
         
    
             
    
                 
    
                     
                 
    
                 
    
                 
    
             
    
         
    
     


#### java
    FrameLayout mFlHead;
    mSvContent.setHeaderView(mFlHead);//设置需要弹性的头布局
    mSvContent.setHeaderView(mFlHead);
        mSvContent.setScrollViewListener(new ObservableScrollView.ScrollViewListener() {
            @Override
            public void onScrollChanged(ObservableScrollView scrollView, int x, int y, int oldx, int oldy) {
            //滚动侦听
            }
        });

    mSvContent.setCloseDuration(300);//关闭动画的速率
    mSvContent.setMaxHeight(200);//最大的增加高度
    mSvContent.setCanRebound(false);//设定开启弹性功能与否

    mSvContent.setOnAnimListener(new ReboundScrollView.OnAnimListener() {//侦听动画
        @Override
        public void onAnim(ReboundScrollView scrollView, float fraction, float height) {
            Log.d("MainActivity", "fraction:" + fraction);//下拉的百分比
            Log.d("MainActivity", "height:" + height);//下拉的高度
        }
    });



## 关于自定义属性
    暂时未加入，后续会考虑加入自定义属性

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)