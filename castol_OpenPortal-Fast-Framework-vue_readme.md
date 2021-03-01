## OpenPortal-Fast-Framework-vue
- OpenPortal-Fast-Framework-vue基于vue、element-ui构建开发，实现后台管理前端功能，提供一套更优的前端解决方案
- 前后端分离，通过token进行数据交互，可独立部署
- 主题定制，通过scss变量统一一站式定制
- 动态菜单，通过菜单管理统一管理访问路由
- 数据切换，通过mock配置对接口数据／mock模拟数据进行切换
- 发布时，可动态配置CDN静态资源／切换新旧版本
 

**如何交流、反馈、参与贡献？**
- [官方网站](http://www.openportal.com.cn)：http://www.openportal.com.cn
- 官方QQ群：579395648
 

# 介绍

基于vue、element-ui构建开发，提供一套更优的前端解决方案。

# 功能

```
- 登录/退出 (接口数据交互)
- 管理员列表 (接口数据交互)
- 角色管理 (接口数据交互)
- 菜单管理 (接口数据交互)
- SQL监控 (接口数据交互)
- 定时任务 (接口数据交互)
- 参数管理 (接口数据交互)
- 文件上传 (接口数据交互)
- 系统日志 (接口数据交互)
- 前后端分离，通过token进行数据交互，可独立部署
- 主题定制，通过scss变量统一一站式定制
- 动态菜单，通过菜单管理统一管理访问路由
- 数据切换，通过mock配置对接口数据／mock模拟数据进行切换
- 发布时，可动态配置CDN静态资源／切换新旧版本
- 更多，持续迭代中...
```

# 技术栈

你需要在本地安装 nodejs，提前了解和学习这些知识会对使用本项目有很大的帮助。

- [nodejs](http://nodejs.org/)
- [ES6](http://es6.ruanyifeng.com/)
- [vue-cli](https://github.com/vuejs/vue-cli)
- [vue](https://cn.vuejs.org/index.html)
- [vue-router](https://github.com/vuejs/vue-router)
- [vuex](https://github.com/vuejs/vuex)
- [axios](https://github.com/axios/axios)
- [vue-cookie](https://github.com/alfhen/vue-cookie)
- [element-ui](https://github.com/ElemeFE/element)
- [iconfont](http://www.iconfont.cn/)

# 目录结构

本项目已经通过vue-cli脚手架为你生产完整的开发框架（有根据业务需求做调整修改），下面是整个项目的目录结构。

```
├── dist                       // 构建打包生成部署文件
│   ├── 2001010101             // 静态资源（20年01月01日01时01分）
│   ├── config                 // 配置
│   ├── index.html             // index.html入口
├── build                      // 构建相关
├── config                     // 构建配置相关
├── src                        // 源代码
│   ├── assets                 // 静态资源
│   ├── components             // 全局公用组件
│   ├── element-ui             // element-ui组件配置
│   ├── element-ui-theme       // element-ui组件主题配置
│   ├── icons                  // 所有 svg icons
│   ├── mock                   // mock 模拟数据
│   ├── router                 // 路由
│   ├── store                  // 全局 store管理
│   ├── utils                  // 全局公用方法
│   ├── views                  // view
│   ├── App.vue                // 入口组件
│   ├── main.js                // 入口
├── static                     // 第三方不打包资源
│   ├── config                 // 全局变量配置
│   ├── plugins                // 插件
├── .babelrc                   // babel-loader 配置
├── eslintrc.js                // eslint 配置项
├── .gitignore                 // git 忽略项
├── favicon.ico                // favicon图标
├── index.html                 // html模板
└── package.json               // package.json
```

# 安装

安装过程中，可能会出现安装过慢、报错等情况，请尝试以下2种方式：

```
# 安装依赖
# 1
npm install -g cnpm --registry=https://registry.npm.taobao.org
# 2
cnpm install
# 启动服务
npm run dev
```


# 布局 & 主题

整体布局包括：

- 头部导航条 main-navbar
- 左侧边栏 main-sidebar
- 中间内容展示 main-content

> 对应代码在 src/views/main.vue

`项目`中除去`404`、`login`页面，其它页面都是基于这个布局的。这里我将

- 无需嵌套上左右整体布局的路由称为“全局路由”放在`globalRoutes`常量中，
- 需嵌套上左右整体布局的路由称为“主入口路由”放在`mainRoutes`常量的`children`属性中。

> 对应代码在 src/router/index.js

```
// 全局路由(无需嵌套上左右整体布局)
const globalRoutes = [
  { path: '/404', component: _import('common/404'), name: '404', meta: { title: '404未找到' } },
  { path: '/login', component: _import('common/login'), name: 'login', meta: { title: '登录' } }
]

// 主入口路由(需嵌套上左右整体布局)
const mainRoutes = {
  path: '/',
  component: _import('main'),
  name: 'main',
  redirect: { name: 'home' },
  meta: { title: '主入口整体布局' },
  children: [
    // 通过meta对象设置路由展示方式
    // 1. isTab: 是否通过tab展示内容, true: 是, false: 否
    // 2. iframeUrl: 是否通过iframe嵌套展示内容, '以http[s]://开头': 是, '': 否
    { path: '/home', component: _import('common/home'), name: 'home', meta: { title: '首页' } },
    { path: '/theme', component: _import('common/theme'), name: 'theme', meta: { title: '主题' } },
    {
      path: '/demo-01',
      component: null, // 如需要通过iframe嵌套展示内容, 但不通过tab打开, 请自行创建组件使用iframe处理!
      name: 'demo-01',
      meta: {
        title: '我是一个通过iframe嵌套展示内容, 并通过tab打开 demo',
        isTab: true,
        iframeUrl: 'http://ffw.openportal.com.cn/'
      }
    }
  ],
  beforeEnter (to, from, next) {
    let token = Vue.cookie.get('token')
    if (!token || !/\S/.test(token)) {
      next({ name: 'login' })
    }
    next()
  }
}

const router = new Router({
  mode: 'hash',
  scrollBehavior: () => ({ y: 0 }),
  isAddDynamicMenuRoutes: false, // 是否已经添加动态(菜单)路由
  routes: globalRoutes.concat(mainRoutes)
})
```

同时，主入口路由提供meta对象2个属性设置路由展示方式。

`isTab`: 是否通过tab展示内容

`iframeUrl`: 是否通过iframe嵌套展示内容

> 如需要通过iframe嵌套展示内容, 但不通过tab打开, 请自行创建组件使用iframe处理!

# 菜单路由

之前版本的菜单路由都需要手动在`router/index.js`文件中添加，这次新版本提供通过菜单管理统一管理访问路由，自动映射对应文件目录组件

# 主题定制

提供12套颜色主题，进行element-ui和整站主题切换。具体切换方法如下：

1. 修改/src/element-ui-theme/index.js文件中`import './element-[#17b3a3]/index.css'`[]中括号中的值，值可以在同文件中`list`属性中取即可。**（注意：这里只是修改element-ui组件主题）**
2. 修改/src/assets/scss/_variables.scss文件中`$--color-primary: [#17b3a3];`[]中括号中的值，值与第一步值同步即可。**（注意：这里只是修改站点主题，不包括element-ui组件主题）**

主题定制具体实现方法是：

1. 先通过element-ui官方提供的[在线主题生成工具](https://elementui.github.io/theme-chalk-preview/#/zh-CN)，进行切换主题色，再下载解压文件（保留`fonts目录中文件和index.css即可`）放置`/src/element-ui-theme/`目录中，使用同目录中的`index.js`进行统一配置管理。
2. 再设置修改站点主题，使整站主题色统一一致。

> 之所以放弃之前直接在项目中通过`scss`一站式设置主题，是因为开发时编译太慢！同时按需求加载组件的css文件并没有比现在的`index.css`文件小多少kb（主要大小还是在js文件上）。考虑到大部分一个站配置一个主题色后，不会频繁修改！

> 网上查阅也有通过打包插件，对`css`添加父级`id or class`进行主题切换的，但是这样就相当于12套皮肤，需要将12个`index.css`进行合并打包发布，那文件岂不是太大了！这样的需求暂不考虑！

**总之主题定制这块，还需要花更多的心思优化改进！大家可以多多给点思路和建议哦 0.0**



# 动态菜单路由

通过菜单管理统一管理访问路由，自动映射对应文件目录[`src/views/modules/...`]组件。功能实现通过拦截路由进行逻辑判断处理。

####       这里需特别注意，在通过左侧边栏菜单管理，操作新增／修改[菜单路由]项，进行自动映射对应文件目录组件时的规则，规则如下：

- 值为`/sys/user`自动映射对应文件目录为`src/views/modules/[sys/user.vue]`文件
- 值项为`/job/schedule`自动映射对应文件目录为`src/views/modules/[job/schedule.vue]`文件
- 值项为`http://ffw.openportal.com.cn/`自动使用iframe访问`http://ffw.openportal.com.cn/`地址，也就是说**只要是以http[s]?://开头时，都通过iframe访问地址**，不再自动映射

#### 如何确定新增／修改菜单路由是否映射成功？

所有的动态菜单路由都会保存在`sessionStorage['dynamicMenuRoutes']`属性中，同时输出在浏览器控制台

```
! 
数据对象
! 
```

1. 先查看`dynamicMenuRoutes`每一项中的`meta: { iframeUrl: '' }`属性，如果`iframeUrl === ''`，那么就会自动映射对应文件目录。如果`iframeUrl !== ''`就会通过iframe访问地址，无需查看第二步。
2. 再查看`dynamicMenuRoutes`每一项中的`component: null`属性，如果`component === null `，那么就是自动映射对应文件目录`失败`。如果`component !== null`自动映射对应文件目录`成功`。

> 对应代码在 src/router/index.js

```
router.beforeEach((to, from, next) => {
  // 添加动态(菜单)路由
  // 1. 已经添加 or 全局路由, 直接访问
  // 2. 获取菜单列表, 添加并保存本地存储
  if (router.options.isAddDynamicMenuRoutes || fnCurrentRouteType(to) === 'global') {
    next()
  } else {
    http({
      url: http.adornUrl('/sys/menu/nav'),
      method: 'get',
      params: http.adornParams()
    }).then(({data}) => {
      if (data && data.code === 0) {
        fnAddDynamicMenuRoutes(data.menuList)
        router.options.isAddDynamicMenuRoutes = true
        sessionStorage.setItem('menuList', JSON.stringify(data.menuList || '[]'))
        sessionStorage.setItem('permissions', JSON.stringify(data.permissions || '[]'))
        next({ ...to, replace: true })
      } else {
        sessionStorage.setItem('menuList', '[]')
        sessionStorage.setItem('permissions', '[]')
        next()
      }
    })
  }
})

/**
 * 判断当前路由类型, global: 全局路由, main: 主入口路由
 * @param {*} route 当前路由
 */
function fnCurrentRouteType (route) {
  var temp = []
  for (var i = 0; i  = 1) {
      temp = temp.concat(globalRoutes[i].children)
    }
  }
  return temp.length >= 1 ? fnCurrentRouteType(route, temp) : 'main'
}

/**
 * 添加动态(菜单)路由
 * @param {*} menuList 菜单列表
 * @param {*} routes 递归创建的动态(菜单)路由
 */
function fnAddDynamicMenuRoutes (menuList = [], routes = []) {
  var temp = []
  for (var i = 0; i  = 1) {
      temp = temp.concat(menuList[i].list)
    } else if (/\S/.test(menuList[i].url)) {
      var route = {
        path: menuList[i].url.replace('/', '-'),
        component: null,
        name: menuList[i].url.replace('/', '-'),
        meta: {
          menuId: menuList[i].menuId,
          title: menuList[i].name,
          isDynamic: true,
          isTab: true,
          iframeUrl: ''
        }
      }
      // url以http[s]://开头, 通过iframe展示
      if (isURL(menuList[i].url)) {
        route['path'] = `i-${menuList[i].menuId}`
        route['name'] = `i-${menuList[i].menuId}`
        route['meta']['iframeUrl'] = menuList[i].url
      } else {
        try {
          route['component'] = _import(`modules/${menuList[i].url}`) || null
        } catch (e) {}
      }
      routes.push(route)
    }
  }
  if (temp.length >= 1) {
    fnAddDynamicMenuRoutes(temp, routes)
  } else {
    mainRoutes.name = 'main-dynamic'
    mainRoutes.children = routes
    router.addRoutes([
      mainRoutes,
      { path: '*', redirect: { name: '404' } }
    ])
    sessionStorage.setItem('dynamicMenuRoutes', JSON.stringify(mainRoutes.children || '[]'))
    console.log('\n%c! ', 'color:blue')
    console.log(mainRoutes.children)
    console.log('%c! \n\n', 'color:blue')
  }
```



# mock/api数据切换

在前后端分离的情况下，往往前后台是并行开发的！两队先讨论商议确定接口名称、请求类型、请求参数、返回数据等后，就可以暂时并行开发了。为了让前端更加灵活的、更快捷的进行业务逻辑开发，这里提供通过mockJs本地接口拦截，返回模拟数据功能。

#### 开启mock本地模拟数据

1. 通过设置/src/mock/index.js文件中`fnCreate(common, [false])`[]中括号中为true／false开启关闭当前模块mock本地模拟数据功能。（默认开启）
2. 通过设置/src/mock/modules/文件下模块`isOpen: [false]`[]中括号中为`true／false`开启关闭当前api接口mock本地模拟数据功能。（默认开启）

> 具体模拟数据请参考：[mockJs](https://github.com/nuysoft/Mock)



# 打包 & 发布

构建生成的资源文件保存在`/dist`目录下，可通过`config/index.js`目录文件修改相关配置信息

```
# 构建生产环境(默认)
npm run build

# 构建测试环境
npm run build --qa

# 构建验收环境
npm run build --uat

# 构建生产环境
npm run build --prod
```



# 常见问题

### 开发时，如何连接后台项目api接口？

修改`/static/config/index.js`目录文件中` window.SITE_CONFIG['baseUrl'] = '本地api接口请求地址';`



### 开发时，如何解决跨域？

1. 修改`/config/dev.env.js`目录文件中`OPEN_PROXY: true`开启代理
2. 修改`/config/index.js`目录文件中`proxyTable`对象`target: '代理api接口请求地址'`
3. 重启本地服务



### 开发时，如何提前配置CDN静态资源？

修改`/static/config/index-[qa/uat/prod].js`目录文件中`window.SITE_CONFIG['domain'] = '静态资源cdn地址';`



### 构建生成后，发布需要上传哪些文件？

```
/dist`目录下：`2001010101（静态资源，20年01月01日01时01分）、config（配置文件）、index.html
```



### 构建生成后，如何动态配置CDN静态资源？

修改`/dist/config/index.js`目录文件中`window.SITE_CONFIG['domain'] = '静态资源cdn地址';`



### 构建生成后，如何动态切换新旧版本？

修改`/dist/config/index.js`目录文件中` window.SITE_CONFIG['version'] = '旧版本号';`


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)