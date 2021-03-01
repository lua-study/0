# OSChina Android

开源中国官方App客户端开源代码。



## 注意

- 最新版下载地址：[客户端](http://www.oschina.net/app/)
- Master中不再放置源码，请切换到对应Tag查看
- 源码仅作学习，接口将进行限制，如需请求API接口应使用 [openapi](http://www.oschina.net/openapi)



##历史分支

| 标签名                                      | 发布版本                | 备注               |
| ---------------------------------------- | ------------------- | ---------------- |
| [v2.6.9](http://git.oschina.net/oschina/android-app/tree/v2.6.9/) | v2.6.9 (1611220955) | 当前最新版            |
| [v2.6.6](http://git.oschina.net/oschina/android-app/tree/v2.6.6/) | v2.6.6 (1609281026) |                  |
| [v2.6.5](http://git.oschina.net/oschina/android-app/tree/v2.6.5/) | v2.6.5 (1609211120) |                  |
| [v2.6.4](http://git.oschina.net/oschina/android-app/tree/v2.6.4/) | v2.6.4 (1608081154) |                  |
| [v2.6.3](http://git.oschina.net/oschina/android-app/tree/v2.6.3/) | v2.6.3 (1607081128) |                  |
| [v2.6.2](http://git.oschina.net/oschina/android-app/tree/v2.6.2/) | v2.6.2(1606121625)  |                  |
| [v2.4](http://git.oschina.net/oschina/android-app/tree/v2.4/) | --                  | --               |
| [v2.3](http://git.oschina.net/oschina/android-app/tree/v2.3/) | --                  | 迁移到AndroidStudio |
| [v2.2.1](http://git.oschina.net/oschina/android-app/tree/v2.2.1/) | --                  | Eclipse可用        |



##最新版开发环境

1. Android Studio >= 2.2
2. Gradle Version: 2.2.2
3. SDK Tool >= 24.0.3



##项目简述

- 新版相关代码集中在**“net.oschina.app.improve”**包中，其他包中代码将逐步清理。
- 项目分包方式采取功能模块进行分包，查看代码请按功能查询
- 由于接口逐步进行规范化限制，自己编译后将会出现大部分接口请求无数据的情况（这不是BUG）
- 新项目已抛弃**ListView**转而使用**Recyclerview**

#### 相关依赖

- **com.android.support**：Google官方适配包，用于提供卡片、列表、主题等基础模块
- **android-async-http**：当前正在使用的网络框架（后续会进行迁移）
- **butterknife**：注解库，用于简化findView和onClick操作
- **com.google.zxing**：用于二维码扫描
- **pub.devrel:easypermissions**：简化权限请求的库
- **com.github.bumptech.glide**：所有的图片请求管理库
- **de.hdodenhof:circleimageview**：用于圆角图片的实现
- **com.google.code.gson**：Json-Model解析库，新API已弃用XML数据格式
- **net.qiujuer.genius**：用于图片模糊，Material Design 控件5.0以下适配
- **net.oschina.common**：OSChina官方工具包，用于提供基础功能支持



##支持开源

通过以下方式对我们的项目进行支持：

1. 对于🅱ug请通过：描述**(怎么操作？什么情况？手机型号？操作系统？)**->[Issue](http://git.oschina.net/oschina/android-app/issues/new?issue%5Bassignee_id%5D=&issue%5Bmilestone_id%5D=)
2. 如果有时间，你可以自己解决问题并向我们提出 [Pull Request](http://git.oschina.net/oschina/android-app/pulls)
3. 当然，我们提倡通过顶部**捐赠**方式赞助开发小组童鞋们喝杯咖啡



##开源协议

	The MIT License (MIT)

	Copyright (c) 2016 OSChina.net

	Permission is hereby granted, free of charge, to any person obtaining a copy
	of this software and associated documentation files (the "Software"), to deal
	in the Software without restriction, including without limitation the rights
	to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
	copies of the Software, and to permit persons to whom the Software is
	furnished to do so, subject to the following conditions:

	The above copyright notice and this permission notice shall be included in all
	copies or substantial portions of the Software.

	THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
	IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
	FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
	AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
	LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
	OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
	SOFTWARE.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)