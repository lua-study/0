# MultiImageSelector
仿微信实现多图选择。支持单选和多选两种模式

###截图
![Example1](art/example_1.png) ![Select1](art/select_1.png) ![Select2](art/select_2.png) ![Select3](art/select_3.png) ![Select4](art/select_4.png)

-------------------

###运行DEMO

>./gradlew installDebug

###快速开始
* 第0步
把模块 `multi-image-selector` 作为你的项目依赖添加到工程中.

* 第1步 
在你的 `AndroidManifest.xml` 文件中添加权限 `android.permission.READ_EXTERNAL_STORAGE`.
别忘了同时在 `AndroidManifest.xml` 中声明 `MultiImageSelectorActivity`和`PreviewPicturesActivity` 这两个Activity.
```xml
         
         
```

* 第2步
代码中调用，例如:
```java
     //yourActivity-Activity,requestCode-requestCode,maxNum-最多选择的图片数,selectedMode-选择模式（单选/多选）
     MultiImageSelectorActivity.startSelect(yourActivity, requestCode, maxNum, selectedMode);
```

* 第3步
在你的 `onActivityResult` 方法中接受结果. 例如:
```java
@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
    super.onActivityResult(requestCode, resultCode, data);
    if(requestCode == REQUEST_IMAGE){
        if(resultCode == RESULT_OK){
            // 获取返回的图片列表
            List  path = data.getStringArrayListExtra(MultiImageSelectorActivity.EXTRA_RESULT);
            // 处理你自己的逻辑 ....
        }
    }
}
```

* 第4步
没第4步了，就这样就OK啦~ :)

-------------------

* 具体可以参考`MultiImageSelectorActivity.java`的实现

-------------------

###感谢

* [square-picasso](https://github.com/square/picasso) A powerful image downloading and caching library for Android
* [lovetuzitong-MultiImageSelector](https://github.com/lovetuzitong/MultiImageSelector) 此项目根据lovetuzitong-MultiImageSelector修改而来，修复了一些BUG，去掉了拍照功能（如果你需要也可以根据原项目添加）

-------------------

###License
>The MIT License (MIT)

>Copyright (c) 2015 Nereo

>Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

>The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)