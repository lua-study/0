Loppo 是一个简单、好用的静态文档生成器，可以一键生成 Markdown 文档站点，请看 [demo](http://redux.ruanyifeng.com/)。

## 特点

- 简单的配置 ([示例](https://raw.githubusercontent.com/ruanyf/loppo/master/loppo.yml.default))
- 清晰的目录 ([示例](https://raw.githubusercontent.com/ruanyf/redux-docs/master/chapters.yml))
- 易用的模板语法 ([示例](https://raw.githubusercontent.com/ruanyf/redux-docs/master/themes/oceandeep/page.template))
- 内置[功能性命令](docs/commands.md)

## 用法

**提醒：Loppo 目前还是 alpha 状态，请谨慎使用。**

首先，将文档项目整理成下面的文件结构。

```
|- myProject
   |- README.md
   |- docs
      |- page1.md
      |- page2.md
      |- ...
```

然后，安装 Loppo。

```bash
$ npm install loppo -g
```

进入项目目录。

```bash
$ cd myProject
```

运行命令。

```bash
$ loppo
```

运行结束后，项目根目录下会生成一个`dist`子目录，生成的站点就在该目录中。你可以运行下面的命令，在浏览器中浏览站点。

```bash
$ open dist/index.html
```

## 许可证

GPL v3



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)