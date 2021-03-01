Whats Git on Android
====================

一个用于 **跨提供商** 查看仓库/项目的 Android 应用.

一个 **烧脑** 的开源Android项目.

一个采用 **Reactive（响应式编程）** 模式开发的 Android 应用。


Source
------

由于使用了 **烧脑组合**, 不建议 *开发新手* 阅读本项目源码.

源码特点:

- 使用 Gradle 构建项目
- 不兼容 Eclipse 结构
- 多模块. 最主要是 git 与 app. 另外的 coding, oscGit 以及 github 用于接入特定提供商
- 使用 AccountManager 实现账号管理 .
- XXX 和 WTF
- 使用 Picasso 加载图片
  (目前只声明了依赖)
- 使用 Retrofit 请求 RESTful API
  (期待它的 2.0 版本)
- 使用 Timber 显示 LOG
  (我很懒, 所以用它)
- 使用 ButterKnife 绑定 view 与 事件
  (我很懒, 所以用它)
- 单元测试与指令测试(或指令测试) 共存
  (目前只声明了依赖)
- 使用了烧脑库

已使用的烧脑库有:

- Dagger by Square: 依赖管理, 特点: 基于模块声明与注解. 烧脑指数 **??**
- RxJava by ReactiveX: Java响应式扩展, 特点: 函数式. 烧脑指数 **????**


暂不考虑的设计有:

- Mortar by Square: All in one activity, `Path` `Screen` `View` `Presenter` mode.
- MVC, MVP, MVVM


GitHub
------

-   使用 github 模块要求在 github/ 目录下添加 github-client.properties 文件:

    内容为:

    ```
    CLIENT_ID=Your Client ID
    CLIENT_SECRET=Your Client Secret
    ```

    这两项要求你使用 github 账号创建应用, GitHub 为你提供 Client ID 和 Client Secret.

    以下是操作页面:

     


-   如果你不需要 github 模块, 可以 从 app 模块的 `AppMain` 的 `Platform.initialize` 中删除 `GitHubModule.class`,
    并注释掉 app/build.gradle 文件中的 依赖:

    ```
    dependencies {
        compile project(":git")
        compile project(":coding")
        compile project(":oscGit")
    //    compile project(":github")
    ```

-   GitHub 数据的加载更多暂不支持。待 Retrofit 2.0 出来之后再作支持。


Pull Requests
-------------

项目代码尚未稳定, 如需 PR , 请先添加一条 讨论, 以说明意图.

欢迎 在 Issues(讨论) 中 讨论/吐槽/夸赞 本项目.


题外话
------

以下是一些与本项目不相关的内容.


### 想看 MVP 项目?

我此前的一个用于探索 **烧脑Android** 的应用:

 

其中包含了: `Data/Domain/UI` 分层, `MVP`, `DI` 依赖注入, `EventBus`, `AccountManager` 等等.


### 想用 Gradle, 又得兼容 Eclipse ?

在此附一份源码结构的通用配置, 特别适用于为已存在的 Eclipse 项目添加 Gradle 构建:

```groovy
androidSourceSetsEclipseStyle = {
    manifest.srcFile 'AndroidManifest.xml'
    java.srcDirs = ['src']
    resources.srcDirs = ['src']
    aidl.srcDirs = ['src']
    renderscript.srcDirs = ['src']
    res.srcDirs = ['res']
    assets.srcDirs = ['assets']
    jni.srcDirs = []
    jniLibs.srcDirs = ['libs']
}
```

使用方法:

```groovy
android {
    sourceSets {
        main androidSourceSetsEclipseStyle
    }
}
```


License
-------

Coding is available under the MIT license. See the MIT-LICENSE.txt file for more info.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)