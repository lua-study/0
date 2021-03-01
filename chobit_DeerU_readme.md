 
  DeerU 
 
 
   
   
   
 
 
    快速开始  
  &#x2022;
    文档  
  &#x2022;
    插件与主题  
  &#x2022;
    贡献代码  
 

 
   
     
   

   
     
   
 


[DeerU](https://github.com/gojuukaze/DeerU) is a content management system, used for blogs.

DeerU 是一个开源博客系统，它基于Django开发。  

它提供了丰富的json数据接口（需安装[api插件](https://github.com/gojuukaze/deeru_plugin_theme)），前端开发人员可以不依赖Django模板，方便的开发主题，实现前后端分离。
___


依赖
---
* Python 3.5+ -- 安装教程 https://www.ikaze.cn/article/28
* pip 10+
* git
* libjpeg，zlib -- pillow包的依赖 
    - ubuntu: ``apt-get install libjpeg8-dev zlib1g-dev libfreetype6-dev`` 
    - centos: ``yum -y install python-devel zlib-devel libjpeg-turbo-devel`` 



目录
---

* 项目文档 ：[https://deeru.readthedocs.io](https://deeru.readthedocs.io)
* 插件与主题 ：[https://github.com/gojuukaze/deeru_plugin_theme](https://github.com/gojuukaze/deeru_plugin_theme)
* GITHUB ：[https://github.com/gojuukaze/DeerU](https://github.com/gojuukaze/DeerU)
* DEMO ：[https://www.ikaze.cn](https://www.ikaze.cn)
* [安装](#安装)
* [初始化](#初始化)
* [运行](#运行)

安装
---

* 安装之前建议配置虚拟环境

``` bash

    pip install virtualenv
    virtualenv --no-site-packages deeru_env
    source deeru_env/bin/activate
```

* pip安装

```bash
    pip install DeerU
    deeru-admin install deeru

```

* 手动安装

```bash

    git clone -b dev https://github.com/gojuukaze/DeerU.git
    cd DeerU
    pip install -r requirements.txt
    
    # 创建 deeru/settings_local.py , deeru/urls_local.py ，具体参考文档
```

初始化
---

* 运行下面命令初始化项目，注意：如果你更改了数据库的配置，或者修改了主题的静态文件 则需要再次运行初始化

```bash

    cd DeerU # 如果你没进入工程目录先进入
    python manage.py init_deeru
```

运行
---
* 以debug模式运行
```bash
    python manage.py runserver 0.0.0.0:8000

```

license
-------
DeerU使用 [GNU General Public License v3.0 协议](https://github.com/gojuukaze/DeerU/blob/master/LICENSE)
，你可以在遵循此协议的情况下免费使用DeerU

**重要！！**

> 需要注意的是，DeerU本身是免费的，但后台管理使用了富文本编辑器froala，其扩展插件并不免费，你可以在以下链接中查看收费信息：  
>
> https://github.com/froala/django-froala-editor#license  
>
> https://froala.com/wysiwyg-editor/pricing  
>
> 你可以自己更换其他编辑器（参照文档 [富文本编辑器](http://deeru.readthedocs.io/zh_CN/master/user_guide/rich_text_editor.html) ），我也会在之后内置一些富文本编辑器的替代方案 


截图
---
首页

 
文章详情

 
admin
 
admin2
 
手机1
 
手机2
 



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)