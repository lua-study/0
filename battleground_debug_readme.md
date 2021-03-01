#
debug-core库使用手册


* 库名称：`com.abooc.debug:debug-core:latest.release`
* 当前版本：`v1.2.1`
* 开发语言：`Java`
* 适于开发平台：`Android`

## 概述

**简述**：封装**debug-core**库，用于开发期间的调试代码，提高生产力。

本库主要有以下功能：

1. **打印日志**：封装android.util.Log类，方便日志输出
2. **定位代码**：输出的日志可以快速定位到具体代码
3. **Toast.show()**：方便使用Toast

## 介绍

主要功能类：

* `Debug.class`
* 负责debug日志打印（默认**TAG**为'Debug'）。
* `Toast.class`
* 显示吐司

预览主要方法：

- `Debug.debugOn();`
- `Debug.debugOff();`
- `Debug.enable(boolean enable);`
- `Debug.anchor();`
- `Debug.anchor(anything to string);`
- `Debug.error(string);`
- `Debug.setLevel(Log.level);`
- `Debug.setTag("TAG");`
- `Debug.debugClass();`
- `Debug.destroyClass();`

## 使用方法

**1. 添加远程仓库**

```
maven{ url 'http://oss.abooc.com/repository/maven-public/' }
```

**2. 引入项目**

```
compile 'com.abooc.debug:debug-core:latest.release'

```

**3. 开启日志**

```java
public class AppApplication extends Application {

@Override
public void onCreate() {
super.onCreate();
Debug.enable(BuildConfig.DEBUG); // 开启Debug
super.onCreate();
...

```

**4. 用于代码定位（代码锚点）**

**场景：**你想调试一下`MainActivity`的`onResume`方法和`onDestory`方法是否有在你的预期内执行：

```java
public class MainActivity extends AppCompatActivity {

@Override
protected void onResume() {
super.onResume();
Debug.anchor(); // 加一个定位
...

@Override
protected void onDestory() {
super.onDestory();
Debug.anchor(); // 加一个定位
...
```

此时，日志打印：

```
// PID 包名 级别 TAG 类名 方法 代码超链到行
$ 30586-30586 /包名 D/Debug:MainActivity.onResume(MainActivity.java:19):

```

即，`Debug.anchor()`方法的作用：

* 定位到**类名**、**方法名**、**代码行**
* 可超链接到代码

此方法通常用于：对代码加锚点，方便检验代码执行顺序是否与期望一致。

**5. 用于打印**

```java
@Override
public void onReceived(String message) {
Debug.anchor(message); // 打印'message'
}
```

方法`Debug.anchor(message)`支持类型：

- **String** `Debug.anchor(String message)`
- **int** `Debug.anchor(int message)`
- **boolean** `Debug.anchor(boolean message)`
- **Object** `Debug.anchor(Object message)`

**6. 用于`ERROR`级别打印**

```java
@Override
public void onFailed(String error) {
Debug.error(error); // 打印'error'
}
```

输出Log为`ERROR`级别。

## 高级使用

**1. 过滤本类的日志**

自动将**本类名**作为打印日志的`TAG`。

```java
public class MainActivity extends AppCompatActivity {

@Override
protected void onCreate(Bundle savedInstanceState) {
Debug.debugClass();
super.onCreate(savedInstanceState);
...
```

**输出**：

```
// PID 包名 级别 TAG 类名 方法 代码超链到行
$ 30586-30586 /com.xxx.xx D/MainActivity:MainActivity.onCreate(MainActivity.java:19):

```

**2. 自定义日志**`TAG`

```java
Debug.setTag("test");
```

**3. 修改日志打印级别**

```java
Debug.setLevel(Log.VERBOSE);
```

支持级别：

* Log.VERBOSE
* Log.DEBUG
* Log.INFO
* Log.WARN
* Log.ERROR

## 其他使用

手动开启：`Debug.debugOn();`

手动关闭：`Debug.debugOff();`


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)