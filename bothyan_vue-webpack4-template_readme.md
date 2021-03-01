
# Vue 项目升级 webpack4

[查看博客](https://blog.csdn.net/xlz26296/article/details/84350881)

由于 vue-cli 2 构建的项目是基于 webpack3，所以只能自己动手改动，至于升级 webpack4之后提升的编译速度以及各种插件自己去体验。

## 修改配置

### 1.替换插件 extract-text-webpack-plugin，使用 webpack4 推荐使用的插件 mini-css-extract-plugin

build/webpack.prod.conf.js

```javascript
// ...省略
// const ExtractTextPlugin = require('extract-text-webpack-plugin')
const MiniCssExtractPlugin = require('mini-css-extract-plugin')
// ...省略

// ...省略
  devtool: config.build.productionSourceMap ? config.build.devtool : false,
  performance: {
    hints: false
  },
// ...省略

// ...省略
    // // extract css into its own file
    // new ExtractTextPlugin({
    //   filename: utils.assetsPath('css/[name].[contenthash].css'),
    //   // Setting the following option to `false` will not extract CSS from codesplit chunks.
    //   // Their CSS will instead be inserted dynamically with style-loader when the codesplit chunk has been loaded by webpack.
    //   // It's currently set to `true` because we are seeing that sourcemaps are included in the codesplit bundle as well when it's `false`,
    //   // increasing file size: https://github.com/vuejs-templates/webpack/issues/1110
    //   allChunks: true
    // }),
    new MiniCssExtractPlugin({
      filename: utils.assetsPath('css/[name].css'),
      chunkFilename: utils.assetsPath('css/[name].[contenthash].css')
    }),
// ...省略
    new HtmlWebpackPlugin({
      filename: process.env.NODE_ENV === 'testing'
        ? 'index.html'
        : config.build.index,
      template: 'index.html',
      favicon: 'favicon.ico',
      inject: true,
      minify: {
        removeComments: true,
        collapseWhitespace: true,
        removeAttributeQuotes: true
        // more options:
        // https://github.com/kangax/html-minifier#options-quick-reference
      },
      // necessary to consistently work with multiple chunks via CommonsChunkPlugin
      // chunksSortMode: 'dependency'
    }),
// ...省略
```

### 2.去掉 webpack.optimize.CommonsChunkPlugin 相关配置

build/webpack.prod.conf.js

```javascript
// ...省略
    // // split vendor js into its own file
    // new webpack.optimize.CommonsChunkPlugin({
    //   name: 'vendor',
    //   minChunks (module) {
    //     // any required modules inside node_modules are extracted to vendor
    //     return (
    //       module.resource &&
    //       /\.js$/.test(module.resource) &&
    //       module.resource.indexOf(
    //         path.join(__dirname, '../node_modules')
    //       ) === 0
    //     )
    //   }
    // }),
    // // extract webpack runtime and module manifest to its own file in order to
    // // prevent vendor hash from being updated whenever app bundle is updated
    // new webpack.optimize.CommonsChunkPlugin({
    //   name: 'manifest',
    //   minChunks: Infinity
    // }),
    // // This instance extracts shared chunks from code splitted chunks and bundles them
    // // in a separate chunk, similar to the vendor chunk
    // // see: https://webpack.js.org/plugins/commons-chunk-plugin/#extra-async-commons-chunk
    // new webpack.optimize.CommonsChunkPlugin({
    //   name: 'app',
    //   async: 'vendor-async',
    //   children: true,
    //   minChunks: 3
    // }),
// ...省略
```

### 3.增加 optimization 配置

build/webpack.prod.conf.js

```javascript
// ...省略
  optimization: {
  runtimeChunk: {
    name: 'manifest'
  },
  minimizer: [
    new UglifyJsPlugin({
      cache: true,
      parallel: true,
      sourceMap: config.build.productionSourceMap,
      uglifyOptions: {
        warnings: false
      }
    }),
    new OptimizeCSSPlugin({
      cssProcessorOptions: config.build.productionSourceMap
        ? { safe: true, map: { inline: false } }
        : { safe: true }
    }),
  ],
  splitChunks: {
    chunks: 'async',
    minSize: 30000,
    minChunks: 1,
    maxAsyncRequests: 5,
    maxInitialRequests: 3,
    name: false,
    cacheGroups: {
      vendors: {
        test: /[\\/]node_modules[\\/]/,
        name: 'vendor',
        chunks: 'initial',
        priority: -10
      }
    }
  }
}
// ...省略
```

### 4.修改 utils 配置

build/utils.js

```javascript
// ...省略
// const ExtractTextPlugin = require('extract-text-webpack-plugin')
const MiniCssExtractPlugin = require('mini-css-extract-plugin')
// ...省略

// ...省略
    if (options.extract) {
      // return ExtractTextPlugin.extract({
      //   use: loaders,
      //   fallback: 'vue-style-loader'
      // })
      return [MiniCssExtractPlugin.loader].concat(loaders)
    } else {
      return ['vue-style-loader'].concat(loaders)
    }
// ...省略
```

### 5.增加 mode 配置

build/webpack.base.conf.js

```javascript

module.exports = {
mode: process.env.NODE_ENV === 'production' ? 'production' : 'development',
context: path.resolve(__dirname, '../'),
// ...省略
```

### 6.修改 package.json 依赖版本，自己去对比下，其他依赖的升级到最新即可

```javascript
// ...省略
"devDependencies": {
  "autoprefixer": "^9.3.1",
  "babel-core": "^6.26.3",
  "babel-eslint": "^10.0.1",
  "babel-helper-vue-jsx-merge-props": "^2.0.3",
  "babel-jest": "^23.6.0",
  "babel-loader": "^7.1.5",
  "babel-plugin-component": "^1.1.1",
  "babel-plugin-dynamic-import-node": "^2.2.0",
  "babel-plugin-syntax-jsx": "^6.18.0",
  "babel-plugin-transform-es2015-modules-commonjs": "^6.26.2",
  "babel-plugin-transform-runtime": "^6.23.0",
  "babel-plugin-transform-vue-jsx": "^3.7.0",
  "babel-polyfill": "^6.26.0",
  "babel-preset-env": "^1.7.0",
  "babel-preset-stage-2": "^6.24.1",
  "babel-register": "^6.26.0",
  "chalk": "^2.4.1",
  "chromedriver": "^2.44.0",
  "copy-webpack-plugin": "^4.6.0",
  "cross-spawn": "^6.0.5",
  "css-loader": "^1.0.1",
  "eslint": "^4.19.1",
  "eslint-config-standard": "^10.2.1",
  "eslint-friendly-formatter": "^4.0.0",
  "eslint-loader": "^2.1.1",
  "eslint-plugin-import": "^2.14.0",
  "eslint-plugin-node": "^8.0.0",
  "eslint-plugin-promise": "^4.0.1",
  "eslint-plugin-standard": "^3.1.0",
  "eslint-plugin-vue": "^4.7.1",
  "file-loader": "^2.0.0",
  "filemanager-webpack-plugin": "^2.0.5",
  "friendly-errors-webpack-plugin": "^1.7.0",
  "html-webpack-plugin": "^3.2.0",
  "mini-css-extract-plugin": "^0.4.5",
  "jest": "^23.6.0",
  "jest-serializer-vue": "^2.0.2",
  "nightwatch": "^0.9.12",
  "node-notifier": "^5.3.0",
  "optimize-css-assets-webpack-plugin": "^5.0.1",
  "ora": "^3.0.0",
  "portfinder": "^1.0.19",
  "postcss-import": "^12.0.1",
  "postcss-loader": "^3.0.0",
  "postcss-px2rem": "^0.3.0",
  "postcss-url": "^8.0.0",
  "rimraf": "^2.6.2",
  "semver": "^5.6.0",
  "shelljs": "^0.8.3",
  "stylus": "^0.54.5",
  "stylus-loader": "^3.0.2",
  "uglifyjs-webpack-plugin": "^1.1.1",
  "url-loader": "^1.1.2",
  "vue-jest": "^3.0.0",
  "vue-loader": "^14.2.2",
  "vue-style-loader": "^4.1.2",
  "vue-template-compiler": "^2.5.17",
  "webpack": "^4.26.0",
  "webpack-bundle-analyzer": "^3.0.3",
  "webpack-cli": "^3.1.2",
  "webpack-dev-server": "^3.1.10",
  "webpack-merge": "^4.1.4"
},
// ...省略
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)