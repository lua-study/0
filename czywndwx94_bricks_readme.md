# bricks

 

#### 项目介绍

开思前端React组件库

 

#### 文档

[bricks文档](https://gitee.com/cassfrontend/bricks-docs)

 

#### 使用

```bash
npm install @casstime/bricks --save

```

```jsx
import { Checkbox } from '@casstime/bricks';
import '@casstime/bricks/dist/bricks.production.css';

const App = () =>  ;

```

推荐使用 [bricks-sample](https://gitee.com/cassfrontend/bricks-sample)
 

#### 开发

```bash
npm run site  # 运行文档
npm run build # 构建
```

 

#### 目录结构

 

```js
design	// 设计文档

dist\	// 构建后的输出目录

docs	// 使用文档

site\   // 文档站点目录

	components	// 组件

	config\	// 左侧导航配置
    
    	index.js	// 左侧导航配置

	libs	// 文档工具类

	styles	// 公共样式

	webpack.config.js	// webpack配置

src\	// 源码

	assets	// 图标库

	components  // 组件

	dom // dom接口调用配置：提供jqury的方式使用组件

	styles	// 组件样式

	types	// 第三方包接入配置：引用组件传入数据接口类型定义

	utils	// 工具函数

 .editorconfig // 编辑器配置

 .gitignore    // git忽略的文件配置

CHANGELOG	// 更新日志

package.json  // 依赖管理

README.md     // 项目描

TODO.md       // 待办事项

tsconfig.json // ts配置

tslint.json   // ts风格检查

webpack.config.js // webpack配置

```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)