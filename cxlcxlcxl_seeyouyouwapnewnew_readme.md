## 配置
### 服务器地址
config/config.js中
```
export const apiBaseUrl = 'http://www.seeyouyou.com/';//注意最后斜杠,填写你的域名地址
```

### 海报H5中保存图片跨域
nginx中添加以下配置
```
    location ~ .*\.(gif|jpg|jpeg|png)$ {  
      add_header Access-Control-Allow-Origin *;
      add_header Access-Control-Allow-Headers X-Requested-With;
      add_header Access-Control-Allow-Methods GET,POST,OPTIONS;
    }
```

### 函数差异说明
switchTab
微信小程序有success事件，支付宝小程序暂无此事件

### 目录说明
1.common ：扩展js函数库
2.components:组件文件夹
3.config:配置文件夹
4.pages:页面文件夹
5.statics:静态文件目录
6.store:店铺配置Js


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)