## 简介
[ jeeweb-vue-admin](https://gitee.com/dataact/jeeweb-vue-admin) 是一个基于vue-element-admin的，并且需要配合jeeweb的前后端分离模块一起开发模块。

[后端源码（JeeWeb）](https://gitee.com/dataact/jeeweb/)

[在线访问](http://vuedemo.jeeweb.cn)

## 界面预览
![输入图片说明](https://images.gitee.com/uploads/images/2018/1120/165223_c531df44_1394985.png "QQ截图20181120164919.png")

![输入图片说明](https://images.gitee.com/uploads/images/2018/1120/165233_c96b6c74_1394985.png "QQ截图20181120164934.png")

![输入图片说明](https://images.gitee.com/uploads/images/2018/1120/165242_9d09ed0e_1394985.png "QQ截图20181120164953.png")

![输入图片说明](https://images.gitee.com/uploads/images/2018/1120/165255_29ce44cf_1394985.png "QQ截图20181120165031.png")

## 开发

```bash
# 克隆项目
git clone https://gitee.com/dataact/jeeweb-vue-admin.git

# 安装依赖
npm install

# 建议不要用 cnpm 安装 会有各种诡异的bug 可以通过如下操作解决 npm 下载速度慢的问题
npm install --registry=https://registry.npm.taobao.org

# 启动服务
npm run dev
```

浏览器访问 http://localhost:9527

## 发布

```bash
# 构建测试环境
npm run build:sit

# 构建生产环境
npm run build:prod
```

## 其它

```bash
# --report to build with bundle size analytics
npm run build:prod

# --generate a bundle size analytics. default: bundle-report.html
npm run build:prod --generate_report

# --preview to start a server in local to preview
npm run build:prod --preview

# lint code
npm run lint

# auto fix
npm run lint -- --fix
```

详细文档可以参考（vue-element-admin）：
[vue-element-admin](http://panjiachen.github.io/vue-element-admin) 是一个后台集成解决方案，它基于 [vue]

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)