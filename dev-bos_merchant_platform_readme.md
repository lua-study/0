# 商户平台

> 商户平台 - 权限拆分管理

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:6789
npm run dev

# build for production with minification
# 测试环境
npm run build:test
# 预发布环境
npm run build:pre
# 正式环境
npm run build:pro

# build for production and view the bundle analyzer report
npm run build --report

```


# 结构
```
├─build
│      build.js              构建脚本
│      check-versions.js     开发环境版本监测脚本
│      utils.js              多页面配置及其他配置
│      vue-loader.conf.js    vue-loader插件配置(解析.vue组件)
│      webpack.base.conf.js  开发与生产环境构建通用配置
│      webpack.dev.conf.js   开发环境构建配置
│      webpack.prod.conf.js  生产环境构建配置
│      
├─config                     构建配置目录
│      dev.env.js            可配置开发环境常量
│      index.js              入口
│      pro.env.js            可配置生产环境常量
│      test.env.js           可配置测试环境常量
│      
├─dist                       生产环境代码，未运行npm run build时不存在
│              
├─node_modules               项目依赖
|
├─src                        项目源代码
│
├─static                     静态文件目录
│  package-lock.json         项目描述锁定文件，可维持项目稳定
│  package.json              项目描述文件
│  README.md                 项目说明文件
└─ index.html                项目入口html
```
## src结构引导
```
├─api
│      axios.js              promise封装
│      index.js              请求导出
│      path.js               接口地址管理
│      
├─assets                     文件下内容会被webpack处理解析为模块依赖
│      css                   公用样式
│      images                项目用到的icon
│      
├─components                 组件,文件夹下最多一层文件夹,文件名单词大写开头(PascalCase)且文件夹名称为组件的名称
│              
├─containers                 容器(装有侧边栏等)
|
├─router                     路由管理
│      development.js        开发环境使用require (开发环境使用懒加载可能会导致热更新不及时)
│      production.js         生产环境使用懒加载
│      index.js              路由地址导出
│
├─store                      vuex,公用状态值储存
│  action.js                 调用mutation方法对数据进行操作
│  index.js                  导出
│  mutations.js              state数据的修改操作
│
├─util                       实用方法的导出
│  index.js                  输出为对象
│
├─views                      页面
│
├─App.vue                    入口vue文件
│  
├─login.js                   登陆后要做的一些内容储存和跳转控制
│  
└─main.js                    入口js文件
```

> views

```
├─index             文件夹名
│  │  index.vue
│  └─ views
│       │   
│       └─ start.vue
│ 
│    
└─sys             
   │  index.vue
   └─ views
        │
        └─ equipmentman
           system
           pos
           onlinePayment
           rule
           rulesManage
           usermgment
           videomanag
```

> store

`vuex引用`
```
export default {

    /** 公用状态 **/
    state:{
        show:false
    },

    /** vue中的computed类似,都是用来计算 state 然后生成新的数据(状态) **/
    getters:{
        not_show(state){
            return !state.show;
        }
    },

    /** 使用$store.commit('switch_dialog')来触发mutations 中的 switch_dialog 方法 **/
    mutations:{
        switch_dialog(state){
            state.show = state.show?false:true;
            //你还可以在这里执行其他的操作改变state
        }
    },

    /** 执行多个mutations需要用action **/
    actions:{
        switch_dialog(context){
            context.commit('switch_dialog');
            //你还可以在这里触发其他的mutations方法
        },
    }
}

项目中使用mapGetters、mapActions 和 mapState
mapGetters 一般写在 computed 中
mapActions 一般写在 methods 中
```


# 组件

```
├─components
│      Breadcrumb.vue            面包屑
│      Header.vue                头部导航
│      Sidebar.vue               侧边栏引用
│      SidebarItem.vue           侧边栏菜单
...
```

# 关于util实用方法
```
├─util.
       getCookie                 获取cookie
       setCookie                 设置cookie
       delCookie                 删除cookie
│      routerTo                  router方法,路由跳转(query)
│      routerToParams            router方法,路由跳转(params)  
│      routerReplace             router放法,路由重定向 
│      selectTitle               filter方法,筛选数组是否有符合条件的key值,返回bool
│      foryear                   时间戳改时间 (年-月-日)
│      fortime                   时间戳改时间 (时:分:秒)
│      getQuery                  获取浏览器参数,query方法
│      getParams                 取浏览器参数,parames方法
│      validTelPhone             固定电话正则验证
│      validMobilePhone          移动电话正则验证
│      validNumber               纯数字正则验证
│      validSocialCreditCode     18位数字&大写字母正则验证
│      validIdentity             身份证号正则验证
│      validEmail                邮箱验证
│      validChinese              中文验证
│      validChineseCode          全角字符验证
│      replaceSpecialSymbol      替换所有特殊字符
│      validSpecialSymbol        匹配所有特殊字符
│      validChineseAndLetter     匹配中文和字母
│      validEmpty                匹配空格
│      replaceChineseAndLetter   替换非字母非汉字字符
│      replaceNumber             替换非数字字符
│      replaceEmpty              替换空格
│      replaceSocialCreditCode   替换除数字和大写字母的其他字符
│      replaceChineseAndBracket  替换除中文和全角括号的其他字符
│      replaceFixPhone           替换除去数字和-的其他字符
│      replaceEmail              替换除大写字母和小写字母和数字和@的其他字符
       negativeNum               不能输入负数
       numHundred                输入1到100的数字
       positiveInt               验证正整数
       twoDecimal                验证数字保留两位小数
       validZipCode              验证邮编
       validFixCode              验证传真
       onlyChinese               只输入汉字
       moreThanZero              只输入大于0的正整数
│      replaceTotal              替换除数字和.之外的其他字符
...
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)