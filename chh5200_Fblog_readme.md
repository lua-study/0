# Fblog
```
一个基于vue3.x+element-ui简洁的博客模板
```

## 演示地址
[demo](http://www.fengziy.cn/fBlog/)
[备用地址](https://fengziye.github.io/blog/)
```
http://www.fengziy.cn/fBlog/

https://fengziye.github.io/blog/
```

## 项目截图

### 首页（懒，博文列表都一样 :sweat_smile: ）

![首页](https://images.gitee.com/uploads/images/2019/0326/212821_d068d429_1658323.png "屏幕截图.png")

### 国际化效果（只截了一张图）

![国际化](https://images.gitee.com/uploads/images/2019/0326/213439_7719202a_1658323.png "屏幕截图.png")

### 博文页

![博文页](https://images.gitee.com/uploads/images/2019/0326/213002_d950f6fe_1658323.png "屏幕截图.png")

### 申请友链

![申请友链](https://images.gitee.com/uploads/images/2019/0326/213340_0de8aa80_1658323.png "屏幕截图.png")

### 归档（标签页与他类似）

![归档](https://images.gitee.com/uploads/images/2019/0326/213057_d1b8d6ac_1658323.png "屏幕截图.png")

### 关于页

![关于](https://images.gitee.com/uploads/images/2019/0326/213232_9b8a17df_1658323.png "屏幕截图.png")



## 安装
```
npm install
```
## 运行
```
npm run serve
```

## 打包
```
npm run build
```

## 部署
把build的dist文件命名为fBlog(自取)上传到服务器

### nginx配置
```
location /fBlog/ {
	root /usr/local/nginx/;#fBlog所在的更目录
	try_files $uri $uri/ /fBlog/;
}
```

## 演示
```
域名:4567/fBlog/
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)