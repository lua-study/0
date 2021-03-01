# 文件管理

#### 介绍
基于SpringBoot+elFinder搭建的私有云盘服务 二次开发（版本v2），  链接
https://gitee.com/52itstyle/spring-boot-CloudDisk

#### 软件架构
```
待补
```
#### 工程结构
``` 
tubang-fileserver-main
├── java
├    ├── com
├    ├    ├── cloud
├    ├    ├    ├── api -- 接口 
├    ├    ├    ├── common -- 公用配置搭建
├    ├    ├    ├── repository -- 存储jpa
├    ├    ├    ├── web -- 控制器
├    ├    ├    ├── Application 启动类
├── resources
├    ├── META-INF
├    ├── sql -- sql
├    ├── static -- 静态资源
├    ├── templates -- html
├    ├── application.yml 配置文件
```
#### 安装教程

1.  注意代码的完成性和配置文件参数的修改（端口/项目路径）
2.  命令打包
    ```
    call mvn clean package install -U -Dmaven.test.skip=true
    ```
3.  把jar cp至指定目录,启动（命令如下），可以在任何存在java 环境下使用建议jdk  7.0 / 1.7 以上使用
    ```
    nohup java -jar > file.log  2>&1 &
    # 可根据实际情况设置
    # -Xms256m 初始堆内存 
    # -Xmx1024m 最大堆内存 
    ```

#### 使用说明

>1. 启动成功后通过配置域名或ip端口访问，
    建议在谷歌浏览器进行访问 
    默认账户: admin 密码：admin
>2. 第三方服务对接上传图片
    [接口说明](http://www.sosoapi.com/pass/apidoc/share/forward.htm?shareKey=413c72db5b34111e5ac30d07fb81b06e)
    密码: 123456
>3. 可搭配nginx反向代理进行图片/文件访问

#### 能做什么

1. 文件以及文件夹新增，删除，移动，重命名
2. 在线打包文件
3. 文件下载、上传
4. 在线预览文件，图片
5. 在线处理图片，文件



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)