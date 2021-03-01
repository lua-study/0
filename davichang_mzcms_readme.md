
## mzcms 基于Yii2高级版企业网站cms
>交流群：584202801 博客地址：https://www.fankers.cn

- 安装使用方法
```

1、克隆代码
2、导入数据库 /docs/sql cms 是开发时建表sql mzcms.sql包含测试数据
3、初始账号、密码：fankers/123456789

# 生成密码
yii mzcms/set-pass 123456


4、配置虚拟主机指向/web 默认前台  后台地址：域名+/admin
```

- 目录结构
```
|--application
    |--system      后台
    |--site        前台
|--config      配置文件（公共）
|--data        上传文件存放目录
|--console     命令行
|--docs        开发文档（包含：sql 服务器配置文件）
|--mz          自定义核心文件
|--vender      框架核心
|--web         入口目录
    
```

>图片存储方式：

- 单张图片：存放在每条数据的中
- 多张图片：存放在单独表中

>功能列表

- 分类管理
- 文章管理
- 友情链接
- 关于我们
- 联系我们
- 客户案例
- 网站SEO设置




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)