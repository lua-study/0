### 安装离子

```
npm install -g ionic
```

### 启动应用程序

```
ionic start myApp tabs
```

### 运行你的App

```
cd myApp
ionic serve
```



*****

### 新建一个ionicUI 页面

```
ionic g page ionicUI
```

### 添加到tabs栏

***********

### 新建一个ionicUI 页面

```
ionic g component ui
```

并在ionicUI页面上引入使用  



******

### 页面修改为懒加载(组件报错)

### 

*******

### 组件修改为懒加载



*************

### 引入轮播图 并开启自动轮播

>标签ion-slides上的属性配置 pager loop="true" autoplay="3000"
>
>page表示轮播图开启显示当前页码，loop="true"表示开启循环播放 autoplay="3000"表示每个3秒钟自动播放一次。



*******

### 引入tab 栏segment 并ts 设定默认选中第一个tab



*****

### 在android 手机上运行测试

参考:http://www.cnblogs.com/wangpinzhou/articles/8948482.html

http://www.cnblogs.com/wangpinzhou/articles/8949923.html

```
cordova platform add android
cordova run android
// 环境安装总报错是建议重启电脑换时间段再试;

```

>cordova run android命令等于cordova build android(生成apk)和adb install -r apk路径(安装apk到真机)
>如果代码有修改,记得先执行ionic serve或者使用ionic cordova run android



***************

###生成app图标 splash 图片

将 resources文件夹下的 icon 和 splash 图标替换; 格式png/ psd

```
$ ionic cordova resources android --icon
$ ionic cordova resources android --splash 

或全部生成 ionic cordova resources
```

第一次 生成 有提示 Email 及密码; 在ionic 官网注册免费版即可;
网址https://dashboard.ionicframework.com/apps



************

### 打包app 并签名 (签名后才可以安装手机使用)



### 打包

```
ionic cordova build android --release
```

(如果这条命令有问题，可以去掉–release然后debug编译，编译完成Dos会显示apk目录位置)

Build Success! 说明成功打包;命令行结束会提示你apk的生成位置。

如果报错,根据报错情况,下载对应的sdk 包 ;

### 签名

[Android应用程序签名（或重新签名）详解](https://blog.csdn.net/yu17310133443/article/details/52701492)

打包后文件必须签名才可安装使用;

在JDK目录下的bin文件夹下有 keytool.exe和jarsigner.exe文件，这两个程序用于给APK签名，签名以后即可发布安装;

配置环境变量;见前面的链接

找到 打包后的app 文件夹,运行命令行;

```
keytool -genkey -v -keystore dome.keystore -alias dome.keystore -keyalg RSA -validity 20000
```

```
/*说明：-genkey 产生密钥

-alias demo.keystore 别名 demo.keystore

-keyalg RSA 使用RSA算法对签名加密

-validity 40000 有效期限4000天

-keystore demo.keystore */
```

```
jarsigner -verbose -keystore dome.keystore -signedjar notepad_signed.apk(新文件名) notepad.apk(旧文件名) dome.keystore
```

```
/*说明：-verbose 输出签名的详细信息

-keystore  demo.keystore 密钥库位置

-signedjar demor_signed.apk demo.apk demo.keystore 正式签名，三个参数中依次为签名后产生的文件demo_signed，要签名的文件demo.apk和密钥库demo.keystore.*/
```



*************

### 调用 原生 Camera

参考官方文档: 

##### 安装Cordova and Ionic Native plugins:

```
$ ionic cordova plugin add cordova-plugin-camera
$ npm install --save @ionic-native/camera
```

##### 增加插件(plugin)到项目应用模块 app.module.ts

```
import { Camera } from '@ionic-native/camera';

...

@NgModule({
  ...

  providers: [
    ...
    Camera
    ...
  ]
  ...
})
export class AppModule { }
```

##### Camera 支持的平台(platforms)

> - Android
> - Browser
> - iOS
> - Windows

```
  // 这里注意;在chrome 打开时用
  ionic cordova platform add browser
  ionic cordova run browser
```


将图片存为 base64 并用*ngFor渲染到 html 上的轮播图slides中;

增加一个clear Button ; 

没有图片时 用*ngIf   *ngIf="images.length>'0'"   隐藏slides;



***********

## 页面跳转的方式

### （1）NavController

1.在first.ts中，先导入NavController，再注入到构造器中。

```
import { NavController } from 'ionic-angular';
class FirstPage { 
    constructor(public navCtrl: NavController) { }
}

```

2.然后导入要跳转到的页面，再定义跳转按钮触发的跳转方法,调用push方法跳转

```
import { SecondPage } from '../second/second';
class FirstPage { 
constructor(public navCtrl: NavController) { }
  goSecondPage(){
    this.navCtrl.push(SecondPage);
  }
}

```

3.在模板中写上按钮绑定事件：

```
 跳转到second 
```

> 报错 No component factory found for “......” 

**解决办法：在app.module.ts 中引入新模块，并在declarations，entryComponents里面添加新模块即可。**

*****

#### 改为懒加载 

app.module.ts中删除引入;

```
  this.navCtrl.push("SecondPage");   //页面增加双引号;
```



********

###（2）[navPush]指令

同样，先导入SecondPage，然后定义一个变量，将SecondPage赋值给它。然后在模板中，向button添加[navPush]属性，绑定pushPage，实现跳转

```
import { SecondPage } from '../second/second';

class FirstPage {
  pushPage;
  constructor(){
    this.pushPage = SecondPage;  // 使用懒加载时app.module.ts不用引入页面;这里改为加双引号: "SecondPage"
  }
}
模板中：
  
```



***********

## 将参数传递给下一个页面

### （1）NavController

为push函数添加第二个参数(发送页面)

假设我们要为TestPage传入一个标题，用来显示到页面上，我们为push方法传入一个对象。

```
 pushTestPage(){
    this.navCtrl.push(TestPage,{
        title:'没有人可以比我帅'
    });
  }
```

引入NavParam并使用(接受页面)

利用NavParams的get方法，可以将传进来的页面参数读取出来。
切换到 test.ts，完成三个步骤
1.引入NavParams并，并在构造函数添加注入语句
2.为TestPage类添加title属性，读取参数并赋给title
3.将title输出到模板中

- 文件 test.ts

```
import { Component } from '@angular/core'

import { NavParams } from 'ionic-angular' //step1

@Component({
    selector: 'page-test',
    templateUrl:'./test.html'
})
export class TestPage {

    title:string; //step2

    constructor(public params:NavParams){ //step1
        this.title=this.params.get('title'); //step2
    }
}
```

###  （2）[navPush]指令

```
 navPage 传参 
```

## 另一种页面跳转 ModalController：(类似模态框)

modal：一个覆盖整个屏幕的overlay，可认为是一个特殊的page。Modals不可重用。当一个modal被关闭（或覆盖）后，它将被毁灭（从堆栈中去除）。
比如，qq登录，你登录成功后，即使你隐藏了页面的返回按钮，安卓手机也是可以使用返回键跳回上一个页面的，那一按返回又退回了登录页面，这显然不是我们想要的，我们需要在登录后销毁页面。

```
import { ModalController } from 'ionic-angular';
import { SecondPage } from '../second/second';

 
@Component(...)
class FirstPage {
 constructor(public modalCtrl: ModalController) {}
 presentSecondPage () {
    let SecondPage = this.modalCtrl.create("SecondPage");
    SecondPage.present();
 } 
}

```

同样在模板中用button触发该方法。

#### 返回上一页面

` this.navCtrl.pop();`



*************
##引入vconsole 方便手机调试(腾讯出品)

```
/ 在 main.ts 引入vconsole 方便手机调试 入口main.ts引入可以全局使用;
import VConsole from "vconsole";
let vConsole = new VConsole(); 
```



*********

## ionic cordova run android   运行报错处理 ;

原因分析 :安装扫描插件后报错;

```
FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':app:processDebugManifest'.
> Manifest merger failed with multiple errors, see logs

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug                                               option to get more log output.

* Get more help at https://help.gradle.org

BUILD FAILED in 2s
    at ChildProcess.whenDone (C:\Users\wpz\Desktop\app\myapp\platforms\android\c                                              ordova\node_modules\cordova-common\src\superspawn.js:169:23)
    at ChildProcess.emit (events.js:159:13)

```



处理过程如下;重装android 平台

```
 cordova platform rm android 
 cordova platform add android 
```

**移除安装的包;**

```

$ ionic cordova plugin add cordova-plugin-qrscanner
$ npm install --save @ionic-native/qr-scanner
```



************

## 引入扫一扫原生插件 ;

参考链接:https://www.jianshu.com/p/45f8b44b9a42

```
app.module.ts
import { QRScanner } from "@ionic-native/qr-scanner";

  providers: [
 ...
    QRScanner
  ]
```

```
scan.ts
scan.scss 
scan.html
*******
variables.scss  //背景白屏解决
ion-app.cameraView,
ion-app.cameraView ion-content,
ion-app.cameraView .nav-decor {
  background: transparent none !important;
  .tabbar.show-tabbar {
    opacity: 0;
  }
}
```

### 封装一个公共组件 进度条

```
ionic g component  progress-bar

```

### 使用segment + swiper 4.0 插件 做 滑动菜单;

参考菜单:https://blog.csdn.net/dan_2017/article/details/78774034

> 关注如何引入第三方库

```
index.html
 
 
 
  

```

```
ts
import { Component, ViewChild } from '@angular/core';
import { NavController, Slides, IonicPage} from 'ionic-angular';

//声明一个Swiper对象，是全局的引用
declare var Swiper;       //引入********
```

```
//当页面加载的时候触发，只触发一次，当有缓存的的时候，打开页面时不在加载
  ionViewDidLoad() {
    this.initSwiper();
  }
  //初始化swiper
  initSwiper() {
    this.swiper = new Swiper('.pageMenuSlides .swiper-container', {
    .....参swiper 设置
    });
  }
```



## 安装 cordova-plugin-statusbar 状态栏插件;

安装命令

```
cordova plugin add cordova-plugin-statusbar
```

消除控制台报警;



### 增加两个页面做投票

> this.navCtrl.push("nextPage")练习页面跳转; --加引号是,懒加载方式
>
> ion-grid ion-row ion-col  col-6 练习栅格布局;
>
> *ngFor="let item of list;index as i;" 练习数据渲染;
>
> 引用进度条组件progress-bar ..   ---需要在module.ts 引入;



## 使用ionic 的storage 做一个存储的搜索记录功能; 类似localstorage;

```
//app.module.ts 
import { IonicStorageModule } from "@ionic/storage"; // 本地存储; 
@NgModule({
...
  imports: [
      IonicStorageModule.forRoot(), //本地存储
  ],
  ...
```

页面中使用

```
import { Storage } from '@ionic/storage'; // 本地存储 存搜索记录
...
  searchdata: string = ''; // 双向绑定数据 [(ngModel)]
  searchHistoryList: Array ;  // 历史数据
  constructor(
    private storage: Storage,  // 本地存储 存搜索记录
  ) {
  }
  
    ngOnInit() {
    // 初始化,获取本地的数据;
    this.storage.get('searchHistoryList').then((val) => {
      if (!val) {  // 没有数据时设定为 [];
        this.searchHistoryList = []
      } else {
        this.searchHistoryList = val;
      }
    })
  };

  search() {
    // 点searchBtn 时记录 数据
    this.searchdata = this.searchdata.trim(); // 去除两边的空格符;
    if (!this.searchdata) { // 空数据时 实用 toast 提示 输入;
      let toast = this.toastCtrl.create({
        message: '请输入搜索值',
        duration: 1000
      });
      toast.present();
    } else {
      for (let i = 0; i  
     
       单选 
                // placeholder 默认显示值
         {{item.examineClassify}} 
       
     
     
       上面单选的联动加多选 
       
         {{item.enrollBatch}} 
       
     
   

   
    {{item.enrollBatch}}
      {{item.enrollStartTime}}
      {{item.enrollEndTime}}
   
```



```
export class SelectPage {

  danxian: string;    // 这个数据可用于返回后台
  liandong: string;    // 这个数据可用于返回后台
  selectdate: Array  = []  
  
  mock: Array  = [   // 联动的全部数据
    {
      examineClassify: "考试分类1",
      "examineClassifyId": "考试分类id",
      "enrollBatchList": [   // 联动的数据
        {
          "enrollBatch": "报名批次1111111",
          "enrollBatchId": "报名批次id1",
          "enrollStartTime": "2017/12/01 16:30",
          "enrollEndTime": "2017/12/01 16:30",
          "limitNumber": "50",
          "enrollNumber": "21",
        },
        {
          "enrollBatch": "报名批次1111111111112",
          "enrollBatchId": "报名批次id22",
          "enrollStartTime": "2017/12/01 16:30",
          "enrollEndTime": "2017/12/01 16:30",
          "limitNumber": "50",
          "enrollNumber": "21",
        }
      ]
    },
    {
      examineClassify: "考试分类2",
      "examineClassifyId": "考试分类id",
      "enrollBatchList": [
        {
          "enrollBatch": "报名批次222222221",
          "enrollBatchId": "报名批次id1",
          "enrollStartTime": "2017/12/01 16:30",
          "enrollEndTime": "2017/12/01 16:30",
          "limitNumber": "50",
          "enrollNumber": "21",
        },
        {
          "enrollBatch": "报名批次222222222222",
          "enrollBatchId": "报名批次id22",
          "enrollStartTime": "2017/12/01 16:30",
          "enrollEndTime": "2017/12/01 16:30",
          "limitNumber": "50",
          "enrollNumber": "21",
        },
        {
          "enrollBatch": "报名批次222222221",
          "enrollBatchId": "报名批次id1",
          "enrollStartTime": "2017/12/01 16:30",
          "enrollEndTime": "2017/12/01 16:30",
          "limitNumber": "50",
          "enrollNumber": "21",
        },
        {
          "enrollBatch": "报名批次222222222222",
          "enrollBatchId": "报名批次id22",
          "enrollStartTime": "2017/12/01 16:30",
          "enrollEndTime": "2017/12/01 16:30",
          "limitNumber": "50",
          "enrollNumber": "21",
        }
      ]
    }
  ]

  mock2: Array  = [];   // 联动的数据

  constructor(public navCtrl: NavController, public navParams: NavParams) {
  }

  change(val) {   // 点击 选项是 生成 关联项目的 数据;
    console.log(val);
    this.mock2 = val.enrollBatchList;
  }
  change2(val) {
    console.log(val);
    this.selectdate = val;
  }
}
```







 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)