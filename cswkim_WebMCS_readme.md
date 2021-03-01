### 关于WebMCS
---
这是一个没啥技术含量的Minecraft服务器网页面板程序

网页服务端使用Java开发，支持Windows,Linux,Mac全平台

鉴于Coding关闭服务，仓库迁到Gitee存放后续版本的开发  

---
### 关于源码

server：软件核心代码，负责提供简易HTTP服务器，提供Ajax接口与和网页端交互控制Minecraft服务端，使用Java开发  
        为了方便玩WebIDE，构建工具选择了Ant，可通过以下命令构建程序  
        `cd server //跳转到server目录`  
        `ant //编译并运行项目`  
        `ant build //编译项目并构建可运行jar`  
        `ant run //不编译直接运行项目(需先编译过项目)`  

web：网页代码，负责整个项目中的网页显示部分，基于BootStrap构建

update：在线更新检测代码，部署在Coding Pages博客中，用于实现版本检测和更新提醒  

docgenerate（已死）： web文档生成器，用于根据JS注释快速生成开发帮助文档（Markdown格式）  
在目录中使用`ant`命令即可根据js自动生成开发文档，开发文档保存在项目根目录下的`webmcs.js API.md`文件中

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)