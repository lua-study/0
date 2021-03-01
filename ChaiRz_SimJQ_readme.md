# SimJQ
SimJQ全称Simple JQuery，支持类似JQuery语法的常用DOM操作和网络请求功能。它不到4K大小，适合应用于存储空间极其有限的场景。

开源中国 [https://www.oschina.net/p/simjq](https://www.oschina.net/p/simjq)

项目主页 [https://gitee.com/Leytton/SimJQ/](https://gitee.com/Leytton/SimJQ/)

项目演示 [http://leytton.gitee.io/simjq](http://leytton.gitee.io/simjq)

详细介绍 [http://blog.csdn.net/leytton/article/details/78388553](http://blog.csdn.net/leytton/article/details/78388553)

使用时引入js文件即可
>   

支持函数链式调用，如：
```
$().tag('p').text("hello").attr('id','test').outHtml();
$().dom(' 11111  hello   ').attr('id','test').outHtml();
```

注: $(),s(),$s()都行，与Jquery冲突时在Jquery之前引入js文件，采用s()或$s()

 **1、为什么是4K？** 

簇是文件系统分配存储空间的基本单位，无论文件大小，它占用的空间总是整数个文件簇。即便你的文件只有1个字节(Byte)，它仍旧会占用一个文件簇的大小，也就是4KBytes。

 **2、用在哪里？** 

- 2.1对文件大小有严格要求的应用场景
- 2.2Android
    打包本地HTML资源尽量减小包大小
- 2.3嵌入式网络通信
    STM32、NodeMCU、Arduino等HTTP请求返回Js文件
- 2.4 等待你的发挥

# 升级日志
## 1.6版本
添加$(this)支持
## 2.1版本
改用H5写法,优化核心算法，并新增了一些常用函数，文件体积压缩后更小只有3.45KB
## 2.2版本
1、修复val、html、text等函数参数为''与null区别的问题
2、为simJQ完善click方法，click方法现能多次绑定不同的方法，并能通过“click()”触发所绑定的方法

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)