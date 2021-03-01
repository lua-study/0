# 使用AnyProxy自动抓取微信公众号数据-包括阅读数和点赞数
### 目录

[TOC]

准备工作：

- **安装node.js**
- **安装AnyProxy代理服务器**
- **使用我提供的sql文件和js代码**

-------------------

## 原理图
![AnyProxy原理图](http://img.blog.csdn.net/20171220100138826?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvenN5b3VuZw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

## 1.安装Node.js

去Node.js 官网下载对应操作系统的安装包，然后按照默认步骤安装至电脑中。

下载地址：http://nodejs.cn/download/

安装好之后，打开终端或命令行运行输入下面代码，检查是否安装成功，如果成功，会输出当前Node 版本号。
>node -v

##2.安装AnyProxy 代理服务器
命令行或终端输入以下命令，表示全局安装AnyProxy 程序包：
>npm install -g anyproxy

如果是Mac 系统，可能需要在命令前添加sudo ，然后输入密码：
>sudo npm install -g anyproxy

输入以上命令后，电脑会自动从网络下载程序包并安装。

参考网址：https://github.com/alibaba/anyproxy

##3. 启动AnyProxy
终端输入：
>anyproxy

Mac 系统需输入（以后的命令也是需要输入sudo ，下面就忽略不写了）：
>sudo anyproxy

如出现下面提示，则表明安装成功：

![启动AnyProxy](http://img.blog.csdn.net/20171220101222929?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvenN5b3VuZw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

##4. 安装HTTPS 网络传输所需的证书

####**电脑安装**

微信采用加密的HTTPS 网络传输，所以需要安装证书。结束上面的运行程序，一般为ctrl + c 。然后在终端运行命令：

>anyproxy --root

此时会在文件夹生成rootCA.crt 证书与对应的密钥rootCA.key，根据提示打开对应文件夹，双击安装rootCA.crt 证书。

####**手机安装**

电脑命令行或终端输入下面命令启动代理程序：
>anyproxy

然后浏览器中输入网址http://localhost:8002/qr_root，则会出现证书二维码，然后手机扫描此证书二维码，下载按照提示完成安装即可。

参考网址1：http://anyproxy.io/cn/

####**安装mysql 模块部分**

默认你的电脑上已经安装了mysql 数据库，现在node 连接mysql 数据库，也需要安装一个程序包来实现：

>npm install -g mysql

##5.程序部分
####**程序地址**

windows 程序AnyProxy 默认的安装目录在：
>C:\Users\你的用户名\AppData\Roaming\npm\node_modules\anyproxy

Mac 安装目录为：
>/usr/local/lib/node_modules/anyproxy

本程序为修改和增加AnyProxy 中lib 文件中对应的代码部分。

####**代码部分**

文章末尾获取下面5个文件，你只需覆盖掉lib 目录中对应的文件即可。（建议先备份）

    ./anyproxy
      ./lib
         myRule.js
         rule_default.js
         1.png
         requestHandler.js
         httpsServerMgr.js
        
- 其中逻辑部分主要写在`myRule.js `文件中，此文件已做了详细的注释

- `rule_default.js `是判断各种网络请求数据然后调用对应的方法

- `1.png `为很小的一个图片，替换手机所有图片请求，加快网络传输速度  

- 其余两个文件是注释掉了之前在终端打印的一些提示性的字符，不重要

####**运行程序部分**

>anyproxy -i

终端输入以上命令即可运行。参数`-i` 表示开启`HTTPS` 。

可操作`myRule.js` 文件，选择对应的功能。修改文件后，需重启程序。

运行后，确保电脑和手机在同一个WiFi 环境下，然后根据提示设置手机WiFi 的代理，输入代理网址与端口（运行后终端会提示连接地址）。

下面是我的设置，手机的代理服务器设置为手动，代理主机名应和电脑IP相同，代理服务器端口为8001：
![这里写图片描述](http://img.blog.csdn.net/20171220105725812?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvenN5b3VuZw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

之后选择查看公众号文章，即可自动抓取数据至数据库中。

####**myRule.js 代码主要部分**

三个主要函数：

>getProfile - 对历史页的操作，获取文章其他数据；插入自动翻页代码
getReadAndLikeNum - 获取文章点赞、阅读、打赏等数据
insertJsForRefresh - 对文章页的操作，主要是插入自动翻页代码

####**代码原理**

此程序为事件驱动。即一开始要给定一个触发事件，例如打开微信公众号查看历史消息或打开公众号某篇文章。

微信打开历史消息页之后会触发事件，运行`getProfile`函数，跳至下一个历史消息页后又会触发打开历史消息页此事件。

同理，微信打开文章页会触发事件运行`insertJsForRefresh` 函数，此函数会向网页中插入一段脚本自动翻页，当翻页后，又会触发此事件，然后一直运行下去。

同理，打开文章页时，微信会请求另一个链接，然后会自动触发`getReadAndLikeNum` 函数,获取阅读量和点赞数。

历史消息页有4种插入js 代码的方式，已在代码中注释。

####**Js 注入详解**

文章页自动翻页原理为在网页head 部分插入类似以下形式代码，表示隔5s 跳转至下一个文章页

```
 
```

历史消息页注入Js 脚本示例，将以下脚本插入至返回给微信客户端的数据中，可以使网页自动下拉至最低端，到最早一篇文章之后再跳转至下一个历史消息详情页：

```
 
    var end = document.createElement("p");
    document.body.appendChild(end);
    (function scrollDown(){
        // 下拉至页面最低端后，微信会自动向服务器请求数据
        end.scrollIntoView();
        var loadMore = document.getElementsByClassName("loadmore with_line")[0];
        // 判断是否到达最早一篇文章
        if (!loadMore.style.display) {
            document.body.scrollIntoView();
            // 插入meta，使10秒后自动翻页
            var meta = document.createElement("meta");
            meta.httpEquiv = "refresh";meta.content = "10;url=' + nextProLink + '";
            document.head.appendChild(meta);
        } else {
            // 每个随机时间段下拉网页
            setTimeout(scrollDown,Math.floor(Math.random()*2000+1000));
        }
    })();
 
```
在代码部分中有4个这样类似的脚本，用于实现不同情况下特定的功能。你可在运行时作出选择。
####**数据库部分**

`myRule.js`文件开头会有数据库连接，对应修改成自己的数据库配置。

// 创建数据库连接，需根据自己数据库账号密码修改
```
var connection = mysql.createConnection({
    host: 'localhost',
    user: 'root',
    password: '0000',
    database: 'phone_weixin'
});
```
数据库中有4张表，分别对应文章信息，历史消息抓取记录和公众号信息。
```
msg
history
mpaccout
```
表的结构也在文章末尾文件中。在mysql 数据库中新建好即可。
####**数据库字段解释**
```
msg.sql
    id  -  文章id，自动递增
    msg_title  -  文章标题
    msg_link  -  文章永久链接
    publish_time  -  文章发布时间，13位时间戳形式
    modi_time  -  数据抓取时间，13位时间戳形式
    read_num  -  阅读量
    like_num  -  点赞量
    reward_total_count  -  安卓手机赞赏量
    msg_idx  -  文章发布位置，首条、二条等等
    msg_biz  -  公众号唯一标识，重要
    msg_source_url  -  文章阅读原文链接，若无则空
    msg_cover  -  文章封面图片链接
    msg_digest  -  文章摘要
    is_fail  -  文章是否删除，如果删除改为1，下次就不在抓取
    copyright_stat  -  文章是否原创标识 11为原创 100为无原创 101为转发
    author  -  文章作者
    
mpaccount.sql
    id  -  公众号id，自动递增
    biz  -  公众号唯一标识
    nickname  -  公众号名称
    metavalue  -  公众号id
    
history.sql
    id  -  公众号id，自动递增
    biz  -  公众号唯一标识
    url  -  上次抓取的链接
    moditime  -  上次抓取时间
```
  
---------
文件地址：https://gitee.com/zsyoung01/AnyProxy
博主码云地址：https://git.oschina.net/zsyoung01,欢迎关注！

参考文章：
链接：http://www.jianshu.com/p/13d70a5a244d
因原博主的js和sql使用后有部分问题，所以略有改动。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)