
  layui-admin  
  【thinkphp6.0】基于thinkphp的后台管理系统。 

 
 开发文档 
 DEMO[备案中] 
 

## 特性

1. 基于tp6.0
2. 基于layui前端框架
3. 内置用户和权限管理
4. Form类快速构建表单
5. 包含多种表单组件
6. Table类快速构建列表

## Requirement

1. php >= 7.0
2. thinkphp >=6.0.0

## Installation
第一步：
```shell
$ composer create-project topthink/think tp5 && cd tp5

```
第二步：
```shell
$ composer require thans/layui-admin
```
第三步：

```shell
$ php think layuiAdmin:install
```
第四步：

> 先配置好数据库
```shell
$ php think migrate:run
```

安装完成。访问：http://hostname/admin/login.html

## Compoents

* 富文本编辑框【ckeditor4】
* 文本输入框
* 数字输入框
* TextArea输入框
* 单[多]文件[图片]上传
* 开关
* 下拉单选
* 下拉多选
* checkbox
* 权限树
* ICON选择器
* 日期选择，支持多种格式。支持范围。

## Demo

> 界面预览
![login](https://uinge.oss-cn-beijing.aliyuncs.com/Screen%20Shot%202019-08-01%20at%2010.49.20.png)
![form](https://uinge.oss-cn-beijing.aliyuncs.com/Screen%20Shot%202019-08-01%20at%2010.48.01.png)
![list](https://uinge.oss-cn-beijing.aliyuncs.com/Screen%20Shot%202019-08-01%20at%2010.47.48.png)
![console](https://uinge.oss-cn-beijing.aliyuncs.com/Screen%20Shot%202019-08-01%20at%2010.47.39.png)
## License

MIT


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)