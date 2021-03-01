# 新德汇地图应用类库

基于Openlayers的地图应用Vue组件。内置了百度、高德、天地图瓦片，并支持与方正、超图、山海经纬、航天精一等PGIS厂商对接。 
包含文本、图形、html、热力图、轨迹回放等20个组件，支持与ECharts结合实现散点、飞行迁徙等基于地理位置的图表，满足项目常见需求。 
使用者不需要有地图相关专业知识，甚至不需要写任何JS代码就能实现通用功能。

![info](https://images.gitee.com/uploads/images/2020/0529/101300_8d254ed7_1386281.png)

## 重要说明

`xdh-map` 完成了升级改版， 为了提供更好的开发体验，现已集成到了【MY】。 代码仓库已迁移到 [https://gitee.com/newgateway/my](https://gitee.com/newgateway/my)


## 开发指南

- [官网](http://newgateway.gitee.io/my/)
- [开发指南](http://newgateway.gitee.io/my/guide/)
- [基础组件库](http://newgateway.gitee.io/my/ui/components/)
- [地图应用类库](http://newgateway.gitee.io/my/ui/map/)

## 预览

![info](https://images.gitee.com/uploads/images/2020/0529/101300_9eb21d13_1386281.jpeg)

![info](https://images.gitee.com/uploads/images/2020/0529/101300_1d2deb0d_1386281.jpeg)

![info](https://images.gitee.com/uploads/images/2020/0529/101301_0a6ab494_1386281.jpeg)

![info](https://images.gitee.com/uploads/images/2020/0529/101300_c64e0713_1386281.jpeg)

![info](https://images.gitee.com/uploads/images/2020/0529/101301_3fc645f5_1386281.jpeg)

![info](https://images.gitee.com/uploads/images/2020/0529/101301_0e78ba10_1386281.jpeg)


## 安装

推荐使用 npm 的方式安装，它能更好地和 webpack 打包工具配合使用。
```sh 
npm i @xdh/my --save
```

## 快速上手

可通过以下两种使用 `My`

### 一、采用项目工程模板创建项目【推荐】

官网提供的基于Vue项目的一站式解决方案。

```sh 
git clone https://gitee.com/newgateway/my-web.git
```

只需把工程模板项目获取下来就可以使用，包括全部功能，开箱即用。

### 二、调用组件库功能

如只需用到 `My` 其中的某些组件，可以在已有的项目工程中安装，并完成配置。步骤：

#### 1、安装组件库和相关插件

安装组件
```sh 
npm i element-ui @xdh/my --save
```

安装项目依赖插件
```sh 
npm i babel-plugin-component node-sass sass-loader --save-dev
```

#### 2、配置 `babel.config.js`

组件采用了按需加载，需要 在`babel.config.js` 加上插件，如：
```js  
module.exports = {
  presets: [
    '@vue/cli-plugin-babel/preset'
  ],
  plugins: [
    [
      'component',
      {
        libraryName: 'element-ui',
        styleLibraryName: `theme-chalk`
      }
    ],
    [
      'component',
      {
        libraryName: '$ui',
        libDir: 'components',
        styleLibraryName: `~node_modules/@xdh/my/ui/lib/styles`,
        ext: '.scss'
      },
      '$ui'
    ],
    [
      'component',
      {
        libraryName: '$ui/charts',
        libDir: 'packages',
        style: false
      },
      '$ui/charts'
    ],
    [
      'component',
      {
        libraryName: '$ui/map',
        libDir: 'packages',
        style: false
      },
      '$ui/map'
    ],
    [
      'component',
      {
        libraryName: '$ui/go',
        libDir: 'packages',
        style: false
      },
      '$ui/go'
    ]
  ]
}
```

#### 3、配置 `vue.config.js`

需要在`vue.config.js`加上别名，如：

```js 
module.exports = {
  transpileDependencies: ['@xdh/my'],
  chainWebpack(chain) {
    chain.resolve.alias.set('$ui', '@xdh/my/ui/lib')
  }
}
```

#### 4、引用组件
到此，你可以开始引入组件开始编码了，如：
```html 

 
    
 

 
  import {MyMap} from '$ui/map'
  export default {
    components: {
      MyMap
    }
  }
 
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)