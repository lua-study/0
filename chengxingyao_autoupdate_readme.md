# autoupdate
自动更新分渠道打包，解决百度市场与360市场发布问题

现在国内应用市场一大堆，应用市场的恶性竞争要求开发者必须集成自己的自动更新，且排除其他平台的自动更新。在这种情况下对于开发者无疑增加了大量工作量。不过好在android studio 的高效分渠道打包方式

github源码
https://github.com/chengxingyao/autoupdate
开源中国
https://git.oschina.net/chengxingyao/autoupdate

##### 在project build.gradle中添加 maven 地址
```
allprojects {
    repositories {
        jcenter()
        maven { url "https://raw.githubusercontent.com/chengxingyao/maven/master/" }
    }
}
```
##### 在app build.gradle中添加 配置及引用
```
apply plugin: 'com.android.application'

android {
    compileSdkVersion 25
    buildToolsVersion "25.0.2"
    defaultConfig {
        //360 渠道通过 applicationId  检查更新
        applicationId "com.example.cheng.myapplication"
        minSdkVersion 15
        targetSdkVersion 25
        versionCode 1
        versionName "1.0"
      //配置百度应用市场的 appid appkey
        manifestPlaceholders = [
                BDAPPID: "8235504",
                BDAPPKEY : "kMe1fyBG8RqcLgInyZOx39Dy4K731noh"

        ]
    } 
    //渠道名称定义
    productFlavors {
        //360
        channel_360
        //百度
        channel_baidu
    }
}

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    compile 'com.android.support:appcompat-v7:25.2.0'
    //360渠道自动更新包引用
    channel_360Compile "com.autoupdate:c360update:0.1"
    //百度渠道自动更新包引用
    channel_baiduCompile "com.autoupdate:bdautoupdate:0.1"
}

```
##### 调用自动更新
```java
   //自动更新
  AutoUpdate.uiUpdateAction(this, new UICheckUpdateCallback() {
      @Override
      public void onCheckComplete() {

   }
   });
```
##### 手动检测版本更新
```java
//手动检测版本
 AutoUpdate.cpUpdateCheck(this, new CPCheckUpdateCallback() {
      @Override
      public void onCheckUpdateCallback(AppUpdateInfo appUpdateInfo) {

  }
 });
```
百度自动更新样式
![百度自动更新样式](http://upload-images.jianshu.io/upload_images/2937228-48bc937353fafea0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/300)

360自动更新样式
![360自动更新样式](http://upload-images.jianshu.io/upload_images/2937228-433b11390b418e69.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/300)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)