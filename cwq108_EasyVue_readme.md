# EasyVue

#### 介绍
EasyVue 是一个简易使用vue的小工具,让你可以轻易的再浏览器环境中使用vue生态,采用异步加载方式完成单文件组件
#### 软件架构
软件架构说明

#### 使用说明

1. 克隆本项目,将EasyVue文件夹放在您的的web应用的根目录下,启动web应用
2. 注意:若要修改文件结构,需在/EasyVue/static/index.html中,可以通过修改cxt参数,来修改访问路径前缀
    
```
$.EasyVue({
        dev:true,
        el:"#app",
        cxt:"/EasyVue/static",
        routeUrl:"routes.json",
        loginUrl:"/login",
    });
```


#### 参与贡献

1. Fork 本仓库
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)