# express-study-guide

#### 介绍
express学习指南

#### 学习前的建议
本教程需要你有一些node.js基础知识和对express有一些了解   
[express快速入门](https://developer.mozilla.org/zh-CN/docs/Learn/Server-side/Express_Nodejs)   
[express学习手札](https://gitee.com/bullet/express-study.git)   

#### 安装教程
>mongodb
>>最好安装4.0以上版本,具体的可以自行百度 
 
>项目启动
```
npm install		// 或者 cnpm install,前提需要安装cnpm,不会的百度
npm start		// 默认是http://localhost:3000
```
#### 软件架构

├─bin				//express启动文件   
├─config			//各种配置,比如redis,mysql,mongodb   
├─controllers		        //控制器   
├─logs				//日志   
├─middlewares		        //中间件   
├─models			//数据库模型   
│  ├─connect		        //数据库连接文件   
│  └─schemas		        //数据库文档(mongodb)   
├─node_modules		        //node包   
├─public			//静态资源   
├─routes			//路由   
├─services			//业务处理,可以把controller分解成单一职责文件   
├─utils				//常用的方法   
├─views				//视图   
├─接口文档			//api文档   

#### 哪些收获

1.  路由如何组织
2.  MVC结构如何组织
3.  中间件如何使用
4.  mongoose如何使用
5.  强化es6基础知识

#### 温馨提示
本项目没有前端页面,但是有一个接口文档,读者可以借用postman等其他接口工具进行测试   



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)