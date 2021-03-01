# database-dictionary

#### 介绍
鉴于企业开发过程中数据字典难维护，我们团队参考阿里云数据库管理中的数据字典展示，进行了一个克隆。当前 4.0 版本支持 MySQL SQLSERVER ORACLE DB2 PG 数据库的数据字典生成，关联您的数据库后，可以自动生成 PDF和markdown 文件格式的数据字典文档,也可以直接运行项目支持在线
同步数据库数据字典，支持在线选择不同的数据库，得到该库相应的所有表信息列表，支持在线PDF文件下载。
码云下载地址：https://gitee.com/cdtrh_group/database-dictionary
官方QQ群：256612400
#### 使用说明
DOCKER镜像：
docker pull 251878350/database-dictionary:v4.0

docker run -itd -p 9998:9998 --name=database-dictionary  251878350/database-dictionary:v4.0

在项目的单元测试用例中，有相关数据库的DEMO。
PDF格式数据字典效果展示如下：
![输入图片说明](https://images.gitee.com/uploads/images/2019/0909/165825_17d123d2_1447662.png "PDF2.png")
直接运行 DataBaseApplication 开启springboot web 启动成功后，访问：http://127.0.0.1:9998/ 就可以进入首页了
在线markdown展示效果如下:
![输入图片说明](https://images.gitee.com/uploads/images/2019/0909/165854_e0c42eb6_1447662.png "WEB.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0909/165904_b0614670_1447662.png "web2.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0909/165915_f047f1b8_1447662.png "v4.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0909/165926_da6ce172_1447662.png "web3.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0909/165938_a32c886e_1447662.png "web4.png")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)