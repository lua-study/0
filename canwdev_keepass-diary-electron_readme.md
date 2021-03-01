# KeeDiary

日记编辑器，使用 kdbx 作为数据库加密存储你的日记。

> 配合 Syncthing 使用，可以方便的在不同设备同步数据库。

## Screenshots · 截图

![demo](./public/screenshots/01.png)

![demo](./public/screenshots/02.png)

![demo](./public/screenshots/03.png)

![demo](./public/screenshots/04.png)

## TechStack · 技术栈

- Electron
- React (create-react-app、react全家桶，新手学习 React 中，存在诸多性能问题等待后期优化...)
- [kdbxweb](https://github.com/keeweb/kdbxweb) (用于操作数据库，由于网络问题使用了拷贝的国内源)

## Features · 特性

- [X] 打开数据库（`密码`/`密码+密钥`）
- [X] 浏览群组(groups)和群组里面的条目(entries)
- [X] 保存数据库/关闭数据库
- [X] 使用一个变量判断数据库是否被改动
- [X] 加密存储本地密码
- [X] 全数据库搜索功能
- [X] 实现日历视图
- [X] 支持黑暗模式
- 群组(groups)
    - [X] 重命名群组
    - [X] 移动至回收站（如果关闭了回收站则直接删除群组）
    - [X] 清空回收站
    - [X] 移动群组
    - [X] 新建群组
    - [ ] 列表的展开与收缩
    - [x] 渲染性能优化
- 条目(entries)
    - [X] 标题(Title)和内容(Note)的查看与编辑
    - [X] 创建新条目
    - [X] 删除条目
    - [X] 移动条目
    - [X] 列表性能优化
    - [X] 排序（按创建或修改日期排序）
    - [ ] 搜索/过滤
    - [X] Markdown 支持
    - [X] 修改图标

## Run · 运行

```sh
# 安装依赖
yarn install

# 开发模式 
npm run dev
```

## Build · 构建

```sh
# 全局安装 electron-builder
npm -i -g electron-builder

# 首先构建 React
npm run build:react

# 构建 electron 生成可执行文件
npm run build:electron
```

## 备注

- 如果在开发过程中出现 electron 无法启动的问题，请删除应用缓存：`C:\Users\ \AppData\Roaming\ ` （已查明是 `electron-devtools-installer` 插件的问题，已禁用插件）
- 安装**前端**依赖时请务必安装在 `devDependencies`（`yarn add axios --D`），否则，如果安装在 `dependencies` 会一并打包进发行版，从而增大 electron 体积。

## Reference · 参考

- [Building an Electron application with create-react-app](https://www.freecodecamp.org/news/building-an-electron-application-with-create-react-app-97945861647c/)
- [Electron.js 快速入坑指南 - Windows 下的打包](https://canwdev.gitee.io/manual/setup-electronjs.html#windows-%E4%B8%8B%E7%9A%84%E6%89%93%E5%8C%85)
- [KdbxWeb 国内拷贝并修改依赖源](https://gitee.com/canwdev/kdbxweb)
- [Electron 打包优化 - 从 393MB 到 161MB](https://imweb.io/topic/5b9f500cc2ec8e6772f34d79)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)