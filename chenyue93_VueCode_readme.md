[Vue CLI 命令行工具简介](https://cli.vuejs.org/zh/guide/creating-a-project.html#%E4%BD%BF%E7%94%A8%E5%9B%BE%E5%BD%A2%E5%8C%96%E7%95%8C%E9%9D%A2)

[Vue官方文档](https://cn.vuejs.org/v2/guide/syntax.html)

- 1.安装下查看vue2.x和vue3.x安装要求

  - node版本必须大于等于8.9(使用 node -v查看)
  - vue-cli3.x: npm  / cnpm install -g @vue/cli	//cnpm是npm的淘宝镜像
  - vue-cli2.x: npm/cnpm install -g @vue/cli-init

- 2.创建项目

  - vue init webpack my-project

    > 提示目录已存在，是否继续：Y
    > Project name（工程名）:回车
    > Project description（工程介绍）：回车
    > Author：作者名
    > Vue build（是否安装编译器）:回车
    > Install vue-router（是否安装Vue路由）：回车
    > Use ESLint to lint your code（是否使用ESLint检查代码，我们使用idea即可）：n
    > Set up unit tests（安装测试工具）：n
    > Setup e2e tests with Nightwatch（也是测试相关）：n
    > Should we run `npm install` for you after the project has been created? (recommended)：选择：No, I will handle that myself

    ![1.vue2.x创建项目](images/1.vue2.x创建项目.PNG)

    - 安装依赖的时候,选择最后一个,就是自己安装

- 3.启动项目

  - cd my-project		//跳到自己项目
  - npm install //安装项目
  - npm start	/	npm run dev	//启动项目

- 4.工程目录

  ![2.vue工程目录](images/2.vue工程目录.PNG)

  ```
  build: webpack配置文件
  config:  针对开发时服务器的配置
  src: 代码源文件(我们只关心写代码的src目录)
  src/assets: css,image等
  src/components: 其他子组件
  src/App.vue: 最顶层的主组件
  src/main.js: 入口文件
  static： 静态文件
  .babelrc: es6的解析文件和vue解析依赖文件(es6特性浏览器还没有全部支持，babel用来将es6代码转换成浏览器能够识别的代码,babel是下一代JavaScript 语法的编译器)
  .editorconfig: 配置文件
  .postcssrc.js:  css的配置文件
  index.html:  项目根视图
  package.json: 配置,比如 启动命令
    "scripts": {
      "dev": "webpack-dev-server --inline --progress --config build/webpack.dev.conf.js",
      "start": "npm run dev",
      "lint": "eslint --ext .js,.vue src",
      "build": "node build/build.js"
    },
  ```
  [babel之配置文件.babelrc入门详解](https://www.jb51.net/article/135225.htm)

  > ├── App.vue                      // APP入口文件
  > ├── api                          // 接口调用工具文件夹
  > │   └── index.js                 // 接口调用工具
  > ├── components                   // 组件文件夹
  > ├── frame                        // 子路由文件夹
  > ├── main.js                      // 项目配置文件
  > ├── page                         // 页面组件文件夹
  > ├── router                       // 路由配置文件夹
  > │   └── index.js                 // 路由配置文件
  > ├── style                        // scss 样式存放目录
  > │   ├── base                     // 基础样式存放目录
  > │   │   ├── _base.scss           // 基础样式文件
  > │   │   ├── _color.scss          // 项目颜色配置变量文件
  > │   │   ├── _mixin.scss          // scss 混入文件
  > │   │   └── _reset.scss          // 浏览器初始化文件
  > │   ├── scss                     // 页面样式文件夹
  > │   └── style.scss               // 主样式文件
  > └── utils                        // 常用工具文件夹
  >   └── index.js                // 常用工具文件



  - 模板语法

    vue中由三个标签构成

     
     
     

    1. 插值

       数据绑定最常见的形式就是使用“Mustache”语法 (双大括号) 的文本插值：

       {{ 变量 }} 其中只能是单行语句

       变量可以是data中的数据,可以直接使用,{{msg}}页面返回hello world

       ```vue
       data(){
       	return {	
       		msg: "hello world!"
       	}
       }
       ```

    2. 指令(Directives): 只能使用在标签中,可以当做标签属性

       指令 (Directives) 是带有 `v-` 前缀的特殊特性。指令特性的值预期是**单个 JavaScript 表达式**

       v-once:	只渲染一次,数据变了,标签的值不会变

       v-html:	解析html结构,后面不需要使用{{  }}直接v-html="msg"

       v-bind:	Mustache 语法不能作用在 HTML 特性上,如果要使用msg值,要使用v-bind:,可以简写为:

       ```vue
         
         
       ```

       - 条件渲染(判断)

         v-if

         v-else-if

         v-else

         key

         v-show

         ## [`v-if` vs `v-show`](https://cn.vuejs.org/v2/guide/conditional.html#v-if-vs-v-show)

         `v-if` 是“真正”的条件渲染，因为它会确保在切换过程中条件块内的事件监听器和子组件适当地被销毁和重建。

         `v-if` 也是**惰性的**：如果在初始渲染时条件为假，则什么也不做——直到条件第一次变为真时，才会开始渲染条件块。

         相比之下，`v-show` 就简单得多——不管初始条件是什么，元素总是会被渲染，并且只是简单地基于 CSS 进行切换。

         一般来说，`v-if` 有更高的切换开销，而 `v-show` 有更高的初始渲染开销。因此，如果需要非常频繁地切换，则使用 `v-show` 较好；如果在运行时条件很少改变，则使用 `v-if` 较好。

       - 列表渲染

         v-for

       - 事件

         v-on:click="handleClick("哈哈",$event)"或者@click="handleClick()"

         在data平级下创建

         ```
         methods:{
            handleClick (data,event) {
               // this指向当前组件
               // this来索引当前data中的数据
               console.log(this);
               console.log(data);
                console.log(event);
               this.show = !this.show;
            },
            addHandler(){
                
            }
         }
         ```

         ​	

- ## 拉取 2.x 模板 (旧版本)

  Vue CLI >= 3 和旧版使用了相同的 `vue` 命令，所以 Vue CLI 2 (`vue-cli`) 被覆盖了。如果你仍然需要使用旧版本的 `vue init` 功能，你可以全局安装一个桥接工具：

  ```bash
  npm install -g @vue/cli-init
  # `vue init` 的运行效果将会跟 `vue-cli@2.x` 相同
  vue init webpack my-project
  ```









































#项目初始化

    1.安装vue-cli
    
        npm install -g vue-cli
        
    2.初始化项目
    
        vue init webpack my-project
        
    3.进入项目
    
        cd my-project
        
    4.安装依赖
    
        npm install
        
    5.启动项目
    
        npm run dev

#项目目录结构

    index.html:  项目根试图
    .postcssrc.js:  postcssrc配置文件
    static： 静态文件
    config:  针对开发时服务器的配置
    src: 代码源文件
    src/main.js: 入口文件
    src/App.vue: 最顶层的组件
    src/components: 其他子组件
    src/assets: css,image等
# VUE基础
Vue组件：
    
        包含三个部分：
        
            Template：视图部分
            template中只有一个根元素,只有一个  ,只有一个同级的元素
            script: 逻辑部分
            	//创建Vue实例
                new Vue({
                  el: '#app',		//element 元素挂载到id为app的div上
                  components: { App },  //加载组件
                  template: ' ',   //加载模板,引入App然后当成组件使用 import App from './App'
                  store,
                  router
                })
            
               样式只在当前组件生效
            style: 样式部分


Mustache: 模板
    

        表现形式： {{语法}}
        
        {{ hello }}
        
         {{1 + 1}} 
        
         {{'xsdsffr'}} 
        
         {{0  -->
        
        {{'注意：只能存在单行语句'}}

## VUE 基本指令

        v-html: 渲染文本,可以解析html语法
        
        v-text: 渲染文本,html就是字符串
        
        v-bind: 绑定
        
        v-if: 条件指令
        
        v-else:
        
        v-show: display:block/none
        
            v-if 是“真正”的条件渲染，因为它会确保在切换过程中条件块内的事件监听器和子组件适当地被销毁和重建。
    
            v-if 也是惰性的：如果在初始渲染时条件为假，则什么也不做——直到条件第一次变为真时，才会开始渲染条件块。
    
            相比之下，v-show 就简单得多——不管初始条件是什么，元素总是会被渲染，并且只是简单地基于 CSS 进行切换。
    
            一般来说，v-if 有更高的切换开销，而 v-show 有更高的初始渲染开销。因此，如果需要非常频繁地切换，则使用 v-show 较好；如果在运行时条件很少改变，则使用 v-if 较好。

#### 列表渲染：
            v-for: 数组(for...in...)遍历
            每个列表都需要添加key

 #### 事件监听:
            v-on:
            methods:
            事件参数
            修饰符
            	为了解决这个问题，Vue.js 为 v-on 提供了事件修饰符。
            	之前提过，修饰符是由点开头的指令后缀来表示的。
                .stop
                .prevent
                .capture
                .self
                .once
                .passive


            简写方法：@click 代替 v-on:
        数组更新检测：
            变异方法（改变了原数组）：引起视图更新
            替换数组（创建新数组）：不会引起视图更新
       显示
#### 计算属性: computed
            computed和method的区别
            计算属性是基于它们的依赖进行缓存的。只在相关依赖发生改变时它们才会重新求值。这就意味着只要 message 还没有发生改变，多次访问 reversedMessage 计算属性会立即返回之前的计算结果，而不必再次执行函数


#### 表单输入绑定
            v-model双向数据绑定
            修饰符：lazy,trim,number
            watch: 实时监听数据变化,写在 和data齐平
    
             {{msg}} 
              // watch: {
      //   msg: function (data) {
      //     if (data === 'hello') {
      //       console.log('输入了你好')
      //     }
      //   }
      // }

## 组件之间通信 

​       ![3.组件组合](images/3.组件组合.PNG)


        父 -> 子：props  支撑
        每个 prop 都有指定的值类型。这时，你可以以对象形式列出 prop，这些属性的名称和值分别是 prop 各自的名称和类型：
           props: {
              title: String,
              likes: Number,
              isPublished: Boolean,
              commentIds: Array,
              author: Object,
              callback: Function,
              contactsPromise: Promise // or any other constructor
            }
            数据传递类型限制
          props: {
              title: [String,Number],//父模块传递title类型是String或者Number
              lifemsg: {
                  type: String,
                  required: true	//添加必选项
              },
              num: {
                  type: Number,
                  default: 1		//没值的时候,默认值
              },
              obj: {
                  type: Object,
                  default: () => {  //es6语法
                      return {
                          name: 'lily',
                          age: 21
                      }
                  }
              }
       	 }
        子 -> 父：emit  发出

#### 父组件

```vue
 
   
    父组件 
     
     接受子组件传递的数据：
       {{info}} 
     
   
 

 
  import Child from './Child'

  export default {
    name: "parent",
    data() {
      return {
        info: "hih",
        num:0
      }
    },
    components: {
      Child
    },
    computed:{
      convertNumber(){
        return this.num - 0
      }
    },
    methods: {
      getMsg(data) {
        this.info = data
      }
    }
  }
 

 
 
```

#### 子组件

```vue
 
   
    子组件
     传递 
     子组件获取父组件数据
       {{num}} 
     
   
 

 
    export default {
      name: "child",
      data(){
        return{
          msg:"我是子组件数据"
        }
      },
      props:{
        num:{
          type:Number,
          default:-1
        }
      },
      methods:{
        sendMsg(event){
          // 两个参数：1：key,名字自己取，会在父组件中获取对应名字的数据, 2:数据
          this.$emit('sendmsg', this.msg)
        }
      }
    }
 

 
 

```



#### 插槽
        单个插槽
        具名插槽: ` ` 元素有一个特殊的特性：`name`。这个特性可以用来定义额外的插槽
        作用域插槽：数据是子传父 `slot-scope` 

 #### 动态组件：keep-alive
        主要用于保留组件状态或避免重新渲染
        不会在函数式组件中正常工作，因为它们没有缓存实例
        include 和 exclude 属性允许组件有条件地缓存

## 过渡和动画(css)

- 在 CSS 过渡和动画中自动应用 class

- 可以配合使用第三方 CSS 动画库，如 Animate.css

        在css过渡和动画中自动应用class
            过渡类名：
                v-enter：定义进入过渡的开始状态。在元素被插入之前生效，在元素被插入之后的下一帧移除。


                v-enter-active：定义进入过渡生效时的状态。在整个进入过渡的阶段中应用，在元素被插入之前生效，在过渡/动画完成之后移除。这个类可以被用来定义进入过渡的过程时间，延迟和曲线函数。
        
                v-enter-to: 2.1.8版及以上 定义进入过渡的结束状态。在元素被插入之后下一帧生效 (与此同时 v-enter 被移除)，在过渡/动画完成之后移除。
        
                v-leave: 定义离开过渡的开始状态。在离开过渡被触发时立刻生效，下一帧被移除。
        
                v-leave-active：定义离开过渡生效时的状态。在整个离开过渡的阶段中应用，在离开过渡被触发时立刻生效，在过渡/动画完成之后移除。这个类可以被用来定义离开过渡的过程时间，延迟和曲线函数。
        
                v-leave-to: 2.1.8版及以上 定义离开过渡的结束状态。在离开过渡被触发之后下一帧生效 (与此同时 v-leave 被删除)，在过渡/动画完成之后移除。
        可以配合使用第三方 CSS 动画库，如 Animate.css

#### 自定义指令(directive)
    1. 全局指令
    注册一个全局自定义指令 `v-focus`
        // Vue.directive('focus', {
        //   // 当被绑定的元素插入到 DOM 中时……
        //   inserted: function (el) {
        //     // 聚焦元素
        //     el.focus()
        //   }
        // })
    2.  局部指令和data平级
        directives: {
            focus: {
            // 指令的定义
            inserted: function (el) {
                el.focus()
            }
            },
            mycss: {
            inserted: function (el) {
                el.style.color = 'blue'
            }
            }
        }
#### 过滤器
        过滤器可以用在两个地方：双花括号插值和 v-bind 表达式 (后者从 2.1.0+ 开始支持)。过滤器应该被添加在 JavaScript 表达式的尾部，由“管道”符号指示：
         
        {{ message | capitalize }}
    
         
          
            在一个组件的选项中定义本地的过滤器：
                filters: {
                    capitalize: function (value) {
                        if (!value) return ''
                        value = value.toString()
                        return value.charAt(0).toUpperCase() + value.slice(1)
                    }
                }
## Axios: 

[Axios中文文档](http://www.kancloud.cn/yunye/axios/234845)

[github](https://github.com/axios/axios)

1. 安装

   npm install axios

2. 引入加载

   import Axios from “axios”

   Vue.protptype.$axios = Axios

3. 请求

   #### get请求:

   ```vue
   created(){//和data平级
       this.$axios(“http://www.wwtliu.com/sxtstu/news/juhenews.php”,{//默认get请求
           params:{
               type:"junshi",
               count:30	
           }
       }).then(res => {//请求成功
           this.newsData = res.data;
           console.log(res.data);
       }).catch(error => {//请求失败
           console.log(error);
       })
   }
   ```

   #### post请求:

   ```vue
   created(){//和data平级
       this.$axios.post(“http://www.wwtliu.com/sxtstu/blueberrypai/login.php”,
       qs.stringify({
           user_id:"iwen@qq.com",
           password:"iwen123",
           verification_code:"crfvw"
       })).then(res => {//请求成功
           this.newsData = res.data;
           console.log(res.data);
       }).catch(error => {//请求失败
           console.log(error);
       })
   }
   ```


    post请求注意事项：
            axios接受的post请求的参数格式必须为form-data格式
                ① formData格式：?name='aa'&pwd='123'
                我们是x-www-form-urlencoded:	{name:"iwen",age:20}
                可以引入第三方库 qs库全名 querystring,做参数转换
                import qs from "qs"
                qs.stringify({
                    user_id:"iwen@qq.com",
                    password:"iwen123",
                    verification_code:"crfvw"
                })
#### 		全局的 axios 配置:写在main.js中

```js
// The Vue build version to load with the `import` command
// (runtime-only or standalone) has been set in webpack.base.conf with an alias.
import Vue from 'vue'
import App from './App'
import Axios from 'axios'
import qs from 'qs'
import store from './store'
import router from './router'
import VueResource from 'vue-resource'
import VueAwesomeSwiper from 'vue-awesome-swiper'
import 'swiper/dist/css/swiper.css'
Vue.prototype.$axios = Axios
// Vue.prototype.HOST = 'api'

Axios.defaults.baseURL = 'http://www.wwtliu.com'
// Axios.defaults.headers.common['Authorization'] = AUTH_TOKEN
Axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded'
Vue.config.productionTip = false

// 注册一个全局自定义指令 `v-focus`
// Vue.directive('focus', {
//   // 当被绑定的元素插入到 DOM 中时……
//   inserted: function (el) {
//     // 聚焦元素
//     el.focus()
//   }
// })
// 添加请求拦截器  拦截器:在请求或响应被 then 或 catch 处理前拦截它们。
Axios.interceptors.request.use(function (config) {
  // 在发送请求之前做些什么
  // console.log('request', config)
  if (config.method === 'post') {
    config.data = qs.stringify(config.data)
  }
  return config
}, function (error) {
  // 对请求错误做些什么
  return Promise.reject(error)
})

// 添加响应拦截器
Axios.interceptors.response.use(function (response) {
  // 对响应数据做点什么
  // console.log('response', response)
    if(config.method == "post"){
        config.data = qs.stringify(config.data)
    }
  return response
}, function (error) {
  // 对响应错误做点什么
  return Promise.reject(error)
})
Vue.use(VueAwesomeSwiper)
Vue.use(VueResource)
/* eslint-disable no-new */
new Vue({
  el: '#app',
  components: { App },
  template: ' ',
  store,
  router
})

```

在get和post请求中key简化url地址只要写“/sxtstu/blueberrypai/login.php”

            axios.defaults.baseURL = 'https://api.example.com'; // 请求接口基础路径
            axios.defaults.headers.common['Authorization'] = AUTH_TOKEN; // 作者认证
            axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded';  // post 请求时转码
        拦截器：
            在请求或响应被 then 或 catch 处理前拦截它们
        跨域处理：
            config/index.js":
                // 跨域解决方案
                proxyTable: {
                    '/api': {
                        target: 'http://localhost:3000', // 开发
                        changeOrigin: true,
                        pathRewrite: {
                        '^/api': ''
                        }
                    }
                }
            main.js:HOST
                Vue.prototype.HOST = 'api'
    mock: 数据模拟
        方案：
            1.前端静态JSON文件，get请求形式访问数据（只能get请求）
            2.项目中集成服务器，模拟各种接口（多为前后端分离同步开发时采用）
            3.直接使用线上数据（多为重构时采用）
            4.mock.js 

#Vuex
    1.是什么
    
        Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。
        
    2.什么情况下我应该使用 Vuex？
    
        如果您不打算开发大型单页应用，使用 Vuex 可能是繁琐冗余的。确实是如此——如果您的应用够简单，您最好不要使用 Vuex。一个简单的 store 模式就足够您所需了。但是，如果您需要构建一个中大型单页应用，您很可能会考虑如何更好地在组件外部管理状态，Vuex 将会成为自然而然的选择。
        
    3.Vuex状态管理
    
        mutations:
        
            只能同步执行
            
        action:
        
            1.Action 提交的是 mutation，而不是直接变更状态
            
            2.Action 可以包含任意异步操作

#vue-resource

    1.1.0以后已弃用，具体参考Axios



 跨域处理

```vue
   // 跨域处理：注意: 此种跨域解决方案值适用于测试阶段,打包的时候,不会具备服务器
	//不能跨域了,后端解决此问题
      在项目/config/index.js下添加 配置文件修改要重启项目
//需要删除axios默认配置URL
//Axios.defaults.baseURL=""  注释掉
module.exports = {
  dev: {

    // Paths
    assetsSubDirectory: 'static',
    assetsPublicPath: '/',
    // 跨域解决方案  //添加内容
    proxyTable: {
      '/api': {
        target: 'http://localhost:3000', // 开发
        changeOrigin: true,
        pathRewrite: {
          '^/api': ''
        }
      }
    },
        在项目/config/main.js中添加HOST代理
            Vue.prototype.HOST = '/api'
在项目中使用地址时:
	var url = this.HOST +"/login";// 打印url 结果是 /api/login
```

mock: 数据模拟

>   方案：
>         1.前端静态JSON文件，get请求形式访问数据（只能get请求）
>         	优点: 方便,快捷
>         	缺点: 只能存在get请求
>         2.项目中集成服务器，模拟各种接口（多为前后端分离同步开发时采用,用最多）
>         	优点: 模拟真实线上环境
>         	缺点: 增加开发成本
>         3.直接使用线上数据（多为重构时采用）
>         	优点: 真实
>         	缺点: 不一定每个项目都适用
>         4.mock.js (官网http://mockjs.com需要vpn打开或者github上搜索mock.js,或者highsea90.com/t/mock)

# Vue Router

[Vue Router官方文档](https://router.vuejs.org/zh/installation.html)

## 1. 安装

 npm install --save vue-router

## 2. 引用

在项目/main.js下

import VueRouter from "vue-router"

Vue.use(VueRouter )

## 3. 配置路由

```js
//配置路由后路径是localhost:8080/#/,多了#号
//main.js,配置完成后还要再App.vue显示位置配置  
import Vue from 'vue'
import App from './App'
import VueRouter from "vue-router"
import HelloWorld from './components/HelloWorld'
import Login from './components/Login'

Vue.use(VueRouter)

var router = new VueRouter({
	routers: [{
 	       path: "/",
  	      component: HelloWorld	//需要引入import Helloworld模块
	},{
    	    path: "/login",
   	     component: Login	//需要引入import Login模块
	}]
})

new Vue({
	el: "#app",
    template: " ",
    router,//写入刚才创建的VueRouter对象 
    components: {
        App
    }
})
```

## 4. 提取配置文件,不在写在main.js中

1. 创建src/router目录

2. 创建src/router/index.js文件

3. ```js
   //index.js
   import Vue from 'vue'
   import VueRouter from "vue-router"
   import HelloWorld from '../components/HelloWorld'
   import Login from '../components/Login'
   import Hi from '@/components/Hi'//@寻找项目根目录
   Vue.use(VueRouter)
   //导出
   export default new VueRouter({
   	routers: [{
    	       path: "/",
     	      component: HelloWorld	//需要引入import Helloworld模块
   	},{
       	    path: "/login",
      	     component: Login	//需要引入import Login模块
   	},{
       	    path: "/hi",
      	     component: Hi	
   	}]
   })
   ```

4. main.js

   ```js
   //配置路由后路径是localhost:8080/#/,多了#号
   //main.js
   //配置完成后还要再App.vue显示位置配置  ,添加视图加载位置
   import Vue from 'vue'
   import App from './App'
   import router from "./router"//不需要写./router/index,默认加载文件夹中的index.js文件
   Vue.config.productionTip = false
   
   new Vue({
   	el: "#app",
       template: " ",
       router,
       components: {
           App
       }
   })
   ```

## 5. 跳转

> //点击实现代码跳转
>  helloworld 
>  login 
>
> to可以动态变化,在data中统一管理
>
> ```js
> export default {
>   name: 'details',
>   data () {
>     return {
>         urlData:{
>             helloworld:"/",
>             login:"/login"
>         } 
>         ,Url: {
>         '/details/health1': require('../assets/images/health-1.png'),
>         '/details/health2': require('../assets/images/health-2.png'),
>         '/details/health3': require('../assets/images/health-3.png'),
>         '/details/health4': require('../assets/images/health-4.jpg')
>       }
>     }
>   },
> ```

## 6.路由嵌套

1. ```js
   export default new VueRouter({
   	routers: [{
    	       path: "/course",
           name:'course',
     	      component: Course,	//课程
           //默认进来重定向路径,没有点击时子子路由区域显示的内容
           redirect:'/course/java',
           children:[{
              path: "java",//这里填写vue组件的name名称
               name:'java',
     	      	component: Java	
           },{
              path: "web",//这里填写vue组件的name名称
               name:'web',
     	      	component: Web	
           }]
   	},{
       	    path: "/login",
           name:'login',
      	     component: Login	//需要引入import Login模块
   	},{
       	    path: "/hi",
           name:'hi',
      	     component: Hi	
   	}]
   })
   ```

2. 给定显示路由的位置 

   几级路由就有几个router-view,子组件属于谁,就在其下添加router-view

## 7. 路由传递参数

​	1. 路由要添加name

```js
export default new VueRouter({
	routers: [{
    	path: "/hi/:say/:type",//:type是对象
    	name:'hi',
   		component: Hi	
	}]
})
```

​	2. 传递参数:

在路由使用的地方

//to中的name就是路由的name

​	//params:{say:'你好'}是将参数添加到url后/

​	//localhost:8080/#/hi/say='你好'

 

打招呼 

或者

 

打招呼 

data(){
	return{
        obj:{
            name="张三",
            age=25
        }
	}
}

​	3. 接受参数:

//param接受

 
    打招呼:{{$route.params.say}}--{{$route.params.type.name}}
 
## 8.路由点击高亮

全局显示

 
    .router-link-active{
        color:red;//点击会显示红色
    }
 

或者

在路由中配置class, 中使用.active配置

```js
//history.back()/,只向后跳一级,不会记录多次操作
export default new VueRouter({
    mode:"history",//路由记录操作位置,点击后退可以回到前一个路由
    //class="router-link-exact-active active"
    linkActiveClass:"active",
	routers: [{
 	       path: "/course",
        name:'course',
  	      component: Course,	//课程
        //默认进来重定向路径,没有点击时子子路由区域显示的内容
        redirect:'/course/java',
        children:[{
           path: "java",//这里填写vue组件的name名称
            name:'java',
  	      	component: Java	
        },{
           path: "web",//这里填写vue组件的name名称
            name:'web',
  	      	component: Web	
        }]
	}]
})
```

 
    .active{
        color:red;//点击会显示红色
    }
 

# 组件库Element

[Element](element.eleme.io/#/zh-CN/component.carousel):元素样式

看快手上手,改变项目配置文件

1. 安装element-ui

   npm i element-ui -S     //i 是install的简写 -S 是save的简写

2. 安装需要加载的依赖

   npm install babel-plugin-component -D

3. 修改.babelrc文件

   ```text
   {
     "presets": [["es2015", { "modules": false }]],
     "plugins": [
       [
         "component",
         {
           "libraryName": "element-ui",
           "styleLibraryName": "theme-chalk"
         }
       ]
     ]
   }
   ```

4. 进入组件

   ```text
   import { Button, Select } from 'element-ui';
   Vue.use(Button);
   ```

   

## [swiper](github.com/surmon-china/vue-awesome-swiper)



## [lazyload](github.com/hilongjw/vue-lazyload)

[REM与Less]()

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)