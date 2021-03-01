## 简介

最简单的spring boot web 示例,message的curd演示操作
没有使用数据库,数据都保持在内存中

因为没有用到数据库,所以可以用来检测服务器java环境是否正确安装
- 使用mvn/mvnw命令打包项目,生成jar文件
- 将jar文件,application配置文件放到服务器目录
- 执行`java -jar xxx.jar`
- 启动成功后浏览页面查看是否正常运行

### 仓库地址

- [github仓库](https://github.com/cschenzz/springboot-web-thymeleaf)
- [gitee仓库](https://gitee.com/chenzz/springboot-web-thymeleaf)

### 打包命令

`mvn clean package -Dmaven.test.skip=true`

`mvnw clean package -Dmaven.test.skip=true`

在powershell和git shell中执行mvnw会提示错误，请使用当前目录执行命令`./mvnw clean package`

### 运行截图

![](screenshot/home.png)
![](screenshot/detail.png)
![接口](screenshot/api-json.png)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)