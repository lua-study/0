# oauth授权登录comoser包

>只是一个包，没有什么依赖

**目录结构：**
```
|--api         第三方授权接口
|--config      配置文件（公共）
|--helper      助手文件
|--lib         核心类库
|--Github.php  Github授权渠道入口文件   
|--Qq.php      Qq授权渠道入口文件   
|--index.php   使用demo   
|--Wx.php      Wx授权渠道入口文件   

```

**使用方法：**

```
在项目中的composer.json 文件中添加如下内容

"require-dev": 
{
    "fankers/oauth": "dev-master"
},
    
"repositories": 
[
    {
        "type": "vcs",
        "url":  "git@gitee.com:fankers/oauth.git"
    }
]
    
```




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)