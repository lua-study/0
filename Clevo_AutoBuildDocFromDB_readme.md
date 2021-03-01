# AutoBuildDocFromDB
使用SQL文件自动生成markdown格式的数据库文档。

## 使用说明

1. 使用git克隆该项目

2. 从数据库中导出sql文件,请尽量导出只有表结构无表数据的sql文件

3. 在项目目录下运行:
`python build.py sql_dir`
其中sql_dir为您的sql文件路径

4. 生成成功的md文件,在项目的md文件夹中,文件名同您的sql文件名

[示例](http://blog.2liang.me/2016/03/06/%E4%BD%BF%E7%94%A8SQL%E6%96%87%E4%BB%B6%E8%87%AA%E5%8A%A8%E7%94%9F%E6%88%90%E6%95%B0%E6%8D%AE%E5%BA%93%E6%96%87%E6%A1%A3/)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)