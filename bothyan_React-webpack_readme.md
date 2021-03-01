#React-webpack项目主要完成什么?
开发react的通用组件

---

##配置

* $ npm install webpack -g
* $ npm install
* $ npm run dev(纯静态页面)
* 打开localhost:8181即可

或者

* $ npm install webpack -g
* $ npm install
* $ npm start(后台express,目前只写了一个接口例子:api/Page,去组件页面可看到有回传的数据)
* 打开localhost:8181即可

---

## 目标组件

- [ ] 轮播图
- [ ] 按钮
- [ ] 输入框
- [ ] 回到顶部
- [ ] 文字提示
- [ ] 分页
- [ ] 图标
- [ ] 选择框
- [ ] 下拉菜单
- [ ] 日期选择器
- [ ] 表格
- [ ] 文件上传
- [ ] 单选框
- [ ] 表单
- [ ] 多选框


---

## 目前已完成组件部分
- [x] MButton
- [x] MTooltip
- [x] MInput
- [x] MBackTop
- [x] MIcon
- [x] MPagination
- [x] MSelect

---


## 残留问题

### 1. 工具类

工具类的作用是为组件或者页面进行事件绑定,例如click等事件,目前只对 document、window这样的全局对象进行处理,类似class、id这样的还未进行过滤处理,后期应该加上,组件和页面都有各自的工具类


### 2. API文档

因为目前主要是在开发组件过程中(同时公司里项目也比较忙),所以API接口文档目前撰写的比较慢,后期会加上去,这样用户在使用的时候则更加的便捷


### 3. 页面响应式

组件开发过程中，也要保证显示页面(不是组件)的自适应


---

##有问题反馈
在使用中有任何问题，欢迎反馈给我，可以用以下联系方式跟我交流

* 邮件(447247261@qq.com)
* QQ: 447247261

---

##关于作者

```javascript
  var siteSource = {
    name  : "梅超",
    site : "http://bigmeichao.com/"
  }
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)