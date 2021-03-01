PPM Platform -- PPM开源项目开发平台
=======

项目主页： http://www.ppm123.cn

PPM Platform是所有PPM开源项目的开发平台，它是PPM项目业务实现的公共基础，对功能模块，功能场景，前端UI，
工具类等多方面进行了封装，服务于多个PPM开源项目，实现了公用性与代码解耦。

Security权限模型
=======

基于Spring Security框架，采用最佳的用户，角色，资源的权限模型实现的公用权限模块。一个用户可对于多个角色取
权限并集，一个角色定义其可访问的多个资源。实现了对登录控制，Session监控，URL访问控制，菜单访问控制，按钮
操作权限控制等。

Entity实体自动化
=======

PPM自主实现的对实体增删改查自动化处理的场景化封装。从页面都后台业务再到数据库保存，无需任何代码，只需配置
Handler即可，大量减少了代码重复及开发效率。

Attach附件处理
=======

PPM自主实现的附件处理的场景化封装。从页面上传，后台文件处理，单据附件查询、显示，图片查看，文件下载，无需
任何代码。采用JSP 2.0的自定义标签，只需在页面引入标签即可 

Platform工具集
=======

PPM开发过程中积累的工具类集合，从数据库操作，日期处理，Excel数据，上传下载，MD5加密，树遍历等等。

UI前端插件
=======

1. cloud.js  PPM前端小工具的汇总，包含Ajax，滚动条，IFrame自动撑开，信息框，确认框，日期处理，翻页等

2. cloud.ui.tab.js  PPM TAB页签插件

3. cloud.ui.select.js  PPM下拉框插件

4. cloud.fn.validate.js  PPM校验插件

5. stat.chart.js  PPM图表插件

Tags自定义标签
=======

PPM基于JSP 2.0实现的自定义标签，用于在页面上封装公用页面组件，以及进行信息转换。包含附件组件以及日期，时间，
部门，用户等的信息转换。

源码使用
=======

首先下载后从Eclipse导入已存在工程。PPM Platform平台不能单独部署运行，首先确认其主项目比如open-bug，打开
PPM Platform构建文件build.xml，配置ppm-base-dir以及ppm-project-dir。

直接在Ant中双击build.xml即可（运行默认target）。Ant会自动将平台的所有前端，后端代码打包并复制到WEB容器
主项目对应目录下。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)