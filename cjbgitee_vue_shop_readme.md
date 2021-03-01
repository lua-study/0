# vue_shop

## Project Manage UI
```
npm install -g @vue/cli
npm install -g cnpm --registry=http://registry.npm.taobao.org
vue ui
```
## Init Project
- 设置详情 - 项目位置 项目名称 git提交内容
- 设置预设 - 手动配置
- 设置功能 - Babel Router Linter/Formatter 使用配置文件
- 设置配置 - ESLint+Standard config,Lint on save
- 安装插件 - vue-cli-plugin-element
- 运行依赖 - axios vue-table-with-tree-grid
- 开发依赖 - less-loader less

## git版本控制
```
git config --global user.name
git config --global user.email
git status
将文件添加到缓存区
git add .
git commit -m '提交的信息'
git remote add origin https://gitee.com/cjbgitee/vue_shop.git
首次推送
git push -u origin master

创建分支
git checkout -b login
git branch
git commit -m '提交的信息'
git push -u origin login

合并分支
git checkout master
git merge login
git push
```
## 登陆退出
- 渲染Login布局：图标 输入框 按钮 iconfont
- 数据绑定 表单数据预验证 重置 登陆预验证
- axios发送登陆请求并弹框提示
- 路由导航守卫控制页面访问
- 实现退出功能

















 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)