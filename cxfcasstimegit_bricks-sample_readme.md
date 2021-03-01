# bricks-sample

[bricks组件库](https://gitee.com/cassfrontend/bricks)示例项目

![](https://images.gitee.com/uploads/images/2018/0809/134349_6afa86cd_386700.png "屏幕截图.png")

## 特性

- 集成[TypeScript](http://www.typescriptlang.org/)
- 集成[sass](http://sass-lang.com/)
- 集成[mobx](https://mobxjs.github.io/),[中文版](https://cn.mobx.js.org/)
- 集成[react-router](https://github.com/ReactTraining/react-router/tree/master/packages/react-router-dom),[react-router-config](https://github.com/ReactTraining/react-router/tree/master/packages/react-router-config)
- 集成[bricks](https://gitee.com/cassfrontend/bricks)
- 集成[autoprfix](https://github.com/postcss/autoprefixer)
- 集成lint-staged
- 支持页面按需加载

## 运行

```bash
# 使用taobao镜像加速
npm install nrm -g
nrm use taobao

git clone https://gitee.com/cassfrontend/bricks-sample.git project-name
cd project-name

rm -rf .git

npm install
npm start
```

## 构建

执行构建前,会加载`config/${NODE_ENV}.js`中的配置文件,
可以根据部署环境修改配置文件，如publicPath

```bash
npm run build-test
npm run build-demo
npm run build-prod
```

## 目录结构

```bash
.
├── config                    # 配置文件，可以根据不同环境配置不同的参数
│   ├── base.js
│   ├── demo.js
│   ├── development.js
│   ├── index.js
│   ├── production.js
│   └── test.js
├── src						            # 源文件
│   ├── components	        	# 应用通用组件
│   │   ├── Loading.tsx
│   │   ├── MenuItem.tsx
│   │   ├── Menu.tsx
│   │   ├── Navbar.tsx
│   │   ├── Page.tsx
│   │   └── Sidebar.tsx
│   ├── config					      # 应用配置
│   │   ├── routes.ts   			# 应用路由配置
│   │   └── stores.ts   			# 跨页面通用的Mobx store配置
│   ├── layouts			    		  # 页面布局，应用中可以有不同的布局方式
│   │   ├── DefaultLayout.tsx
│   │   └── NoSidebarLayout.tsx
│   ├── pages					        # 页面，子目录切分各个页面
│   │   ├── home-page			
│   │   │   ├── components		# 页面组件
│   │   │   │   └── Main.tsx
│   │   │   ├── stores			  # 当前页面用到的store
│   │   │   │   ├── HomePageStore.ts
│   │   │   │   └── index.ts
│   │   │   ├── styles			  # 当前页面的样式
│   │   │   │   └── index.scss
│   │   │   └── index.tsx		  # 页面入口
│   │   ├── test2-page
│   │   │   └── index.tsx
│   │   └── test-page
│   │       └── index.tsx
│   ├── styles					      # 应用通用样式
│   │   ├── _app.scss
│   │   ├── index.scss
│   │   ├── _menu.scss
│   │   ├── _navbar.scss
│   │   ├── _sidebar.scss
│   │   └── _variables.scss
│   ├── types					        # 第三方类型声明
│   │   └── react-router-config
│   │       └── index.d.ts
│   ├── utils					        # 通用工具目录
│   │   └── index.ts
│   └── index.tsx				      # 应用入口
├── .babelrc
├── .browserslistrc				    # 支持的浏览器列表
├── .editorconfig
├── .eslintrc.js
├── .gitignore
├── index.html
├── package.json
├── postcss.config.js			    # postcss配置，自动增加-webkit-前缀
├── README.md
├── tsconfig.json
├── tslint.json
└── webpack.config.js			    # webpack打包配置
```

## 建议

- 尽量按页面分割功能，页面内的样式、组件、store放在对应的文件夹内，尽量不影响其他页面
- 页面内的样式推荐使用[BEM命名规范](http://getbem.com/)，同时为每个页面的class增加前缀
- 一旦某个页面的组件变得通用，往上移动到 src/components中

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)