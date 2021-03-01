# webpack react learning

## 项目结构搭建

##  webpack配置文件

1. 安装webpack

		npm install webpack -g  #全局安装
		npm install webpack --save-dev #项目内安装

2. 配置入口文件

		var path = require('path');
		module.exports = {
			// 入口文件
			entry: path.resolve(__dirname, 'src/js/app.js'),
			// 输出文件
			output: {
				// 输出至哪个文件夹
				path: path.resolve(__dirname, 'dist'),
				// 输出的文件名
				filename: 'bundle.js'
			}
		}

3. 运行项目

    	webpack --config webpack.develop.config.js

## 使用package.json改造配置文件

- 方便启动项目,可以在package.json 中添加脚本

		"scripts": {
			"develop": "webpack --config webpack.develop.config.js",
			"publish": "webpack --config webpack.publish.config.js"
		}

- 运行项目

    	npm run develop

## 使用webpack-dev-server实现浏览器自动刷新

1. 安装webpack-dev-server

    	npm install webpack-dev-server --save-dev

2. 修改package.json中配置文件

    	"develop": "webpack-dev-server --config webpack.develop.config.js --devtool eval-source-map --progress --colors --inline --hot --content-base ./dist",

3. 使用npm运行项目

    	npm run develop

- 此时更改代码后,项目会自动构建, 浏览器也会自动刷新

## react&&react-dom以及babel-loader的使用

1. 安装react 和 react-dom

        npm install react react-dom --save

2. 安装babel-loader以及相关依赖

        npm install babel-loader --save-dev
        npm install babel-core babel-preset-es2015 babel-preset-react --save-dev

3. 修改webpack.develop配置文件

        module: {
         rules: [{
                 test: /\.jsx?$/,
                 use: [{
                     loader: 'babel-loader',
                     options: {
                         presets: ['es2015', 'react']
                     }
                 }]
             }]
        }

4. app.js中书写react代码

        // 引入React
        import React, { Component } from 'react'
        // 引入ReactDOM
        import ReactDOM from 'react-dom'

        // 使用ReactDOM渲染html节点
        ReactDOM.render(
             
                hello world
             ,
            document.getElementById('app')
        )

5. dist目录下index.html中引入bundle.js,并且加入一个id为app的div

6. 修改了配置文件需要重新手动构建项目

        npm run develop

## css-loader&&style-loader的使用

1. 安装

        npm install css-loader style-loader --save-dev

2. 修改配置文件

         rules: [{
             test: /\.jsx?$/,
             use: [{
                 loader: 'babel-loader',
                 options: {
                     presets: ['es2015', 'react']
                 }
             }]
         }, {
             test: /\.css$/,
             // 注意:必须先写style-loader再写css-loader
             loader: 'style-loader!css-loader'
             // 下面这种写法也可以
             // use: ['style-loader', 'css-loader']
         }]

3. 书写CSS文件,并在js或jsx文件中引入CSS文件

4. 重新构建

        npm run develop

## sass-loader的使用

1. 安装sass-loader

        // sass-loader的使用需要安装node-sass
        npm install node-sass --save
        npm install sass-loader --save-dev

2. 添加配置文件

        // 处理js中引用sass文件
        {
            test: /\.scss$/,
            use: ['style-loader', 'css-loader', 'sass-loader']
        }

3. 书写sass文件

## url-loader的使用

1. 安装url-loader和file-loader

        npm install url-loader file-loader -save-dev

2. 添加配置文件

        // 处理图片操作
        {
            test: /\.(png|jpg|jpeg|gif)$/,
            use: 'url-loader?limit=25000'
        },
        // 处理iconfont
        {
            test: /\.(eot|woff|ttf|woff2|svg)$/,
            use: 'url-loader?limit=2500'
        }

3. 引用图片文件

## webpack 发布策略

### 修改配置文件

1. 将webpack.develop.config.js中的配置拷贝到webpack.publish.config.js中

2. 新建一个.bablerc文件,添加如下内容,同时去除webpack.publish.config.js中和此相关的配置

        {
            "presets":["es2015","react"]
        }

3. 修改url-loader中相关配置

        // 处理图片操作
        {
            test: /\.(png|jpg|jpeg|gif)$/,
            use: 'url-loader?limit=25000&name=images/[name].[ext]'
                // 构建时会构建一个images文件夹存放图片
        },
        // 处理iconfont
        {
            test: /\.(eot|woff|ttf|woff2|svg)$/,
            use: 'url-loader?limit=2500&name=fonts/[name].[ext]'
                // 构建时会构建一个fonts文件夹存放icon
        }
        
### 分离第三方包

1. 修改入口文件

        // 分离第三方包后的入口文件
        entry:{
            app:path.resolve(__dirname, 'src/js/app.js'),
            // 需要分离的第三方包名写在数组中
            vendors:['react','react-dom']
        },

2. 增加插件

        plugins:[
          // 分离第三方包插件
          new webpack.optimize.CommonsChunkPlugin({name:'vendors',filename:'vendors.js'})
        ]

3. 在index.html中引入vendors.js

4. 运行npm run publish会看到一个vendors.js被生成

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)