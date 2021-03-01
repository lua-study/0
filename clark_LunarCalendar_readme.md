#LunarCalendar

基于 [electron](https://github.com/atom/electron) + [menubar](https://github.com/maxogden/menubar) + [react](https://github.com/facebook/react) + [materialize](https://github.com/Dogfalo/materialize) 
构建的`工具栏日历应用`，适用于Mac，Windows，Linux平台。


日历数据由 [LunarCalendar](https://github.com/zzyss86/LunarCalendar) 提供。


======

**MAC 版下载链接** [LunarCalendar.app](http://pan.baidu.com/s/1dDB7CIH) 

======

![lc](http://i1.tietuku.com/6cc696c379811560.gif)

## 开发和构建

依赖于node.js环境，请预先安装。

可直接在浏览器中打开`index.html`进行预览测试，但注意jQuery的引用问题。

```
git clone https://git.oschina.net/sinceow/LunarCalendar.git

cd LunarCalendar
```

> 第一步，安装Node.js依赖和利用Bower下载前端依赖

```
npm install
```

> 第二步，利用Gulp构建项目并 Watch SASS 和 JS

```
npm start
```

进行本地测试（可选）

```
npm run-script electron
```

> 第三步，生成APP

```
#生成osx状态栏日历
npm run-script build

#生成win32菜单栏日历
npm run-script build-win
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)