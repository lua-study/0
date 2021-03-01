# taoke-miaozhuan

#### 项目介绍
``` 
    miaozhuan
``` 
#### 软件架构
``` 
软件架构说明
``` 

####  安装教程
``` 
宝塔安装(系统参数：https://www.bt.cn/Download/btsoftlinux.html）
yum install -y wget && wget -O install.sh http://download.bt.cn/install/install_6.0.sh && sh install.sh

部署文档：
【环境要求】
1.php7.1:需要安装imagemagick拓展库，redis，删除禁用proc、proc_open函数
2.安装进程守护
根目录下执行
【守护进程】
1.redis 队列(处理订单)，推荐supervisor，常驻进程
php think queue:work --queue import_order --daemon

php think queue:listen --queue import_order
【命令行定时任务】
1.导淘宝订单(建议每3-5分钟一次) 每次导的是5分+30秒内的订单
淘宝1(创建时间)：
php think order import --type tb1

淘宝2(结算时间)：
php think order import --type tb2

京东：  (建议半小时或一小时一次) 每次导的是当前这个小时的订单
php think order import --type jd    
       
拼多多：(建议5-10分钟一次)每次导的是10分钟内的订单
php think order import --type pdd        

【发放佣金】建议每天或半天一次
php think order fanli
【url定时任务】
1.创建淘宝订单(建议每3-5分钟一次) 每次导的是5分+30秒内的订单
http://xx.com/index/index/import_order?key=xx00oo113322&type=tb1
2.同步淘宝订单(结算时间)
http://xx.com/index/index/import_order?key=xx00oo113322&type=tb2
3.同步京东订单(建议半小时或一小时一次) 每次导的是当前这个小时的订单
http://xx.com/index/index/import_order?key=xx00oo113322&type=jd
4.同步拼多多订单(建议5-10分钟一次)每次导的是10分钟内的订单
http://xx.com/index/index/import_order?key=xx00oo113322&type=pdd
5.返利同步
http://xx.com/index/index/import_order?key=xx00oo113322&type=fanli




系统参数设置（参考：https://www.kancloud.cn/lileivip/tkygzh/1041135）
需注册帐号：
1.阿里百川：https://baichuan.taobao.com/
2.微信开放平台：https://open.weixin.qq.com/
3.七牛：https://www.qiniu.com/
4.阿里云短信：https://cn.aliyun.com/product/sms
5.阿里妈妈：https://www.alimama.com/index.htm
6.多多进宝：https://ddjb.pinduoduo.com/
7.京东联盟：https://union.jd.com/index
8.极光推送：https://www.jiguang.cn/
9.支付宝商户：https://b.alipay.com/index2.htm


``` 
#### 参与贡献
``` 


``` 
####  码云特技
``` 
1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)
``` 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)