

## 开发调试
### android调试
1. react-native  run-android
### ios调试
1. react-native run-ios

##打包
### android 打包步骤
1.React Native项目Xcode打包发布iOS问题 https://www.jianshu.com/p/ada5243d5acc


react - native 调试
1. `https://github.com/facebook/react-devtools/tree/master/packages/react-devtools`
2. `https://facebook.github.io/react-native/docs/debugging.html#accessing-the-in-app-developer-menu`
 
 
 react-native bundle --entry-file index.js --platform ios --dev false --bundle-output ios/ios.jsbundle
 react-native bundle --entry-file index.js --bundle-output ./android/app/src/main/assets/index.android.jsbundle --platform android --assets-dest ./android/app/src/main/res/ --dev false




## 开发调试步骤
### 前置条件:

    1. 克隆代码：`git clone https://gitee.com/cdouble/driverApp.git`
    2. 进入项目根目录：`cd driverApp`
    3. 安装依赖：`npm install ` 或者`yarn ` 关于 [ yarn ](https://yarn.bootcss.com/) 
### android
    1. 确保android studio中已经配置了模拟器，比真机调试块
    2. 项目根目录运行：react-native run-android
### ios
    1. 项目根目录运行：`react-native run-ios`,不建议真机调试，比较慢
        运行效果  


## 代码提交:
    1. 进入项目跟目录：
    2. 增加变更至git管理：`git add .`
    3. 提交代码变更到本地暂存区`git commit -n -m "save for push"`
    4. 合并拉取服务器代码：`git pull origin master`
    5. 增加合并内容至git管理：`git add .`
    6. 增加合并内容至git管理：`git commit -n -m "提交内容说明"`
    7. 上传远程仓库：`git push origin master "提交内容说明"`


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)