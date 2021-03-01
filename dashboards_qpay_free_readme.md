###演示编辑
QPay个人免签【支付宝、微信、云闪付】即时到帐API接口版【前后端已全部包含PHP+MYSQL】：

1.支持语音播报，年、月、周、日帐单查寻，支持人工补单，收款帐号启用停用，支付宝无需上传任何二维码收款等等功能

2.收款前端页面，支持所有后台设置、随时关闭任意支付通道，支持配置，在线客户，随时更换发布 LED 滚动跑马灯广告。

3.灵活多变支持任意 多手机、多帐号同时轮寻收款，任意收款码，自动识别，自动支付，实时到帐。

4.前后端已完美对接，就算是新手也能简单自行的搭建，没有依赖性，一次付费终身使用！

5.支付宝、微信、云闪付个人免签支付接口是个系统工程，需要手机端APP、服务器端的完成。

6.零接入成本零支付成本，支付成功率高。安全稳定性强, 手机端APP无需HOOK无需Root，不需要修改官方任何APP。

7.更重要的是:无需资质，无需频繁审核，无需奔波于各大第三方平台，记录账单清晰一目了然。

8.不限行业，实时到账，资金直接到的个人账户、保证商户资金的绝对安全，通道稳定高效，抗投诉抗封！

9.使用方法比官方接口更简单更方便直接，只需按照文档简单接入即可，纯PHP源码任意修改无需担心。

10.前后端已全面支持PC、移动、平板，三端自适应。

测试前端：http://pay.1388com.com:82/       后台管理：http://pay.1388com.com:82/admin          

图片演示:
![输入图片说明](https://images.gitee.com/uploads/images/2019/0509/053253_7936fc7e_2142605.jpeg "在这里输入图片标题")

![输入图片说明](https://images.gitee.com/uploads/images/2019/0509/053320_66faec27_2142605.jpeg "在这里输入图片标题")

![输入图片说明](https://images.gitee.com/uploads/images/2019/0509/093403_3155e1d0_2142605.jpeg "在这里输入图片标题")

日常养号方式：微信\支付宝帐号的养号比较简单，帐号不能只进不出，最好要有收付款操作，用帐号去购买一些商品，点外卖等等.

不要收了款全额提现，尽量留小部分,尽量控制收款的量如一天1-3万后可先暂停收款,这样对帐号会有好处，以免被微信支付宝等公司风控。

############################
使用Qpay通 支付请阅读

简易路由框架开发支持  【apache或nginx 1.12+】+【php5.6-php7.3】+【MYSQL 5.6-5.7】  注意：为静态在文档下面复制,如有不明之处请加QQ 42321851

mysql 和 手机APP 在Mysql-APP目录内  导入qpay.sql 数据配置文件在 config/config.php  |  qpay-app.apk 安装在手机上建议加入安卓机的白名单，免得在后台被杀掉进程。

手机配置地址 http://你的有服务器域名/callpay    手机token 和 后台管理全局配置 key 配置成一致就可以了OK 搭建比较简单 系统没有依赖 上传只要配置了伪静就可以运行了

全套PHP+APP源码牌 Mysql-APP 目录下 qpay-appcode 为安卓的源码

要求：
* PHP 5.6.0+
## 目录说明
工程目录                根目录
├─app                   应用目录
│  ├─controllers        控制器目录
│  ├─models             模块目录
│  ├─views              视图目录
├─config                配置文件目录
├─extend                框架核心目录
|  ├─lib                自动化加载class公共文件
├─static,assets         静态css文件目录
├─index.php             入口文件
```
## 使用
### 1.安装

### 2. 创建数据库

在数据库中创建名为 project 的数据库：

### 3.修改数据库配置文件

打开配置文件 config/config.php ，使之与自己的数据库匹配

```
$config['db']['host'] = 'localhost';
$config['db']['username'] = 'root';
$config['db']['password'] = 'root';
$config['db']['dbname'] = 'qpay';
```

### 4.配置Nginx或Apache
在Apache或Nginx中创建一个站点，把 qpay 设置为站点根目录（入口文件 index.php 所在的目录）。

然后设置单一入口， Apache服务器为静态配置：
```
 
    # 打开Rerite功能
    RewriteEngine On

    # 如果请求的是真实存在的文件或目录，直接访问
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d

    # 如果访问的文件或目录不是真事存在，分发请求至 index.php
    RewriteRule . index.php
 
```
Nginx服务器配置：
```
# location / {
# 重新向所有非真实存在的请求到index.php
## }
```

宝塔Nginx服务器为静态配置：
```
if (!-f $request_filename){
	set $rule_0 1$rule_0;
}
if (!-d $request_filename){
	set $rule_0 2$rule_0;
}
if ($rule_0 = "21"){
	rewrite /. /index.php;
}

```
### 5.测试访问

然后访问站点域名：http://localhost/ 就可以了。
后台管理: http://localhost/admin 

### 声明

购买本系统请一定测试确定好

请勿将系统用于非法业务,合理学习使用

用来进行违反中国法律用户 跟本工作室一切无关

倒卖被发现同上一律停止更新维护

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)