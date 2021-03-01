## Mr.J——shop-vue移动端商城

### 项目概要

* 本项目用到的技术栈： vue-cli + vue-router + vuex + axios + vue-axios + vant( UI )

* 如何在本地运行本项目

```js

    git clone ***
    cd shop-vue
    npm i 或 cnpm i      //安装项目依赖 建议使用淘宝镜像源 cnpm 安装 具体参考官网cnpm.taobao.org
    npm run dev   //运行项目服务  在浏览器：localhost:8080/   查看

```

* 如果运行不成功请查看是否缺少配置文件 比如.babelrc或者尝试用vue-cli初始化一个vue项目再将本项目移植进去

* 真机体验可能会带来不流畅卡顿等现象 建议使用Chrome浏览器体验

* 本项目用到的素材图片均来自唯品会网，仅学习使用，如果有问题请联系我删除 ^_^

### 项目文档说明

#### 项目结构

``` sh
├── build/ # 项目打包配置文件 vue-cli 初始化的文件
├── node_modules/ #模块文件
├── config/ #配置文件 vue-cli 初始化的配置
├── dist/  #打包后的文件存放目录
├── src/ #项目入口目录
    ├── assets/   #前端资源目录
        ├── css/ # 样式表目录/less文件存放目录
    ├── components/   # vue组件目录/.vue文件存放目录
        ├── about.vue  # 项目介绍组件
        ├── active.vue # 活动版块组件
        ├── buyInfo.vue  # 购买信息组件
        ├── community.vue  # 社区组件
        ├── goodsInfo.vue # 商品信息组件
        ├── home.vue  # 首页组件
        ├── login.vue # 登录注册组件
        ├── me.vue  # 用户组件
        ├── news.vue  # 社区文章信息组件
        ├── orderList.vue  # 订单列表组件
        ├── orderPay.vue  # 订单支付组件
        ├── search.vue  # 搜索版块组件
        ├── shoppingCart.vue  # 购物车组件
        ├── swiper.vue  # 轮播公用组件
    ├── router/  # vue路由管理目录 
        ├── index.js # 路由主文件
    ├── store/ # vuex状态管理目录
        ├── Core_store/  # store对象目录
           ├── active.js  # 活动页的状态管理
           ├── community.js # 社区的状态管理
           ├── home.js  # 主页状态管理
        ├── index.js # 状态管理入口主文件
    ├── App.vue # 项目根组件
    ├── main.js # 项目入口文件

├── static/ #静态文件存放目录
    ├── images/   # 图片资源
    ├── data.json   # mock数据 
├── test/ #测试目录
├── package.json #包文件信息
├── .babelrc
├── .editorconfig
├── .eslintignore
├── .eslintrc.js
├── .gitignore
├── .postcsssrc.js
├── index.html
├── README.md
├── vue-shop.apk
  

```

#### 功能简单介绍

##### main.js 项目入口文件

* 在主文件中，把所需要的模块加进来，vant的框架因为第一次用，所以也不知道具体加啥组件，所以索性都编译进去了~  这也导致了编译的速度有点稍慢

* 状态方面也对它做了简单的封装  /store/

```js
//导入所需模块
import Vue from 'vue'
import App from './App'
import router from './router'
Vue.config.productionTip = false

//axios
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.use(VueAxios, axios)

//状态管理
import vuex from 'vuex'
Vue.use(vuex);

//ui 框架
import Vant from 'vant';
import 'vant/lib/vant-css/index.css';

Vue.use(Vant);

//懒加载
import { Lazyload } from 'vant';
Vue.use(Lazyload);

//瀑布流
import { Waterfall } from 'vant';
Vue.use(Waterfall);

import store from './store/index'

/* VUE实例 */
new Vue({
  el: '#app',
  router,
  store,
  components: { App },
  template: ' '
})

```

#### 路由管理

* 在这里把需要跳转的组件都加进来，配合vue-router使用，因为业务逻辑不是很复杂，所以这里没有用子路由跳转,都是简单的路由处理

* 在js中控制路由跳转：
```js
this.$router.push(url);
```


```js
import Vue from 'vue'
import Router from 'vue-router'
import Home from '@/components/home'
import Search from '@/components/search'
import  GoodsInfo from '@/components/goodsInfo'
import Buy from '@/components/buyInfo'
import Pay from '@/components/orderPay'
import Community from '@/components/community'
import ShopingCart from '@/components/shoppingCart'
import Me from '@/components/me'
import Login from '@/components/login'
import About from '@/components/about'

Vue.use(Router)

export default new Router({
  routes: [
    {
      path: '/',
      name: 'Home',
      component: Home,
    },
    {
      path: '/search',
      name: 'search',
      component: Search,
    },
    {
      path:'/goods/:id',
        name:'goodsInfo',
        component:GoodsInfo,
    },
    {
      path:'/goods/:id/buy',
      name:'buyInfo',
      component:Buy,
    },
    {
      path:'/goods/:id/buy/pay',
      name:'pay',
      component:Pay,
    },
    {
      path:'/community',
      name:'community',
      component:Community,
    },
    {
      path:'/shoppingCart',
      name:'shoppingCart',
      component:ShopingCart,
    },
    {
      path:'/me',
      name:'Me',
      component:Me,
    },
    {
      path:'/login',
      name:'login',
      component:Login,
    },
    {
      path:'/register',
      name:'register',
      component:Login,
    },
    {
      path:'/about',
      name:'aboutMe',
      component:About,
    },
    {
      path:'*',
      redirect:'/'
    }
  ]
})

```


### 总结

* 这是我学vue做的第一个综合性的项目，整个过程耗时差不多20天左右吧,由于平时还有工作要做,都是挤着周末做的o(╥﹏╥)o以后继续完善这个项目

* 在做的过程中遇到了很多问题，所以收获了不少经验，再接再厉 ^_^

* 一句话总结自己： 继续踩坑

#### 始终坚信

敢于尝试的你 其实已经进步了 ^_^


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)