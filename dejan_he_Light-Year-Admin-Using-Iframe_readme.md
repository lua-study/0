# Light Year Admin Using Iframe 光年后台模板的iframe版本

#### 演示网址
[http://lyear.itshubao.com/iframe](http://lyear.itshubao.com/iframe)

[猛戳这里去Light Year Admin项目](https://gitee.com/yinqi/Light-Year-Admin-Template)

[猛戳这里去Light Year Admin V4项目(基于bootstrap 4.4.1版本)](https://gitee.com/yinqi/Light-Year-Admin-Using-Iframe-v4)

#### 文档说明
文档里面对一些常见问题做出了说明，并且在使用过程中改动的示例。

[点击查看文档说明](http://www.itshubao.com/doc-lyear/lyear.html)

#### 其他插件整合示例
有些插件可能你并不一定能用上，这里对其他很多的一些插件整合以示例的形式出现，自己选择需要的插件下载。

[点击查看其他插件整合](https://gitee.com/yinqi/Light-Year-Example)

#### 交流群
703726776

#### 介绍
![light year admin](https://images.gitee.com/uploads/images/2019/0314/224956_3eb2a29a_82992.png "未命名-1.png")

该项目是光年后台管理模板(Light Year Admin)的ifame版本。

#### 说明
项目在Light Year Admin的基础上整理修改而来，用到了开源项目[Bootstrap-Multitabs](https://gitee.com/edwinhuish/multi-tabs)来实现多标签页，稍微做了一些修改。在这感谢该开源项目的小伙伴。

- 相对于Light Year Admin的项目，去掉了暗黑和半透明的两个主题
- 所有需要的链接加上`class="multitabs"`
- 因为插件做了一些修改，在顶部的下拉菜单(dropdown-menu)中，不要把链接写在href里面，放到data-url里
- 插件用到了HTML5的会话存储，因此在修改了init里的默认地址后，可以再浏览器控制台执行下sessionStorage.clear(); // cache配置为true时
- 在iframe的页面中新建tab的使用方法， &lt;a href=&quot;#!&quot; class=&quot;js-create-tab&quot; data-title=&quot;按钮&quot; data-url=&quot;lyear-buttons.html&quot;&gt;新建按钮&lt;/a&gt; 

#### 特别感谢
- Bootstrap(去掉了自带的字体图标)
- JQuery
- bootstrap-colorpicker
- bootstrap-datepicker
- bootstrap-datetimepicker
- ion-rangeslider
- jquery-confirm
- jquery-tags-input
- bootstrap-notify
- Chart.js
- chosen.jquery.js
- perfect-scrollbar
- Bootstrap-Multitabs

#### 更新记录
2020.05.18
老登录页面增加背景，新增三个登录页面

2020.01.06
css中去掉system-ui解决input-group双边框问题，改toolWidth值未固定值

2019.12.29
调整登录页面样式以及多图上传样式

2019.12.18
修改右键菜单绑定方式

2019.12.15
增加内页打开tab的js方法

2019.12.08
修改cssbug，新增card-footer，新增通用绑定iframe打开tab的方法，增加图标的一些使用类

2019.08.04
修改样式bug

2019.07.21
修复tab高度bug，侧边栏改为小图标形式，tab关闭按钮改为右侧总是显示，点击tab标签侧边栏选中

2019.07.02
增加右键关闭其他操作，替换logo

2019.06.27
表格插件页面新增treegrid使用示例

2019.06.26
调整tabs高度，替换size()方法
新增右键菜单刷新和关闭功能

2019.05.13
略微调整单选框和复选框的样式
新增表格插件(bootstrap-table)简单示例页面

2019.05.05
修改Bootstrap-Multitabs插件js，新增缓存配置cache，默认为false，如果需要缓存，可以在index.min.js增加配置cache : true

2019.04.24
新增文档示例页面增加多图上传样式（只有样式），调整标签插件样式和js的默认提示
新增步骤条样式和向导插件，修改消息方法（新增自定义消失时间），增加错误页面(404)，增加通知消息页面说明，调整设置页样式

#### 截图
![示例截图一](https://images.gitee.com/uploads/images/2019/0403/213459_1dd52161_82992.png "首页 - 光年(Light Year Admin)后台管理系统模板4.png")
![示例截图二](https://images.gitee.com/uploads/images/2019/0403/213521_8939b9bc_82992.png "首页 - 光年(Light Year Admin)后台管理系统模板3.png")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)