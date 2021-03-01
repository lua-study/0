# PESCMS Ticket  
![mahua](https://img.shields.io/github/tag/lazyphp/PESCMS-Ticket.svg) ![mahua](https://img.shields.io/github/license/lazyphp/PESCMS-Ticket.svg)      
PESMCS Ticket(下称PT)是一款基于GPLv2协议发布的开源客服工单系统。PT以全新的设计理念，实现一句JS即可嵌入任意页面中，让工单系统变得更加轻便。  
  
## 反馈和建议  
邮箱：sale#pescms.com  
演示地址：[https://ticket.pescms.com](http://ticket.pescms.com)  
反馈问题：[https://www.pescms.com/page/11.html](https://www.pescms.com/page/11.html)  
开发文档：[https://www.pescms.com/d/index](https://www.pescms.com/d/index)  
PESCMS官方QQ 1群：451828934(已满)      
PESCMS官方QQ 2群：496804032      
  
## 运行环境  
PHP 5.6及以上版本  
Mysql 5.5及以上版本  
IE浏览器不保证兼容  
  
## 安装使用  
> * 下载并解压程序至您的HTTP运行环境所在目录。  
> * 没有配置虚拟主机，则访问Public目录。反之，请将虚拟主机目录配置到Public  
> * 根据安装程序填写对应数据，完成软件安装。  

## 快速使用  
登入系统后台--工单模型--创建工单 。创建完毕后，点击'生成JS'按钮。将JS文件保存到本地。最后在任意的页面中，引入如下代码，则可实现您的工单系统。  
  
```html
 
 
     
 
 
 
  
 

  
 
    var ticket = PT.createForm("ticket");
 
 
 
```

## 其他说明  
除了通过一句话引入JS生成工单，本系统支持站内提交工单，且支持登录验证或沿用JS中的匿名方式提交。  

## 界面预览  
  
#### 工单系统首页  
      

#### 提交工单列表  
      
   
#### 提交工单详细页  
      
   
#### 查看工单详细内容以及回复  
      
   
#### 后台首页  
      
   
#### 后台工单列表  
      

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)