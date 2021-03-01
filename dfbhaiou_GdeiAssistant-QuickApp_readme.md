 
   
 

# 广东二师助手快应用客户端

**广东第二师范学院校园助手系统快应用客户端**，支持的最小平台版本号为1020。客户端根据快应用平台的框架结构、原生接口以及界面组件，使用快应用开发工具进行设计开发，实现了用户常用的教务查询功能。应用的后端API数据接口由广东第二师范学院校园助手系统提供。

## 功能

- 成绩查询
- 课表查询

## 预览

 
   
   
   
 

## 体验

### 体验用户账号

为便于非在校师生用户体验和测试应用，应用提供了体验用户账号。详情请查阅 [广东二师助手体验用户账号说明](https://github.com/GdeiAssistant/GdeiAssistant#%E4%BD%93%E9%AA%8C)

## 初始化

### 克隆仓库

```bash
$ git clone https://github.com/GdeiAssistant/GdeiAssistant-QuickApp.git
```

### 安装依赖

```bash
$ npm install
```

### 配置参数

项目目录下的src/manifest.json文件包含了应用描述、接口声明、页面路由等信息，该配置文件的config属性下的data属性保存了项目的配置参数

1. **防重放攻击**：requestValidateToken是移动端请求服务端的拥有防重放攻击保护的数据接口时，需要携带的令牌信息。该令牌信息应该与服务端中配置的防重放攻击令牌值相同，否则校验无法通过。详情请参考 [广东第二师范学院校园助手系统初始化配置文件说明](https://github.com/GdeiAssistant/GdeiAssistant/blob/master/README.md#%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6)


## 数据接口

广东二师助手微信小程序的后端API数据接口由[广东第二师范学院校园助手系统](https://github.com/GdeiAssistant/GdeiAssistant)提供

数据接口API文档说明请查阅[广东第二师范学院校园助手系统数据接口API文档](https://github.com/GdeiAssistant/GdeiAssistant/wiki)

## 协议

[MIT License](http://opensource.org/licenses/MIT)

[Anti 996 License](https://github.com/996icu/996.ICU/blob/master/LICENSE)

Copyright (c) 2016 - 2019 GdeiAssistant

## 贡献

- 若你喜欢本项目，欢迎Star本项目

- 要贡献代码，欢迎Fork之后再提交[Pull Request](https://github.com/GdeiAssistant/GdeiAssistant-QuickApp/pulls)

- 如果你有好的意见或建议，欢迎给我们提交[Issue](https://github.com/GdeiAssistant/GdeiAssistant-QuickApp/issues)

## 联系

- 技术支持和意见建议反馈：[gdeiassistant@gmail.com](mailto:gdeiassistant@gmail.com)

- 用户客服和系统故障工单提交：[support@gdeiassistant.cn](mailto:support@gdeiassistant.cn)

- 社区违法和不良信息举报邮箱：[report@gdeiassistant.cn](mailto:report@gdeiassistant.cn)

## 声明

本项目只用作个人学习研究，如因使用本项目导致任何损失，本人概不负责。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)