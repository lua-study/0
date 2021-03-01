### 需要购买的阿里云的同学 请点击支持 [阿里云优惠券2000元](https://chuangke.aliyun.com/invite?userCode=d4l0ykh3)
### 务必记得点赞哦
#### 文档
>   1. 打包好的文件   [下载](https://gitee.com/lele-666/V-IM/raw/master/v-im%20Setup%200.5.3.exe)。
>   2. 打包好的web文件，在dist/web 目标下（运行的时候需要有容器，例如nginx tomcat之类的）。
>   3. 消息推送接口，调用方式：http://localhost:8080/api/user/sendMsg?access_token=你的token&userId=接收人&msg=我是消息
>   4. 获取token：http://localhost:8080/oauth/token?client_id=v-client&client_secret=v-client-ppp&grant_type=password&scope=select&username=wangwu&password=123456
>   5. 测试地址：http://101.200.151.183   wangwu 123456 。
>   6. 安装依赖命令：yarn 。
>   7. 开发环境命令：npm run dev 。
>   8. 打包安装文件：npm run build，打包完成的文件在/build 下。
>   9. 打包web文件：npm run build:web，打包完成的文件在/dist/web 下。

### 注意事项

> 1. 打包时候项目路径不能有中文，包括你 windows 用户都不能有中文字符，因为npm 缓存都是在用户目录下（如果原先的用户名是中文，再修改成英文也不好用，因为原先的npm包都还在中文目录下，可以新建个window 英文账号，登录新账号打包）。
> 2. 使用yarn 安装依赖，npm 不是很好用，尝试过，都不能打包成功。如果yarn 不能安装依赖成功，可以多试几次，或者翻墙后再打包！
> 3. 基于 t-io websocket 协议， 据说能支持百万级并发，但是此项目并没有进行此方面的测试，还请知晓 ！



#### V-0.53 (觉得不错，请帮点star，谢谢)
>   1. 新增功能点：点击用户显示用户信息页面。
>   2. 修改登录界面，把设置放置到密码下面，原先的右下角的小图标不太容易被看到。
>   3. 修改搜索用户点击无效的bug。
>   4. 登录界面美化调整。
>   5. 其他的几个小问题调整。
![图片](doc/img/user-info.png)
#### V-0.52 
>   1. 请更新后台
>   2. 主动推送消息给用户，新增一个system用户，负责给用户推送消息
>   3. 语句 ：INSERT INTO `im_user` (`id`, `avatar`, `name`, `sign`, `mobile`, `email`, `password`, `login_name`, `default_group_id`, `create_date`, `create_by`, `update_date`, `update_by`, `remarks`, `del_flag`) VALUES ('system', '/img/icon.png', '系统用户', '我爱吃肉', '13699988999', 'zhangsan@163.com', '{bcrypt}$2a$10$tcoeSq.LUagBuj6WalYUaeJjvXEI86YBDS6LVCQUfYtjoUvhHaUWC', 'system', '1048889640612864002', '2019-07-04 13:17:34', '', '2019-07-04 13:17:44', '', '', '0');
>   4. 调用方式：http://localhost:8080/api/user/sendMsg?access_token=你的token&userId=接收人&msg=我是消息
![图片](doc/img/system.PNG)
#### V-0.51
>   1. 解决web版本打包问题，直接 npm run build:web 就可以搞定，不用改文件了
>   2. 如不能yarn 安装成功依赖包，请翻墙后再安装。
>   3. 测试地址 http://101.200.151.183   账号：wangwu 123456
 

![logo](build/icons/icon.png)
### 服务端代码在此
>   1. https://gitee.com/lele-666/V-IM-Server
>   2. 测试账号： wangwu/123456  或者可以点注册，自行注册账号。


### 截图

![登录](doc/img/1.PNG)
![群聊](doc/img/2.PNG)
![表情](doc/img/3.PNG)
![分组](doc/img/4.PNG)
![缓存](doc/img/5.PNG)
![图片](doc/img/6.PNG)

#### Build Setup

``` bash
# install dependencies
yarn

# serve with hot reload at localhost:9080
npm run dev

# build electron application for production
npm run build


```

---
### 功能点
> 1. 文本聊天
> 2. 聊天表情
> 3. 发送图片（http）
> 4. 发送文件（http）
> 5. 单聊
> 6. 群聊
> 7. 用户分组（后端支持）
> 8. 离线消息（单聊）
> 9. 聊天记录（单聊、群聊）
> 10. 支持心跳检测，断线重连
> 11. 使用SpringBoot security oauth2.0 支持单点登录。
> 12. 用户搜索。


### 登录测试
> 1. 测试服务器IP:101.200.151.183,在登录界面右下角有设置的地址，默认的是本地（没有服务不好用），请知晓。
> 2. 自己可以注册个用户进行测试，默认。
> 3. 没有提供在线添加好友和管理群组的功能，后续开发，好友关系维护都在后台服务里。
> 4. 打包好的测试文件-->[下载exe安装文件 64位](https://gitee.com/lele-666/V-IM/blob/master/v-im%20Setup%200.3.9.exe)。


### 参考项目及技术
> 1. layIM（主要是聊天表情，文件处理方面）。
> 2. 使用SpringBoot、oauth2.0、t-io 开发后端服务。
> 3. vue、iview 开发前端。
> 4. 界面高仿微信，如有侵权请告知。
> 5. 其他：使用 fetch 发送ajax 请求，支持跨域，electron 支持打包成为exe，也支持linux 和 mac 目前还没测试，有条件的同学可以测试。


### 后续目标
> 1. 开发基于websocket 的安卓和IOS 版本。
> 2. 打包命令调整，支持自动打包不同的版本（已解决）。
> 3. 后端项目做成SpringBoot启动方式（方便集成），后端提供 restful 方式API，支持数据库分库、分表，支持分布式部署 (已经解决SpringBoot) 。
> 4. 需要高手加入项目，现在只有一个人维护前后端实在是吃力。
> 5. 优化稳定性，包括 token 刷新机制调整，目前还没好的方案控制同一用户下的并发问题（出问题几率很低，但是不代表不会出问题）(已经解决)。
> 6. 支持https 本身t-io是支持的，目前还没测试，后续会测试。
> 7. 持续改进，优化！


### 交流群
> 1. QQ群：617853658（新）验证请说明是 V-IM 用户
> 2. 微信群：![图片](doc/wx.PNG)
> 3. 如果您觉得好用，可以给点个star!!!，或者给个捐赠。

This project was generated with [electron-vue](https://gitee.com/lele-666/V-IM/blob/master/v-im%20Setup%200.3.8.exe) using [vue-cli](https://github.com/vuejs/vue-cli). Documentation about the original structure can be found [here](https://simulatedgreg.gitbooks.io/electron-vue/content/index.html).


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)