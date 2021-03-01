### 自定义SettingView,提高开发效率，节省代码

##### 在设置或个人中心页面频繁使用

* 效果图

![demoview](F:\demo\LSettingView\demoview.jpg)

* 组件说明

  * Title: LSettingView
  * Description: LSettingView
  * Created by Dadong on 2019/2/27
  * leftText   左侧文字   string
  * leftIcon    左侧图标   integer
  * rightIcon   右侧图标   integer
  * textSize    左侧文字大小 dimension
  * textColor   左侧文字颜色 color
  * isShowUnderLine 是否显示底部分割线  boolean
  * rightStyle  右侧图标风格 enum
  * isShowRightText 是否显示右侧文字   boolean
  * rightText   右侧文字   string
  * rightTextSize   右侧文字大小 boolean
  * rightTextColor  右侧文字颜色 color
  * leftIconSize    左侧图标大小 dimension
  * leftTextMarginLeft  左侧图标与文字间距  dimension

  ### 使用

  * 在布局中引用并设置属性

  ```
   
   
   
  ```

* 在activity使用

  ```
   		Fresco.initialize(this);
          setContentView(R.layout.activity_main);
          LSettingView lSettingView=findViewById(R.id.lSetting);
          lSettingView.setmRightIv("https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1551265567953&di=344a8a20162e4d2a1a688b6d4abb36dc&imgtype=0&src=http%3A%2F%2Fb-ssl.duitang.com%2Fuploads%2Fitem%2F20182%2F21%2F2018221142159_MZ33z.jpeg");
          //自定义点击事件
          lSettingView.setmOnLSettingItemClick(new LSettingView.OnLSettingItemClick() {
              @Override
              public void click(int id, boolean isChecked) {
                  Toast.makeText(getApplicationContext(),"自定义条目点击事件",Toast.LENGTH_LONG).show();
              }
          });
  ```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)