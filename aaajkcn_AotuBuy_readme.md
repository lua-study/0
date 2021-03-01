 AutoBuy 
 
   
 
   
 
   
 


## 安装步骤

首先，将程序克隆到本地：

```
git clone https://github.com/Qsnh/AutoBuy.git
```

安装依赖：

```
composer install
```

复制 `.env` ：

```
cp .env.example .env
```

在 `.env` 环境中配置好数据库等信息。执行：

```
php artisan key:generate
```

设置 `storage` 目录权限：

```
sudo chmod -R 0777 storage
```

安装数据库表：

```
php artisan migrate
```

填充默认数据：

```
php artisan db:seed
```

到这里安装结束。
  
后台地址：http://domain.app/home  
管理员账号密码：  

```
username: auto_buy@admin.com
password: admin123
```

> 如果想要程序完整的运行，还需要进行下面的配置。

## 其它配置

#### 支付配置 

本套系统的支付解决方式来自这一篇文章：[基于有赞云的个人收款即时到帐实现方案](https://laravel-china.org/articles/7014/real-time-account-implementation-scheme-based-on-personal-receipts-with-praise-clouds),您在阅读了上面的文章之后，请配置下 `.env` 文件中的：

```
YOUZAN_CLIENT_ID=
YOUZAN_CLIENT_SECRET=
YOUZAN_KDT_ID=
```

##### 回调地址：

```
http://youdomain.com/payment/notify
```

#### 邮箱配置

请参考：[http://www.cnblogs.com/taotaoxixihaha/p/6650845.html](http://www.cnblogs.com/taotaoxixihaha/p/6650845.html)

#### 定时任务配置

请参考：[https://laravel.com/docs/5.5/scheduling](https://laravel.com/docs/5.5/scheduling)

#### 备份文件云存储

> 考虑到代码基本托管到云平台，所以排除了程序本身的备份，只备份了 `config`, `.env`, `storage` 两个目录和与一个文件！

这里如果我想要将备份的文件存储到七牛云我应该这样配置，修改 `.env` 文件：

```
BACKUP_SAVE_DISK=qiniu

QINIU_DOMAIN=https://qiniu.com(示例)
QINIU_ACCESS_KEY=1
QINIU_SECRET_KEY=2
QINIU_BUCKET=3
```

#### 备份结果通知

```
BACKUP_NOTIFICATION_EMAIL=youemail@email.com
```

> 前提必须要配置好邮箱配置！！！

#### 支付结果实时显示

首先，进入项目根目录中，打开命令行：  

```
npm install -g laravel-echo-server
```

安装成功之后你需要配置项目根目录下的 `laravel-echo-server.json` ：

```
{
	"authHost": "http://autobuy.test:987",
	...
	"port": "6001",
	"protocol": "http",
}
```

请按照自己的环境配置相应选项，默认的 socket.io 的端口是 `6001` ，请注意！如果您是在阿里云服务器使用请注意开通 `6001` 端口！其它云服务商也是！如果您使用的 `https` 协议也请更换！你还需要修改 `.env` 的值：  

```
BROADCAST_DRIVER=redis
QUEUE_DRIVER=redis

REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379
```

你还需要再命令行输入：

```
php artisan queue:work
```

> 如果在生产环境中使用请参考 [https://laravel.com/docs/5.5/queues#supervisor-configuration](https://laravel.com/docs/5.5/queues#supervisor-configuration) 这篇文章，配合 `supervisor` 使用！

最后：

```
laravel-echo-server start
```

为了保证服务的稳定，你可以配合 `supervisor` ,在 `/etc/superviosor/conf.d/` 目录下面创建 `laravel-echoserver.conf` :

```
[program:laravel-echoserver]
process_name=%(program_name)s_%(process_num)02d
command=laravel-echo-server start
autostart=true
autorestart=true
user=root
numprocs=1
redirect_stderr=true
stdout_logfile=/you/project/folder/storage/logs/laravel-echo-server.log
```

注意替换其中的 `user` 的值！！！在命令行输入：

```
sudo supervisorctl reread
sudo supervisorctl update
sudo supervisorctl start laravel-echoserver:*
```

## 帮助

#### 建议一

订单支付回调过程系统需要处理4条任务，其中最耗时的应该就是邮件的发送，但是有赞给回调的时间只有10S，因此考略到这个因素，请使用队列处理来优化这个问题！因为目前系统默认是同步进行的！使用教程：  

修改 `.env` :

```
QUEUE_DRIVER=redis

REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379
```

注意重新启动服务！


## 扩展包

| 扩展包 | 描述 | 应用场景 |
| --- | --- | --- |
| [laracasts/flash](https://github.com/laracasts/flash) | 验证消息，通知消息输出 | 用于表单验证，业务逻辑验证等 |
| [mewebstudio/captcha](https://github.com/mewebstudio/captcha) | 图形验证码 | 图形验证码 |
| [overtrue/laravel-youzan](https://github.com/overtrue/laravel-youzan) | 基于laravel封装的有赞扩展包 | 个人收款解决方案 |
| [rap2hpoutre/laravel-log-viewer](https://github.com/rap2hpoutre/laravel-log-viewer) | laravel日志查看 | laravel日志查看 |
| [yangyifan/upload](https://github.com/yangyifan/upload) | laravel filesystem扩展包 | 七牛，又拍，阿里云，腾讯云等存储服务 |
| [spatie/laravel-backup](https://github.com/spatie/laravel-backup) | 数据备份 | 网站备份，数据库定时备份等 |

## 自定义命令

| 命令 | 描述 |
| --- | --- |
| `password:reset` | 重置管理员密码 |
| `order:query` | 查询最近5条未支付订单的支付情况 |
| `backup:run` | 备份当前网站 |

## 定时任务

| 任务 | 描述 | 周期 |
| --- | --- | --- |
| `order:query` | 查询最近5条(循环重置)未支付订单的支付情况 | 每分钟 |
| `backup:run` | 备份当前网站 | 每天凌晨3:00 |
| `backup:clear` | 清除过期备份 | 每天凌晨4:00 |


## 作者

[轻色年华](https://github.com/Qsnh)

## License

MIT



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)