#### 1、Vue 项目初始化

1. 使用 图形化界面方式 创建项目
2. 启动项目
3. 在插件这一栏安装 element 插件
4. 在依赖这一栏安装 axios
5. 在 src/plugins/element.js 文件中导入 element 样式


#### 2、初始化 git 仓库

1. 在本地使用 git status 查看本地文件状态
2. 如果没有保存，使用 git add. 将代码上传到暂存区
3. 使用 git commit xxx 将代码传到 git 仓库
4. 在码云上创建 git 仓库，
5. 根据已有仓库的命令，将本地的代码传到码云即可


#### 3、Token

1. HTTP 是一种无状态协议
2. cookie -- 客户端维持服务器和客户端的会话机制
3. session -- 服务器维持服务器和客户端的会话机制
4. Token -- 服务器维持服务器和客户端的会话机制
5. 如果前端和后台存在跨域，建议使用 Token 维持会话机制，否则使用 cookie、session



#### 4、登录页面布局分析以及 分支操作

1. 使用严谨的分支创建方式
2. 首先基于 master 创建 develop 分支
   - `git checkout -b develop`
3. 基于 develop 创建 feature 功能分支
   - `git checkout -b feature/20200622-login`


#### 5、梳理项目结构

1. 清空 `App.vue`  中的内容，只呈现一个基础结构
2. 清空 `router/index.js` 中的内容，只呈现一个基础结构
3. 将 `components` 以及 `views` 目录下的文件删除，不要删文件夹


#### 6、创建登录组件并配置路由

1. 在 `views` 目录下创建 `Login.vue` 登录页面组件
2. 在组件中创建页面的基础结构
3. 在 `router/index.js` 中配置路由
   - 导入 `Login.vue` 登录页面组件
   - 在 `routes` 中配置路由规则
   - 设置重定向


#### 7、绘制登录区域的盒子和登录区域

1. 给 `Login.vue` 组件的跟组件设置类名 `login-container`
2. 在 `style` 中写样式，会报错，
3. 安装 `less`、`less-loader` 重启服务即可
4. 在 `assets` 目录中 创建 `styles` 目录，然后创建 `global.css` 文件
5. 将 `global.css` 文件在入口文件导入
6. 在 `Login.vue` 的 `style` 中继续写登录框盒子的样式即可


#### 8、登录区域头像
> 样式布局，步骤略


#### 9、登录输入框和按钮
> 使用 element 给提供的组件实现布局

1. 找到 `from` 表单组件，复制基础组件前面四行，到项目使用区域粘贴
2. 在 `element.js` 中按需导入组件
3. 根据登录的区域，复制三份 `el-form-item`, 实现基础布局
4. 将最后一个 `el-form-item` 调整为按钮
5. 进行样式布局


#### 10、给输入框添加 icon

1. 将素材中的 `icon` 图标库放到 `assets` 文件夹中
2. 在入口文件 `main.js` 中导入字体图标的 `css` 文件
3. 使用 `element` 给提供的 `prefix-icon` 属性添加类名
4. 使用深度作用选择器 `/deep/` 调整 `icon` 演示


#### 11、表单数据绑定

1. 查阅文档，得知使用 `model` 属性绑定数据，按照文档进行开发
2. 给 `el-form` 绑定 `model` 属性，在 `data` 中声明绑定的数据对象 `loginForm`
3. 在 `loginForm` 中声明需要绑定的 `username` 以及 `password` 数据
4. 使用 `v-model` 绑定 `loginForm` 中的数据


#### 12、表单验证

1. 查阅文档得知，实现校验，如果给 `form` 表单绑定 `rules`属性
   同时给 `form-item` 属性添加 prop 属性
2. 给 `form` 表单绑定 `rules`属性，同时在 `data` 中声明校验规则字段
   注意规则写法： rules 是一个对象，每一个校验规则是一个数组
3. 给 `form-item` 属性添加 prop 属性，属性值为声明的校验字段



#### 13、重置操作

1. 查阅文档得知，实现重置可以使用组件给提供的 `resetFields` 方法
2. 给 `from` 表单添加 `ref` 属性
3. 点击重置按钮，使用 `this.$refs` 获取到组件实例
   使用 `this.$refs.loginFormRef` 可以获取到 `form` 组件实例
   然后使用 `form` 组件实例调用 `resetFields` 方法即可实现重置


#### 14、表单预校验
> 当用户打开登录页面，直接点击登录，进行预校验

1. 查阅文档得知，实现重置可以使用组件给提供的 `validate` 方法
2. 给登录按钮绑定事件 `login`
3. 在 `methods` 中定义 `login` 事件处理程序
4. 在事件处理程序中，获取到表单引用对象 `this.$refs.loginFormRef`
   然后调用 `validate` 方法，这个方法接收一个回调函数作为参数，回调
   函数的参数接收一个值，是验证以后的结果


#### 15、发起登录请求

1. 在 `main.js` 文件中导入 `axios`，并 配置根域名，同时将 `axios` 挂载到原型上
2. 在 `Login.vue` 的登录方法 `login` 中，发起请求
3. 首先校验用户名和密码是否符合规范，如果不符合，结束代码运行
4. 如果符合要求，则发起登录请求，获取后台返回的值
5. 根据后台返回的值，做相应的判断处理即可


#### 15、消息提示

1. 按需导入 `Message` 组件，按照文档，将组件挂载到 Vue 的原型对象上
2. 在需要使用组件的地方，使用 `this.$message.xxx` 即可实现调用


#### 16、登录后的操作

1. 将 `Token` 使用 `sessionStorage` 保存到本地
2. 使用编程式导航实现路由的跳转
3. 在 `router.js` 中配置路由
4. 创建 `Home.vue` 页面组件，并初始化页面结构


#### 17、退出功能

1、点击按钮，触发 `logout` 退出方法
2、在方法中，清空本地存储并实现页面的跳转


#### 18、登录退出功能 git 操作

1. 删除 `fonts` 目录下的 `iconfont.js` 文件
2. `git status`
3. `git add .`
4. `git commit -m 登录和退出功能`
5. `git checkout develop`
6. `git merge xxx`
7. `git push`


#### 19、主页功能
> 根据设计稿分析页面主题布局

1. `element` 给提供了 `container` 布局容器，辅助实现布局
2. 根据设计稿分析，那个常用的布局符合业务的需求，进行拷贝
3. 导入布局容器组件并绑定
4. 给布局容易设置样式即可
5. 给 `container` 添加类名，并设置高度为 100%

#### 20、头部区域布局
> 使用 flex  进行布局即可

#### 21、侧边栏区域布局
> 使用 element 给提供的 NavMenu 导航菜单组件

1. 复制组件到页面中
2. 在 `element.js` 中导入并绑定组件
3. 将组件调整成我们需要的格式

#### 22、添加请求头
> 使用 element 给提供的 NavMenu 导航菜单组件

1. 复制 `axios` 请求拦截器到 `main.js` 中，
2. 注意，需要放到挂载到 `vue` 原型之前
3. 在第一个函数中配置 `Authorization` 字段，值为本地的 `token`


#### 22、获取左侧菜单数据

1. 在 `methods` 中声明 `getMenus` 方法，用来获取左侧菜单数据
2. 方法创建好后，在 `created` 中调用声明的方法
3. 在方法内部，使用 `axios` 发起请求，
4. 将获取到的数据赋值给 `data` 中的 `menus` 属性


#### 23、渲染左侧菜单数据
> 使用双层 v-for 循环

1. 注意： 给 index 绑定属性值需要是 string 字符型


#### 24、更改图标

1. 首先更改二级图标，替换为 `el-icon-menu`
2. 一级的图标处理比较繁琐，需要我们自定义数据，经过分析，每次循环会
   产生不同的分类 `id`，这时候，我们可以创建一个对象 `iconsObj`，
   对象的键是分类的 `id`，只需要将键的值定义为 `icon` 图标的类名即可,
   这样在每次循环的时候，可以根据 `id` 访问到对象中对应的 `id`，
   从而获取到 `icon` 图标进行绑定


#### 25、控制菜单的展开和折叠

1. 布局三个竖线区域的样式
2. 使用 `element` 给提供的 `collapse` 属性控制菜单是折叠还是展开
   `true` 是展开，`false` 是折叠，
3. 给控制按钮绑定事件，点击按钮以后，对 `collapse` 进行动态控制
   需要在 `data` 中声明 `isCollapse` 属性
4. 给 `menu` 添加 `collapse-transition` 属性去掉过渡动画
5. 根据 `isCollapse` 属性动态设置 `menu` 的宽度



#### 27、路由重定向
> 进入后台需要进入欢迎页面

1. 定义 `welcome` 组件
2. 在 `router.js` 中导入 `welcome` 组件
3. 在 `router.js` 中 `home` 规则下配置子路由
4. 配合重定向
5. 在 `Home.vue` 中添加路由占位符


#### 28、分类菜单改造

1. 给 `menu` 组件添加 `router` 属性
2. 动态绑定 `router`


#### 29、用户功能分支创建

1. `git status`
2. `git add .`
3. `git commit -m 主页功能`
4. `git checkout develop`
5. `git merge xxx`
6. `git log --oneline ` 
7. `git push`
8. `git checkout -b feature/20200206-user`


#### 30、展示用户列表组件

1. 在 `views` 目录下创建 `User --> Users.vue` 用户列表组件
2. 在组件中创建页面的基础结构
3. 在 `router.js` 文件中导入组件，并配置子路由，展示用户组件
4. ☆☆☆☆☆ 注意 @ 符号代表的是 src 目录


#### 31、用户列表组件基础布局 1
> 使用 element 提供的组件实现功能

1. 复制提供的面包屑导航 `el-breadcrumb` 实现页面内的导航布局
2. 赋值提供的卡片组件 `el-card` 实现主体区域的布局
3. 在全局调整样式
4. 使用提供的 `el-input` 复合型组件实现搜索区域布局
5. 使用提供的 `Layout` 布局实现宽度调整
6. 使用 `el-button` 按钮组件实现添加按钮的布局


#### 32、获取用户列表数据

1. 在 `methods` 中创建 `getUserList` 方法，用来获取用户列表数据
2. 在 `created` 中调用  `getUserList` 方法
3. 在 `data` 中初始化请求参数 `queryInfo`
4. 在  `getUserList` 方法根据接口文档发送请求
5. 将后台返回的数据赋值给 `data` 中属性


#### 33、渲染用户列表表格

1. 使用 `element` 提供的 `table` 表格实现页面的渲染
2. 给 `table` 绑定 `data` 属性，渲染数据
3. 给 `el-table-column` 添加 `label` 属性渲染类名
4. 给 `el-table-column` 添加 `prop` 属性渲染字段
5. 给 `el-table-column` 添加 `align` 属性设置对其方式


#### 34、分页功能
> 使用 `element` 提供的分页组件实现

1. 将 `el-pagination` 分页组件拷贝到项目中，分析参数
2. 将方法和参数进行声明或者配置
3. 在 `handleSizeChange` 和 `handleCurrentChange` 处理业务逻辑
4. 更改样式

#### 35、更改状态

1. 给 `switch` 绑定 `change` 事件，触发事件处理程序 `userStatueChange`
2. 将当前用户的数据给事件处理程序
3. 在事件处理程序中，发送 `ajax` 请求，将数据同步到服务器
4. 如果更改成功，提升用户更新成功
5. 如果没有更改成功，不让 `switch` 发生更改，并给用户错误的提示


####  36、添加用户
> 弹框使用 dialog 组件

#### 37、添加用户布局
> 参考登录

#### 37、自定义校验规则
> 参考文档

1. 在 data 中声明函数创建自定义规则
   注意：自定义规则需要写到 return 上方
2. 将创建好的规则，在 `addFormRules` 对象中传递给 `validator` 属性


#### 38、清空校验规则

1. 给 `dialog` 组件绑定 `close` 关闭事件，触发事件处理程序 `closeAddDialog`
2. 在事件处理程序中，获取到 `addForm` 的表单对象，调用 `resetFields` 方法


#### 39. 添加用户

1. 给添加按钮绑定事件 `addUser`
2. 在事件中首先使用 `validate` 方法做预校验
3. 在方法内部发起网络请求，将数据发送到服务器
4. 根据返回的值，给用户提示
5. 关闭弹框


#### 40. 编辑用户弹框
> 参考添加用户


#### 41. 获取到用户信息
> 可以使用 id 调用接口，也可以直接使用 scope.row 中的数据

1. 给编辑按钮绑定事件，使用作用域插槽传递 `id` 给事件处理程序
2. 在事件处理程序中，根据 `id` 发送网络请求
3. 根据返回的状态值做判断
4. 将返回的值赋值给 `data` 中的 `editForm`


#### 42. 编辑用户所有的功能参考添加用户
> 功能、方法、验证等规则一致



#### 43. 删除用户操作

1. 给删除按钮绑定 `click` 事件，触发 `removeUserById` 函数，
   并通过 `scope.row.id` 传递参数
2. 点击后的弹框的使用的是 `MessageBox` 组件，首先需要把组件进行
   导入并挂载到 `Vue` 的原型上，
   注意：只需要挂载 `confirm` 这一个函数即可
3. `this.$confirm` 这个方法返回一个 `promise` 对象，
   所以我们可以使用 `await` 以及 `async` 进行简化操作，
   获取到返回值
4. 点击取消以后，捕获不到错误，需要个 `this.$confirm` 方法绑定一个
   `catch` 方法，返回 `err` 错误对象
5. 同意删除返回 `confirm`，不删除返回 `cancel`
6. 根据返回的值做相应的判断处理


####  43. 分支操作

1. `git status`
2. `git add .`
3. `git commit -m 用户管理完成`
4. `git checkout develop`
5. `git merge xxx`
6. `git log --oneline ` 
7. `git push`
8. `git checkout -b feature/20200627-rights`

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)