# knowlg-pro

> win10风格的一套系统，前端采用layui作为前端框架，后端采用SpringBoot作为服务框架，采用自封装的xml对所有请求进行参数校验，以保证接口安全性。`项目长期更新`，觉得不错的点下star吧

> 注：开源社区版只限学习，切勿使用此版本商用，内设授权码，默认十天删除所有非基础数据

- 项目交流群：(群一(满)：[696070023](http://shang.qq.com/wpa/qunwpa?idkey=e9aace2bf3e05f37ed5f0377c3827c6683d970ac0bcc61b601f70dc861053229))(群二：[836039567](https://shang.qq.com/wpa/qunwpa?idkey=7bb6f29b27f772aadca9c7c4e384f7833c64e9c3c947b5e946c7b303d1fe174a))(群三：[887391486](https://shang.qq.com/wpa/qunwpa?idkey=a65f2e0292eb1048bb13abb7adca302bd83e3465974861ec1f04c2f7fffc4d99))；有问题请提Issues，优先回答Issues问题
- 需要进微信群的，进微信群需要支付五元费用，为了防止发广告的等，望谅解。请加我微信：wzq_598748873
- 如有定制需求，可入群或将需求发送至邮箱`598748873@qq.com`。
- 手机端代码在群文件，可进群获取。
- 如果需要学习资料的（不免费，不贵，一杯咖啡的钱），可以加我微信。
- 不会搭建环境的，可以出钱让作者帮忙搭建，一次100，先付。
- 环境搭建资料获取：进下这个百度网盘群(手机端搜索入群)，3676101838

#### 介绍

- A．管理员可以通过后台对知识库的数据库数据进行批量维护工作，包括导入导出，备份等操作
- B．管理员可以对授权用户实现账号添加功能，通过添加账号可以实现知识库数据的检索展现功能
- C．授权账号通过客户端登录界面登录后可以通过关键字查询，系统展现所有关键字关联的信息供授权账号查询阅读
- D．查询结果显示简要信息列表式呈现，授权用户可以点击进入查看详细内容
- E．授权用户通过微信公众号进行信息内容数据录入，管理员进行审批，经过管理员审批可以收录的直接进入数据库。
- F．数据录入包含标题，内容，编辑人，内容支持图文编辑
- G．检索时支持选择检索对象是标题还是内容
- H. 数据库存放至本地服务器，客户端可以通过手机进行授权访问，管理员可以通过客户端或者浏览器等工具进行集中维护
- I. 可接入微信公众号

#### 启动方式
直接运行com.KnowLeDgeApplication即可，启动完成后，访问`http://localhost:8090`即可。 初始化账号密码：root/123456

#### 功能介绍

功能|功能|功能|功能
-------|-------|-------|-------
菜单管理|员工管理|用户管理|角色管理
权限管理|资源图标|日志管理|多桌面管理
系统基础设置|系统的基础信息设置|知识库类型管理|手机端端展示
知识库管理|批量上传|审核管理|可接入微信公众号

#### 技术选型

##### 后端技术:

技术|名称|版本
---|---|---
[SpringBoot](http://spring.io/projects/spring-boot)|核心框架|2.0.3
[MyBatis](http://www.mybatis.org/mybatis-3/zh/index.html)|ORM框架
[Druid](https://github.com/alibaba/druid)|数据库连接池|
[Maven](http://maven.apache.org/)|项目构建管理|
[redis](https://redis.io/)|key-value存储系统|3.2集群（不要问我单机的能不能行）
[webSocket](http://www.runoob.com/html/html5-websocket.html)|浏览器与服务器全双工(full-duplex)通信|
[quartz 2.2.2](http://www.quartz-scheduler.org/)|定时任务|
[ActiveMQ](http://activemq.apache.org/replicated-leveldb-store.html)|消息队列|
[Java]()|Java|1.8
[MySQL]()|数据库|5.5.28

##### 前端技术：

技术|名称
---|---
[jQuery](http://jquery.com/)|函式库
[zTree](http://www.treejs.cn/v3/)|树插件
[layui](https://www.layui.com/)|模块化前端UI
[winui](https://gitee.com/doc_wei01/skyeye)|win10风格UI(自己做的前端架构)
[handlebars](http://www.ghostchina.com/introducing-the-handlebars-js-templating-engine/)|js模板引擎
[webSocket](http://www.runoob.com/html/html5-websocket.html)|浏览器与服务器全双工(full-duplex)通信

#### 代码描述
##### 前后台接口映射

```
 
	 
 
```

##### 后台代码编写规范

###### 控制层

```
@RequestMapping("后台接口")
public void 方法名(InputObject inputObject, OutputObject outputObject) throws Exception{
	服务层接口对象.方法名(inputObject, outputObject);
}
```

###### 服务层

```
@Override
public void 方法名(InputObject inputObject, OutputObject outputObject) throws Exception {
	Map  map = inputObject.getParams();//接收参数
	Map  user = inputObject.getLogParams();//获取当前登录用户信息
	/**
	 * 业务逻辑
	 */
	outputObject.setBean(bean);//返回单个实体Bean
	outputObject.setBeans(beans);//返回集合
	outputObject.settotal(total);//返回数量
	outputObject.setreturnMessage("信息");//返回前端的错误信息
	outputObject.setreturnMessage("信息", 错误码);//返回前端的错误信息，同时抛出异常（不常用）
}
```

#### 效果图

|效果图|效果图|
| ------------- | ------------- |
|![](https://images.gitee.com/uploads/images/2019/1011/123357_6cbb13ab_1541735.jpeg "")|![](https://s2.ax1x.com/2019/10/11/uHb0jx.jpg "")|
|![](https://images.gitee.com/uploads/images/2019/1011/123435_dbe0068f_1541735.jpeg "")|![](https://s2.ax1x.com/2019/10/11/uHbRCd.jpg "")|
|![](https://images.gitee.com/uploads/images/2019/1011/123526_49900070_1541735.jpeg "")|![](https://s2.ax1x.com/2019/10/11/uHbhvt.jpg "")|
|![](https://images.gitee.com/uploads/images/2019/1011/123700_2a8b9135_1541735.png "")|![](https://s2.ax1x.com/2019/10/11/uHbzrV.png "")|
|![](https://images.gitee.com/uploads/images/2019/1011/123735_a65d3eeb_1541735.png "")|![](https://s2.ax1x.com/2019/10/11/uHqFPJ.jpg "")|
|![](https://s2.ax1x.com/2019/10/11/uHqkG9.png "")||

#### 项目交流：

QQ群号：(群一：[696070023](http://shang.qq.com/wpa/qunwpa?idkey=e9aace2bf3e05f37ed5f0377c3827c6683d970ac0bcc61b601f70dc861053229))
(群二：[836039567](https://shang.qq.com/wpa/qunwpa?idkey=7bb6f29b27f772aadca9c7c4e384f7833c64e9c3c947b5e946c7b303d1fe174a))

> 需要了解的请加微信或者进群：wzq_598748873，备注：码云-公司（姓名）。

|QQ群|公众号|微信群|
|-------|-------|-------|
|![](https://images.gitee.com/uploads/images/2018/1205/145236_4fce6966_1541735.jpeg "微信图片_20181205145217.jpg")|![](https://images.gitee.com/uploads/images/2018/1207/083137_48330589_1541735.jpeg "qrcode_for_gh_e7f97ff1beda_258.jpg")|![输入图片说明](https://images.gitee.com/uploads/images/2019/1026/125556_ff89219a_1541735.jpeg "123.jpg")|

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)