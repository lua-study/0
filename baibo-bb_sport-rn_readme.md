# SportRN

[![CircleCI](https://circleci.com/gh/infinitered/ignite-bowser.svg?style=svg)](https://circleci.com/gh/infinitered/ignite-bowser)

## The latest and greatest boilerplate for Infinite Red opinions

This is the boilerplate that [Infinite Red](https://infinite.red) uses as a way to test bleeding-edge changes to our React Native stack.

Currently includes:

- React Native
- React Router
- MobX State Tree
- TypeScript
- And more!

## **常用命令**

 

- 安装项目所需依赖：

  - 安装 cocoapods：`sudo gem install cocoapods`
  - 命令：`./bin/setup`

- app 启动：

  - 1、启动本地 react-native 服务： `yarn run start`
  - 2、安卓模拟器启动： `react-native run-android`
  - 3、ios 模拟器启动： `react-native run-ios`

- 组件示例启动：

  - 1.启动本地 react-native 服务： `yarn run start`
  - 2.关闭启动安卓和 iOS 模拟器的命令窗口
  - 3.在./app/app.tsx 里，文件末尾修改常量的值`const SHOW_STORYBOOK = true`
  - 4.执行 storybook 启动命令：`yarn run storybook`
  - 5.到安卓和 iOS 模拟器上刷新重新加载即可

- h5 启动：`yarn run dev` ,不需要关闭启动安卓和 iOS 模拟器的命令窗口，可以同时开发

- 格式化代码：

  - 所有代码： `yarn run format`
  - 仅针对 js 文件： `yarn run format:js`
  - 仅针对 json 文件：`yarn run format:json`
  - 仅针对 md 文件： `yarn run format:md`
  - 仅针对 ts 文件： `yarn run format:ts`

- 自动化测试：（根路径下的 e2e 文件夹）
  - 准备工作：全局安装`yarn add detox-cli -g`
  - 自动化测试构建：`yarn run build:e2e`
  - 自动化测试启动：`test:e2e`
  - ci:test:e2e
  - ci:build:e2e

## 命令规则

- 文件名： 烤串
- 自定义组件：大驼峰
- 变量： 小驼峰

## Element-Icon

是使用的 react-native-elements，UI 库支持两端，在 components 文件夹下的 elements-icon 文件中分别写了 app 和 web 两端支持的文件
使用：

- 引用： `import { ElementsIcon as Icon } from "../../components"" 相对路径根据文件来找
- 使用：

## Quick Start

The Ignite Bowser boilerplate project's structure will look similar to this:

```
ignite-project
├── app
│   ├── components  组件
│   ├── utils       工具函数
│   ├── models      状态管理
│   ├── navigation  路由
│   ├── screens     视图组件
│   ├── services    请求API
│   ├── theme       主题
│   ├── wide        react-native-web没有支持的三端通用组件
│   ├── app.tsx     app端入口文件
│   ├── environment-variables.ts
├── web          移动网页端入口文件夹
├── storybook       组件用例
│   ├── views
│   ├── index.ts
│   ├── storybook-registry.ts
│   ├── storybook.ts
├── test           单元测试文件夹(inigite-cli集成，实际我们项目中没有去过多关注，某些文件夹下的.test.ts后缀的文件与此有关)
│   ├── __snapshots__
│   ├── storyshots.test.ts.snap
│   ├── mock-reactotron.ts
│   ├── setup.ts
│   ├── storyshots.test.ts
├── README.md
├── android
│   ├── app
│   ├── build.gradle
│   ├── gradle
│   ├── gradle.properties
│   ├── gradlew
│   ├── gradlew.bat
│   ├── keystores
│   └── settings.gradle
├── ignite
│   ├── ignite.json
│   └── plugins
├── index.js
├── ios
│   ├── IgniteProject
│   ├── IgniteProject-tvOS
│   ├── IgniteProject-tvOSTests
│   ├── IgniteProject.xcodeproj
│   └── IgniteProjectTests
└── package.json
```

### ./app directory

Included in an Ignite boilerplate project is the `app` directory. This is a directory you would normally have to create when using vanilla React Native.

The inside of the src directory looks similar to the following:

```
app
│── components
├── models
├── navigation
├── screens
├── services
├── theme
├── utils
├── app.tsx
├── environment-variables.ts
```

**components**
This is where your React components will live. Each component will have a directory containing the `.tsx` file, along with a story file, and optionally `.presets`, and `.props` files for larger components. The app will come with some commonly used components like Button.

**models**
This is where your app's models will live. Each model has a directory which will contain the `mobx-state-tree` model file, test file, and any other supporting files like actions, types, etc.

**navigation**
This is where your `react-navigation` navigators will live.

**screens**
This is where your screen components will live. A screen is a React component which will take up the entire screen and be part of the navigation hierarchy. Each screen will have a directory containing the `.tsx` file, along with any assets or other helper files.

**services**
Any services that interface with the outside world will live here (think REST APIs, Push Notifications, etc.).

**theme**
Here lives the theme for your application, including spacing, colors, and typography.

**utils**
This is a great place to put miscellaneous helpers and utilities. Things like date helpers, formatters, etc. are often found here. However, it should only be used for things that are truely shared across your application. If a helper or utility is only used by a specific component or model, consider co-locating your helper with that component or model.

**app.tsx** This is the entry point to your app. This is where you will find the main App component which renders the rest of the application. This is also where you will specify whether you want to run the app in storybook mode.

### ./ignite directory

The `ignite` directory stores all things Ignite, including CLI and boilerplate items. Here you will find generators, plugins and examples to help you get started with React Native.

### ./storybook directory

This is where your stories will be registered and where the Storybook configs will live

### ./test directory

This directory will hold your Jest configs and mocks, as well as your [storyshots](https://github.com/storybooks/storybook/tree/master/addons/storyshots) test file. This is a file that contains the snapshots of all your component storybooks.

## Running Storybook

From the command line in your generated app's root directory, enter `yarn run storybook`
This starts up the storybook server.

In `app/app.tsx`, change `SHOW_STORYBOOK` to `true` and reload the app.

For Visual Studio Code users, there is a handy extension that makes it easy to load Storybook use cases into a running emulator via tapping on items in the editor sidebar. Install the `React Native Storybook` extension by `Orta`, hit `cmd + shift + P` and select "Reconnect Storybook to VSCode". Expand the STORYBOOK section in the sidebar to see all use cases for components that have `.story.tsx` files in their directories.

## Previous Boilerplates

- [2017 aka Andross](https://github.com/infinitered/ignite-andross)
- [2016 aka Ignite 1.0](https://github.com/infinitered/ignite-ir-boilerplate-2016)

## Premium Support

[Ignite CLI](https://infinite.red/ignite), [Ignite Andross](https://github.com/infinitered/ignite-andross), and [Ignite Bowser](https://github.com/infinitered/ignite-bowser), as open source projects, are free to use and always will be. [Infinite Red](https://infinite.red/) offers premium Ignite support and general mobile app design/development services. Email us at [hello@infinite.red](mailto:hello@infinite.red) to get in touch with us for more details.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)