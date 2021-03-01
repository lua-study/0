# vue-app

> 重写了关于vue-cil的几个问题

## 构建

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

```
## 关于脚手架的修改
1. 所谓的组件是可以高度复用的，所以这边把页面做成pages
2. router用于编写路由,原则上是引用pages，不应用components
3. 删除了assets,使用公共文件夹common来完成css,images,js
4. 更改了css的引用
5. 准备添加三层架构，这边还未处理
6. 增加了自动增加页面的功能，方便了日常开发
7. 建议增加,可以测试虽然起服务

```
   npm install -g browser-sync 
``` 
``` 
   通过 browser-sync start --server --files "**/*.css, **/*.html, **/*.js"编译
```
8. 关于字体引入了font-awesome,详情看下面地址
```
http://fontawesome.dashgame.com/
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)