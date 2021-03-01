# 重磅提醒 :tada: :tada: :tada:
作者开发的基于Vue2.0和Element-ui2.0的后台模板项目([element-admin](https://github.com/yupeng957/element-admin))已发布，欢迎各位试用。

# 安装说明

### 安装环境准备

- 安装 JDK 1.8 以上
- 安装 MySql 5.7 以上
- 安装 Tomcat 7.0 以上

### 安装步骤

1. 下载war包 https://gitee.com/yupeng957/PowerTeam/attach_files
2. 建立数据库
3. 拷贝powerteam-1.0.0.war到tomcat的webapps目录下，并修改powerteam-1.0.0.war为powerteam.war
4. 启动tomcat

### 建立PowerTeam数据库

1. 打开Mysql管理工具(推荐使用 MySQL Workbench)
2. 执行db.sql脚本
3. **可选操作** 执行demo_data.sql演示数据脚本

### 安装PowerTeam

1. 拷贝powerteam-0.0.1.war到tomcat的webapps目录下
2. 找到 tomcat安装目录\webapps\powerteam\WEB-INF\classes\application-powerteam.yml 配置文件
3. 修改datasource.url 中的ip地址和端口和数据库名称(端口默认是**3306**，数据库默认是**powerteam**)
4. 修改datasource.username 数据库用户名
5. 修改datasource.password 数据库密码
6. 启动tomcat

### 运行PowerTeam
访问 http://localhost:8080/powerteam enjoy it! 如果任何问题， **请加入:family:QQ群(466234012)咨询** 
> 默认的管理员帐号为admin 密码为admin


![image](http://git.oschina.net/yupeng957/PowerTeam/raw/master/screenshot/screenshot-1.png?dir=0&filepath=screenshot%2Fscreenshot-1.png&oid=87ac74d500d8eb948b7a07c63880af09ca3be890&sha=66cd3d83db1653c6cee6fbd6b79bbaa6c5ff1005)

![image](http://git.oschina.net/yupeng957/PowerTeam/raw/master/screenshot/screenshot-2.png?dir=0&filepath=screenshot%2Fscreenshot-2.png&oid=b7777ddb9efe91aea5f19b32affde74bccc3ec28&sha=66cd3d83db1653c6cee6fbd6b79bbaa6c5ff1005)

![image](http://git.oschina.net/yupeng957/PowerTeam/raw/master/screenshot/screenshot-3.png?dir=0&filepath=screenshot%2Fscreenshot-3.png&oid=8b590979cd12e840d9c2eabb085f0429837e0499&sha=66cd3d83db1653c6cee6fbd6b79bbaa6c5ff1005)

![image](http://git.oschina.net/yupeng957/PowerTeam/raw/master/screenshot/screenshot-4.png?dir=0&filepath=screenshot%2Fscreenshot-4.png&oid=45e67aade21220c39f14bf9adfea0bad75c91ed5&sha=66cd3d83db1653c6cee6fbd6b79bbaa6c5ff1005)

![image](http://git.oschina.net/yupeng957/PowerTeam/raw/master/screenshot/screenshot-5.png?dir=0&filepath=screenshot%2Fscreenshot-5.png&oid=5877d33960178e58ab29b39c635c226139c92b9f&sha=66cd3d83db1653c6cee6fbd6b79bbaa6c5ff1005)

![image](http://git.oschina.net/yupeng957/PowerTeam/raw/master/screenshot/screenshot-6.png?dir=0&filepath=screenshot%2Fscreenshot-6.png&oid=78efdcb3ffbd777ce46fb5decc887e4558b9d528&sha=66cd3d83db1653c6cee6fbd6b79bbaa6c5ff1005)


### 常见部署问题

1. **tomcat和mysql不在同一台服务器上**

> 请保证mysql服务器的防火墙已开放3306端口(默认端口，如果是其他端口请举一反三)
> 请保证连接mysql的用户名具有外网访问的权限,如果没有请联系mysql管理员授权用户名具备tomcat服务器访问mysql服务器的权限

2. **tomcat绑定80端口**

> 找到 tomcat\conf\server.xml 修改port="80" 重启tomcat

```
 
```

3. **访问路径去掉/powerteam 采用http://localhost:8080访问**

> 找到 tomcat\conf\server.xml 在Host节中加入该行 重启tomcat

```
 
```
修改后

```
 
    ...
     
    ...
 
```

### 捐赠
请作者喝一杯咖啡吧！
![image](https://raw.githubusercontent.com/wiki/yupeng957/element-admin/Pay.png)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)