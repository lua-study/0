# wechat-demo
wechat-demo 前后端分离场景开发微信公众号。

```$xslt
服务端：wechat-demo
vue前端：wechat-demo-vue
```

##### 微信官方文档：https://mp.weixin.qq.com/wiki 

> #### 前期准备
* 首先，你得有个测试号：[传送门](https://mp.weixin.qq.com/debug/cgi-bin/sandbox?t=sandbox/login)
* 登陆后，进行以下配置
```$xslt
1、JS接口安全域名
2、接口权限表 -> 网页帐号 -> 网页授权获取用户基本信息

注：
    生成环境：直接配置正式的网站域名
    开发环境：需要配置外网可访问的域名(使用内网穿透,参考：http://natapp.cn)
```
* 下载安装微信开发者工具：[传送门](https://mp.weixin.qq.com/wiki?t=resource/res_main&id=mp1455784140)


> #### 前端使用
* 修改dev的代理(config/index.js)
```$xslt
proxyTable: {
  '/api': {
    // 修改为对应的服务端地址
    target: 'http://localhost:8081'
  }
},
```
* 编译运行
```$xslt
npm install
npm run dev
```
* 外网访问
```$xslt
使用内网穿透(参考：http://natapp.cn) 获取能访问前端项目的域名
后续调试，均使用该域名。
```
* 简单介绍
```$xslt
测试页面：components/HelloWorld.vue
微信相关：wechat/index.js
```

> #### 服务端使用
* 配置微信公众号信息
```$xslt
修改application.properties文件中配置：

#微信公众号配置信息
wechat.mp.appId=
wechat.mp.secret=
#wechat.mp.token=
#wechat.mp.aesKey=
```
* 修改常量
```$xslt
package com.sam.constant;

/**
 * @author sam
 * @since 2018/3/28
 */
public class Constant {

    public static final String BASE_HOST = "http://qn8gv9.natappfree.cc";

}

BASE_HOST 修改为 前端通过外网穿透获取到的外网地址
该 BASE_HOST 在授权完毕重定向回来的时候用到
```
* 启动项目


> #### 授权流程讲解
```$xslt
1、前端：访问 http://qn8gv9.natappfree.cc/   (该地址为内网穿透地址)
2、前端：项目中调用 wechat.authorize()方法(接口：/api/init/authorize)，向服务端发起授权请求获取用户信息
3、服务端：判断session中是否存在wxMpUser微信用户信息
        如果有，直接返回用户信息
        如果没有，响应前端，提示前端 window.location.href = res.data.redirect 重定向到微信授权
4、服务端：微信授权通过后，微信服务器会重定向到服务端的/api/wechat/userInfo 获取用户信息接口
        该接口处理完毕后，会重定向到前端页面
5、授权流程完毕，前端再次调用wechat.authorize()（此时服务端session中已有用户信息）获取用户信息
        
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)