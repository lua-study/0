![mahua](mahua-logo.jpg)
关于 QueryBuilder
---------------------------
QueryBuilder是一个基于可视化复杂SQL拼接的一个插件，主要用来缓解用户使用PLSQL或SQL developer构建复杂SQL时的可读性差的问题。

QueryBuilder使用了Bootstrap框架、Jquery.form、Jquery.validate等技术，构成了一个具有优雅的界面可视化、功能齐全化、使用化的扁平化的SQL动态拼接插件。

它支持浏览器缩放，支持主流浏览器心访问（IE8以上，Chrom,fireFox,Opra），但是建议使用Chrome浏览器访问。


QueryBuilder功能和开发进度
---------------------

*  查询模板管理功能
    - [x] 可以进行日常的查询模板的维护
    - [x] 显示查询模板的重要信息
    - [x] 维护查询模板中`查询类`信息
    - [x] 管理查询类的别名
    - [x] 维护查询结果显示列
* 复杂SQL构建功能
    - [x] 构建一个复杂的SQL查询语句
    - [x] `智能化`的约束值输入
    - [x] 可视化的查看、恢复、重置上次保存的查询模板下的SQL
    - [ ] `保存`建立的复杂的SQL语句
	- [x] 支持用户自定义输入值的类型选择-需要在queryBuilder.method.js文件中定义要自定义使用的组件
* 查询结果管理
    - [ ] 基于Boootstrap风格的扁平化的查询结果显示
    - [ ] `分页显示`查询结果
    - [ ] 显示`数据修正`
    - [ ] `数据导出`
*  查询模板嵌套
	- [ ]  更加复杂化的SQL模板嵌套拼接
	
*  表管理功能
    - [ ] 此功能模型待研究

QueryBuilder 操作流程
----------------------

### 流程图
暂缺
- [ ] 

开发环境
----------
jdk>1.6  tomcat 1.6 myeclipse


QueryBuilder 依赖
----------------------
*  jQuery-1.9以上版本
*  Bootstrap-3以上版本
*  Sweetalert
*  jquery.form
*  Jquery.validate
*  bootstrap-datetimepicke
*  bootstrap-select2
*  bootstrap-typeahead

QueryBuilder 使用方法
-----------------------
*  1.按照依赖顺序引入依赖包
*  2.引入queryBuilder.js
*  3.引入queryBuilder.method.js


	
QueryBuilder 功能展示
--------------------
请移步此处查看我们的演示平台：[查看演示](http://www.niubai.net.cn)
### 展示1：模板管理界面
>![模板管理](http://static.oschina.net/uploads/space/2016/0518/152546_eo7k_2303434.png)

### 展示2：SQL拼接组装
>![SQL拼接](http://static.oschina.net/uploads/space/2016/0616/200347_P8pL_2303434.png)



有问题反馈
---------------
在您使用 QueryBuilder 的过程中有任何意见和建议，请提交Issue或在项目下方的评论去进行评论，我们的开发者会对您的问题或意见进行优化或在这里跟您沟通。

在添加 Issue 时，请务必对问题或建议添加详细的描述。提出的 Issue 标题应当简明扼要，Issue 内容正文应当详细具体，最好提供问题的截图和修改建议。

欢迎通过[基于可视化复杂SQL拼接插件 QueryBuilder](http://my.oschina.net/guopengfei/blog/479886)来了解本项目原始开发逻辑，同时欢迎访问我的博客[博客](http://my.oschina.net/guopengfei)。

欢迎加入我的QQ群进行技术交流:[QQ群链接](http://shang.qq.com/wpa/qunwpa?idkey=bda5b5a19dee571bad393db084f379e6eb2bdf068d2be05c0d511d857c03d654)

在使用中有任何问题，欢迎反馈给我，可以用以下联系方式跟我交流

* 邮件(guopengfeiheze@163.com)
* QQ: 825338623
* QueryBuilder 官网: [@QueryBuilder](http:/www.niubai.net.cn)

##捐助开发者
在兴趣的驱动下,写一个`免费`的东西，有欣喜，也还有汗水，希望你喜欢我的作品，同时也能支持一下。

支持方法：
>![SQL拼接](http://static.oschina.net/uploads/space/2016/0616/202527_ggxh_2303434.png)

##项目参与人名单
感谢一下参与人的支持,排名不分先后

* [郭鹏飞](http://my.oschina.net/guopengfei) 
* [武彩平](htp://my.oschina.net/wucaiping)

声明
===================================
本项目版权归属开发作者所有，仅限于研究学习之用，不得用于商业项目。

未经许可，如已经发现，将付诸法律；如有意用于商业项目，请与作者联系，谢谢。

##代码展示

```javascript
  var ihubo = {
    nickName  : "QueryBuilder",
    site : "http://www.niubai.net.cn"
  }
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)