# 2019-nCoV新型肺炎疫情大数据实时平台
### 作者：eaglet 7488719
### 

#### 目录

- 简介
- 目录结构介绍
- 环境要求
- 初始化环境
- 如何启动
- 一键脚本
- Dockerfile

#### 一、简介
  本程序基于https://gitee.com/e4glet/nodejs_http_framework框架开发，使用nodejs作为中间件，读取腾讯接口数据，实时更新疫情信息。

  提示：本程序为数据演示。

  本开源程序将逐步停止维护，将开设新的项目，数据源以中国CDC为准。
  
程序界面
新增全球疫情数据
![输入图片说明](https://images.gitee.com/uploads/images/2020/0315/022241_e7e89610_1651640.png "屏幕截图.png")

![输入图片说明](https://images.gitee.com/uploads/images/2020/0214/092226_be42a415_1651640.png "屏幕截图.png")

![输入图片说明](https://images.gitee.com/uploads/images/2020/0214/092307_a6daa42c_1651640.png "屏幕截图.png")


#### 二、目录结构介绍
    –bin            项目的底层核心，路由配置文件
	-Controller     控制器目录
    –node_modules   项目中依赖的包
    –public         公共资源放的目录
    –routes         学名 路由，里面放着一些路由文件
    –views          放着就是页面文件了
    –app.js         项目的入口文件。当然你也可以改成其他的名字。
    –package.json    项目版本信息文件
    
#### 三、环境要求
- nodejs 6.0以上版本
- 系统环境：windows/linux/Mac OS
- 开发工具：Sublime Text

###  四、初始化环境
1. 在命令行输入命令;
```c
npm install express -gd
```

2. 最新express4.0版本中将命令工具分家出来了,所以我们还需要安装一个命令工具,命令如下:
```c
npm install -g express-generator
``` 

```c
npm install
``` 

3. NodeJS热部署工具 — supervisor
```c
npm install supervisor -g
```

以上三个命令均为全局安装，其他模块已经包含在项目中


#### 五、如何启动？
以windows系统为例：
打开CMD，进入项目目录
运行npm start

打开浏览器：http://localhost:3000/
即可访问项目。
```c
G:\nodejs\2019-nCoVDataSys>npm start

> 2019-nCoVDataSys@0.0.0 start G:\nodejs\2019-nCoVDataSys
> supervisor ./bin/www


Running node-supervisor with
  program './bin/www'
  --watch '.'
  --extensions 'node,js,/bin/www'
  --exec 'node'

Starting child process with 'node ./bin/www'
Watching directory 'G:\nodejs\2019-nCoVDataSys' for changes.
Press rs for restarting the process.

```

## Docker部署

```c
#提取镜像
FROM mynodeapp
#版本信息
MAINTAINER eaglet
RUN rm -rf /home/www
#设置工作目录
RUN mkdir -p /home/www
WORKDIR /home/www
COPY package.json /home/www
RUN npm i --registry https://registry.npm.taobao.org && npm cache clean && npm install express -gd && npm install -g express-generator && npm install supervisor -g
COPY . /home/www
EXPOSE 3000
CMD [ "npm", "start" ]
```

## 一键脚本
给脚本添加执行权限
```c
chmod +x runapp.sh
```

## 小结
本程序辅助程序，数据来源于腾讯接口。如果你有更好改进建议，欢迎指正。
邮箱：7488719@qq.com

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)