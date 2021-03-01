![ESTabBarController](logo.png)

[![Travis](https://travis-ci.org/eggswift/ESTabBarController.svg?branch=master)](https://travis-ci.org/eggswift/ESTabBarController)
[![CocoaPods](https://img.shields.io/cocoapods/v/ESTabBarController-swift.svg)](http://cocoapods.org/pods/ESTabBarController-swift)
[![Carthage Compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)
[![Swift v4](https://img.shields.io/badge/Swift-4-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Twitter](https://img.shields.io/badge/Twitter-@lihao_iOS-blue.svg?style=flat)](https://twitter.com/lihao_iOS)
[![Twitter](https://img.shields.io/badge/Weibo-@李昊_____-orange.svg?style=flat)](http://weibo.com/5120522686/profile?rightmod=1&wvr=6&mod=personinfo&is_all=1)
[![Chat Gitter.im](https://badges.gitter.im/ESTabBarController/Lobby.svg)](https://gitter.im/ESTabBarController/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

### [中文介绍](README_CN.md)

**ESTabBarController** is a highly customizable TabBarController component, which is inherited from UITabBarController.

### Why?

In real-world development, we may encounter the situation that customizing the UITabBar. For instance: change font style, add animation, use bigger item. However it's hard to do with UITabBarItem.

**With ESTabBarController, You can easily achieve these！**

-| Feature |Description
-------------|-------------|-------------
1| Default style | You can get system-like style by initializing the TabBar with ESTabBarController directly.    UITabBarController style:   ![System native style](Resources/SystemStyle.png)   ESTabBarController default style:   ![ES system-like style](Resources/CustomStyle.png)
2| Default style with "More" item | If the items are more than the maximum number of displays, there will be a "More" item.   UITabBarController with "More":   ![enter image description here](Resources/SystemMoreStyle.png)   ESTabBarController with "More":   ![enter image description here](Resources/CustomMoreStyle.png)
3| Mix UITabBarItem and ESTabBarItem | You can set any item as you want, including UITabBarItem and ESTabBarItem.   ESTabBar and UITabBar mixed style:   ![enter image description here](Resources/MixtureStyle.png)   ESTabBar and UITabBar mixed style with "More":   ![enter image description here](Resources/MixtureMoreStyle.png)
4| UIKit attributes | ESTabBarController is compatible with UITabBarController, UITabBar and UITabBarItem's most API attributes. You can migrate to ESTabBarController without any modification of the origin code.    Compatible with UITabBarController's `selectedIndex`:   ![enter image description here](Resources/SelectIndexCode.png)
5| Any nesting with UINavigationController | Developing with`UITabBarController`, there are two common ways to handle layers:   First :   ├── UITabBarController   └──── UINavigationController   └────── UIViewController   └──────── SubviewControllers   Second :   ├── UINavigationController   └──── UITabBarController   └────── UIViewController   └──────── SubviewControllers   In the first case, need to set `hidesBottomBarWhenPushed = true` when pushing subViews. The second is not.   In ESTabBarController, add Container views to UITabBar to be compatible with these two ways。
6| Customizable style | With ESTabBarController, you can：  1. Customize selected item's color and style:   ![enter image description here](Resources/CustomSelectStyleGif.gif)   2. Add selecting animation:    ![enter image description here](Resources/CustomSelectAnimateGif.gif)   3. Customize item's background color:   ![enter image description here](Resources/CustomBackgroundGif.gif)   4. Add highlight animation:   ![enter image description here](Resources/CustomHighlightGif.gif)   5. Add animation to prompt users:   ![enter image description here](Resources/CustomImpliesGif.gif)   6. And much more ...  
7| Customizable item's size   Customizable click event | You can easily customize item's size using ESTabBarController.   **When the button's frame is larger than TabBar, through the use of HitTest to achieve making outer TabBar area click valid.**   In addition, ESTabBarController can customize click event, and through a block to callback super-layer to handle.   With big item in the middle of TabBar:   ![enter image description here](Resources/CustomStyle2.png)   With a special hint style:   ![enter image description here](Resources/CustomStyle3.png)   Customize click event:   ![enter image description here](Resources/CustomHitGif.gif)
8| Default notification style |  You can get system-like notification style by initializing the TabBar with ESTabBarController directly.   UITabBarController notification style:   ![enter image description here](Resources/SystemNotificationStyle.png)   ESTabBarController system-like notification style:   ![enter image description here](Resources/CustomNotificationStyle.png)
9| Customizable notification style | With ESTabBarController, you can：  1. Customize notification animation:   ![enter image description here](Resources/CustomNofticationGif.gif)   ![enter image description here](Resources/CustomNofticationGif2.gif)   2. Customize prompt style:   ![enter image description here](Resources/CustomNofticationGif3.gif)   3. And much more ...  
10| Lottie | Through customizing ContentView, you are able to add Lottie's LAAnimationView to Item(s)   ![enter image description here](Resources/LottieGif.gif)

## Requirements

* Xcode 8 or later
* iOS 8.0 or later
* ARC
* Swift 3 or later

## Demo

You can download and build ESTabBarControllerExample project, and you will find more examples to use ESTabBarController, and also more examples to customize UITabBar。

## Usage

### CocoaPods

``` ruby
pod "ESTabBarController-swift"
```

### Carthage

```ruby
github "eggswift/ESTabBarController"
```

### Manually

``` ruby
git clone https://github.com/eggswift/ESTabBarController.git
open ESTabBarController
```

## TODO

1. The Containers' layout is purely based on code，using Autolayout will be better.
2. When there is "More", if edit it will occurs problem.
3. Partial UITabBarItem attributes are not bridge to ESTabBarItem.
4. ~~The picture of 'More' item in ESTabBarItemMoreContentView is not set into framework, plan to convert it to CGBitmap.~~


## Acknowledgement

* [animated-tab-bar](https://github.com/Ramotion/animated-tab-bar) by   
* Partial pictures in Example are from  


## About

ESTabBarController is developed and maintained by [Vincent Li](mailto:lihao_iOS@hotmail.com). If you have any questions or issues in using ESTabBarController, welcome to [issue](https://github.com/eggswift/ESTabBarController/issues).  
If you want to contribute to ESTabBarController, Please submit [Pull Request](https://github.com/eggswift/ESTabBarController/pulls), I will deal with it as soon as possible.  

[![Twitter URL](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/intent/tweet?text=https://github.com/eggswift/ESTabBarController)
[![Twitter Follow](https://img.shields.io/twitter/follow/lihao_ios.svg?style=social)](https://twitter.com/lihao_iOS)


## License

The MIT License (MIT)

Copyright (c) 2013-2016 eggswift. All rights reserved.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)