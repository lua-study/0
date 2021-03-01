## 一、功能

Golang实现的JetBrains激活服务器，参考代码来源于网络，做了少量更改。

## 二、适用版本

WebStorm, Goland, PyCharm, DataGrip 2017.3+版本测试有效。

理论上支持各IDE的2017.3以上版本，2017.3以下版本没有测试。

# 三、激活方法

先编译代码，得到服务端。

默认监听8011端口，如需修改可携带`-port`参数，如`./server -port=8080`可使服务监听8080端口。

开启成功后会打印日志信息提示：

```
2018/01/11 22:20:35 Jetbrain licence server start and listen port 8011
```

然后打开软件，在弹出的激活页面选择激活方式`Licence server`，输入对应的`IP+PORT`，注意不可省略`http://`部分。

![](http://ww1.sinaimg.cn/large/005wtJ8cgy1fnd19qyi8hj30ce0c0t8y.jpg)

点击`Activate`即可完成激活：

![](http://ww1.sinaimg.cn/large/005wtJ8cgy1fnd19qwyl3j309g031glh.jpg)

![](http://ww1.sinaimg.cn/large/005wtJ8cgy1fnd19rihz9j30hs0b4gpr.jpg)




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)