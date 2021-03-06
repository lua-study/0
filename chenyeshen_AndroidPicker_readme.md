# Summary
[![API 14+](https://img.shields.io/badge/API-14%2B-green.svg)](https://github.com/gzu-liyujiang/AndroidPicker)
[![Download](https://api.bintray.com/packages/gzu-liyujiang/maven/WheelPicker/images/download.svg)](http://jcenter.bintray.com/cn/qqtheme/framework/)
[![JitPack](https://jitpack.io/v/gzu-liyujiang/AndroidPicker.svg)](https://jitpack.io/#gzu-liyujiang/AndroidPicker)
[![Build Status](https://travis-ci.org/gzu-liyujiang/AndroidPicker.svg?branch=master)](https://travis-ci.org/gzu-liyujiang/AndroidPicker)

安卓选择器类库，包括日期及时间选择器（可设置范围）、单项选择器（可用于性别、职业、学历、星座等）、城市地址选择器（分省级、地级及县级）、数字选择器（可用于年龄、身高、体重、温度等）、双项选择器、颜色选择器、文件及目录选择器等……
欢迎大伙儿在[Issues](https://github.com/gzu-liyujiang/AndroidPicker/issues)提交你的意见或建议。    
欢迎Fork & Pull requests贡献您的代码，大家共同学习【[AndroidPicker交流群 604235437](https://jq.qq.com/?_wv=1027&k=42bKOeD)】。
[查看更新日志](https://github.com/gzu-liyujiang/AndroidPicker/blob/master/ChangeLog.md)，新版本可能未对旧版API作兼容处理，升级后若编译报错请根据错误提示更改。

# Install
“app”是测试用例；“library”包括WheelPicker、ColorPicker、FilePicker、MultiplePicker，
WheelPicker包括DatePicker、TimePicker、OptionPicker、LinkagePicker、AddressPicker、NumberPicker、DoublePicker等。
#### 懒人建议直接远程加载jcenter里的
WheelPicker、FilePicker及ColorPicker是独立的，需要用哪个就compile哪个。
latest.release表示使用最新版，也可以[参照此处指定具体的版本号](https://github.com/gzu-liyujiang/AndroidPicker/releases)，~~1.3.x之前的版本基于ScrollView，1.4.x版本基于ListView~~，1.5.x之后的版本基于View：
```groovy
dependencies {
    compile('cn.qqtheme.framework:WheelPicker:版本号') {
        exclude group: 'com.android.support'
    }
    compile('cn.qqtheme.framework:FilePicker:版本号') {
        exclude group: 'com.android.support'
    }
    compile('cn.qqtheme.framework:ColorPicker:版本号') {
        exclude group: 'com.android.support'
    }
}
```
#### 若jcenter仓库里的无法下载的话，可换[JitPack](https://jitpack.io/#gzu-liyujiang/AndroidPicker)的仓库试试：
第一步，在项目根目录下的build.gradle里加：
```
repositories {
    maven {
        url "https://www.jitpack.io"
    }
}
```
第二步，在项目的app模块下的build.gradle里加：
```
dependencies {
    compile('com.github.gzu-liyujiang.AndroidPicker:WheelPicker:版本号') {
        exclude group: 'com.android.support'
    }
    compile('com.github.gzu-liyujiang.AndroidPicker:FilePicker:版本号') {
        exclude group: 'com.android.support'
    }
    compile('com.github.gzu-liyujiang.AndroidPicker:ColorPicker:版本号') {
        exclude group: 'com.android.support'
    }
}
```
#### 使用Eclipse的话如何集成？
直接[下载AndroidPicker的jar包](/app/libs/)复制到你的项目的libs下即可。

# ProGuard
由于地址选择器使用了[fastjson](https://github.com/alibaba/fastjson)来解析，混淆时候需要加入以下类似的规则，不混淆Province、City等实体类。
```
-keepattributes InnerClasses,Signature
-keepattributes *Annotation*

-keep class cn.qqtheme.framework.entity.** { *;}
```

# Sample （更多用法详见示例项目）
各种设置方法：
```java
picker.setXXX(...);
```   
如：    
设置选项偏移量，可用来要设置显示的条目数，范围为1-5，1显示3行、2显示5行、3显示7行……
```java
picker.setOffset(...);
```   
设置是否禁用循环
```java
picker.setCycleDisable(...);
```   
设置每项的高度，范围为2-4
```java
picker.setLineSpaceMultiplier(...);
```   
设置文字颜色
```java
picker.setTextColor(...);
```   
设置分隔线配置项，设置null将隐藏分割线及阴影
```java
picker.setDividerConfig(...);
```   
自定义顶部及底部视图
```java
picker.setHeaderView(...);
picker.setFooterView(...);
```   
自定义选择器示例：
```java
        CustomHeaderAndFooterPicker picker = new CustomHeaderAndFooterPicker(this);
        picker.setOnOptionPickListener(new OptionPicker.OnOptionPickListener() {
            @Override
            public void onOptionPicked(int position, String option) {
                showToast(option);
            }
        });
        picker.show();
```
 核心滚轮控件为WheelView，可以参照SinglePicker、DateTimePicker及LinkagePicker自行扩展。 

# Screenshots
以下图片显示的效果可能已修改过，实际效果请运行demo查看。   
![滑轮选择器内嵌效果图](/screenshots/nestwheelview.jpg)
![自定义选择器效果图](/screenshots/custom.gif)
![日期选择器效果图](/screenshots/date.gif)
![日期选择器效果图](/screenshots/monthday.jpg)
![时间选择器效果图](/screenshots/time.gif)
![单项选择器效果图](/screenshots/option.gif)
![地址选择器效果图](/screenshots/address.gif)
![数字选择器效果图](/screenshots/number.gif)
![星座选择器效果图](/screenshots/constellation.jpg)
![颜色选择器效果图](/screenshots/color.gif)
![文件选择器效果图](/screenshots/file.gif)
![目录选择器效果图](/screenshots/dir.png)

# Thanks
[基于View的WheelView](https://github.com/weidongjian/androidWheelView) 
[基于ListView的WheelView](https://github.com/venshine/WheelView) 
[基于ScrollView的WheelView](https://github.com/wangjiegulu/WheelView) 


# Contact
   
   


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)