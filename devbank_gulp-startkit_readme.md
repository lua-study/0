# Gulp StartKit

## 目录结构

```
gulp-startkit
├─ README.md
├─ app
│    ├─ _assets
│    │    ├─ fonts
│    │    ├─ images
│    │    ├─ scripts
│    │    └─ styles
│    ├─ _data
│    │    └─ global.json
│    ├─ _includes
│    ├─ _layouts
│    ├─ _static
├─ docs
│    ├─ README.md
│    └─ gulp-docs.png
├─ gulp
│    ├─ README.md
│    ├─ config.js
│    ├─ config.js.example
│    ├─ tasks
│    └─ util
├─ gulpfile.js
├─ mock
├─ package.json
├─ screenshot
└─ tests
```

## 测试环境任务列表

```
gulp build
gulp watch
gulp browsersync
gulp delete

gulp images
gulp copy:fonts
gulp copy:static

gulp styles
gulp csslint
gulp cssmin

gulp js
gulp jsconcat
gulp jshint
gulp jsmin

gulp html

gulp manifest
gulp base64
gulp sprites
gulp sizereport
```



## 正式环境任务列表

```
gulp browsersync:production
gulp build:production
gulp gzip
gulp rsync
gulp webp

gulp copy:fonts:production
gulp html:production

gulp optimize:css
gulp optimize:html
gulp optimize:images
gulp optimize:js

gulp rev
gulp rev:collect
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)