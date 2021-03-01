#AliceSPA
##简介
这是一个通过phalconPHP 与 Angular.js实现的开源SPA（single page application）框架，API服务器与客户端完全分离，响应式客户端，可用于开发web、手机APP等多端项目。集成了支付宝担保交易、天下畅通短信服务。实现了一套用于SPA的SEO机制。
##演示
http://shop.laxalex.net
##安装
###安装 phalconPHP，建议使用最新版本。
###安装gulp
###安装 PHP，建议最新版本。
###下文中的根目录/为AliceSPA所在目录，如K:\proj\web\AliceSPA
###修改php.ini：
always_populate_raw_post_data = -1  (当在windows中）
session.save_path = "（你的session存放路径）" （当在windows中）
###API 服务器

####修改/server/config/config.ini：
[database] 仅对Mysql进行测试  
host = 数据库Domain  
username = 数据库用户名  
password = 数据库密码  
dbname = 数据库名（shop）  

[message] 短信相关，内置对天下畅通的短信支持  
user_id = 客户号码  
account = 账户名  
password = 密码  

[application]  
domain = 服务器Domain  
clientDomain = 客户端Domain
其他不需修改


####支付宝担保交易相关 修改/server/API/alipay/alipay.config.php：
$alipay_config['partner'] = 在担保交易申请时你会获得;   
$alipay_config['seller_email']	= 在担保交易申请时你会获得;  
$alipay_config['key'] = 在担保交易申请时你会获得;  
$alipay_config['notify_url'] = "http://（你的API服务器Domain）/alipay/notify_url";  
$alipay_config['return_url'] = "http://（你的API服务器Domain）/alipay/return_rul";




###客户端
####首先在/下启动gulp
####修改/client/dev/js/app/app.js：
baseUrl : API服务器Domain  
baseAPI : 连接到baseUrl后面，可以为空  
baseData : 'http://(客户端的服务器Domain）/data'  
cnzz_site_id : 当你需要CNZZ统计时填入  
withCredentials : 当客户端与API服务器不在一个Domain中（跨域）时设置为true，否则为false


###nginx配置文件范例：
/nginx.conf.sample

###导入数据库：
/install.sql

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)