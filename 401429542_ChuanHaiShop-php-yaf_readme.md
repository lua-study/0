
ChuanHaiShop 采用php的yaf内存框架开发，运行速度极快，自身集成orm，使用灵活，sql语句的执行采用sql预处理方式，从根源上避免了sql注入，业务逻辑大量采用行锁，事务，运行稳定。

ChuanHaiShop为b2c版本，但表结构已经设计为多商户，使用者可根据需要方便的自行改造为b2b2c.

产品特征：

  多规格可以设置多价格，规格自定义

  运费支持设置省级运费
  
  产品价格由 金额和积分2部分，积分用来抵扣现金，价格设置支持2位小数
  
  

配置：

1.安装:http://domain/install/index.php

2.环境要求：php>=5.4 (支持php7) yaf最新版即可,开启yaf命名空间

3.微信支付证书位置：\m\weixin\cert\

4.shell服务：php -f /web路径/cmd.php request_uri=/cmd/order/do

 川海软件 

移动端vue版本预览：http://shop.chuanhaisoft.com/mobile/index.html

手机端扫码：

 

浏览器版本预览:   http://shop.chuanhaisoft.com


后台演示：http://demo.chuanhaisoft.com/chuanhai/
用户名:admin 密码:chuanhaisoft

川海即时通讯插件助您整合咨询系统，商家可使用桌面版与用户的web版在线交流，提高订单成交。（websocket通讯，并做了ie低版本兼容）

apache配置： 
apache使用.htaccess即可

nginx 配置：
server { 
  listen ****; 
  server_name  domain.com; 
  root   document_root; 
  index  index.php index.html index.htm; 
 
  if (!-e $request_filename) { 
    rewrite ^/(.*)  /index.php/$1 last; 
  } 
} 

 Lighttpd配置：
 $HTTP["host"] =~ "(www.)?domain.com$" { 
  url.rewrite = ( 
     "^/(.+)/?$"  => "/index.php/$1", 
  ) 
} 

 SAE的配置 (config.yaml)
 
 name: your_app_name 
version: 1 
handle: 
    - rewrite: if(!is_dir() && !is_file() && path ~ "^(.*)$" ) goto "/index.php" 
    
 
 

app端：


 
 
 
 
 
 
移动web端:


 
 
 
 
 
 
 
 
 
 
 


管理端：


 
 
 
 川海app：
 
 客服桌面端截图：
 
 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)