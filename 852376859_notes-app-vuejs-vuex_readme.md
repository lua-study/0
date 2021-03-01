# notes-app-vuejs-vuex
Learn Vuex by Building a Notes App

## 项目启动步骤

```
1、git clone https://git.oschina.net/852376859/notes-app-vuejs-vuex.git

2、cd notes-app-vuejs-vuex

3、npm install

4、npm run dev(在默认浏览器下自动打开)

```

## Vuex学习笔记

### Vuex 概述

Vuex 是一个主要应用在中大型单页应用的类似于 [Flux](https://facebook.github.io/flux/) 的数据管理架构。它主要帮我们更好地组织代码，以及把应用内的的状态保持在可维护、可理解的状态。

Vuex 把状态分成  **组件内部状态**  和  **应用级别状态**  ：

- 组件内部状态：仅在一个组件内使用的状态(data 字段)

- 应用级别状态：多个组件共用的状态

### 问题背景：

举个例子：比如说有一个父组件，它有两个子组件。这个父组件可以用 props 向子组件传递数据，这条数据通道很好理解。

那如果这两个子组件相互之间需要共享数据呢？ 或者子组件需要向父组件传递数据呢?这两个问题在应用体量较小的时候都好解决，只要用自定义事件即可。

但是随着应用规模的扩大：

- 追踪这些事件越来越难了。这个事件是哪个组件触发的？谁在监听它？
- 业务逻辑遍布各个组件，导致各种意想不到的问题。
- 由于要显式地分发和监听事件，父组件和子组件强耦合。

### Vuex可以做些什么？

Vuex 要解决的就是这些问题，Vuex 背后有四个核心的概念：

- 状态树: 包含所有应用级别状态的对象
- Getters: 在组件内部获取 store 中状态的函数
- Mutations: 修改状态的事件回调函数
- Actions: 组件内部用来分发 mutations 事件的函数

下面这张图完美地解释了一个 Vuex 应用内部的数据流动：

![输入图片说明](https://sfault-image.b0.upaiyun.com/812/064/81206477-57200ab9b8e52_articlex "在这里输入图片标题")

这张图的重点：

- 数据流动是单向的
- 组件可以调用 actions
- Actions 是用来分发 mutations 的
- 只有 mutations 可以修改状态
- store 是反应式的，即，状态的变化会在组件内部得到反映


[想参考完整文章请点击我](https://segmentfault.com/a/1190000005015164)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)