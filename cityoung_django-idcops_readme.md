# 简介
django-idcops 是一个开源的倾向于数据中心运营商而开发的，拥有数据中心、客户、机柜、设备、跳线、物品、测试、文档等一些列模块的资源管理平台，解决各类资源集中管理与数据可视化的问题。
django-idcops 通过“数据中心”来分类管理每个数据中心下面的资源，每个数据中心均是单独的。

软件许可协议

django-idcops 遵循 Apache License 2.0。


联系

[作者博客](https://www.iloxp.com)

Email: 294060408@qq.com

QQ群：185964462
[数据中心运维管理idcops](https://jq.qq.com/?_wv=1027&k=5SVIbPP)

##### 微信公众号:

![weixin_qrcode](https://gitee.com/wenvki/django-idcops/raw/master/screenshots/qrcode_for_weixin.jpg)

#### 项目截图：

[演示地址](http://idcops.iloxp.com/) 按需要进行重置网站测试数据

用户 / 密码： admin / admin123

![仪表盘](https://gitee.com/wenvki/django-idcops/raw/master/screenshots/2018-12-25_173535.jpg)

[部署线上生产环境](https://www.iloxp.com/archive/2390/)

# 快速开始

#### 一、安装：

**传统方式安装**

centos 安装virtualenv: sudo yum install -y python-virtualenv

Ubuntu 安装virutalenv: sudo apt install -y python-virtualenv

```
cd $HOME
git clone https://gitee.com/wenvki/django-idcops.git
cd django-idcops

virtualenv -p `which python3` env # python3虚拟环境，仅支持python3+
source env/bin/activate # 激活python虚拟环境
pip install -U pip -i https://mirrors.aliyun.com/pypi/simple/ # 升级pip
pip install -r requirements.txt -i https://mirrors.aliyun.com/pypi/simple/ 
python manage.py migrate
python manage.py createsuperuser --username admin
# 按提示创建一个超级管理员admin用户和密码
python manage.py runserver 0.0.0.0:8000 # 以django开发服务器运行软件
# 访问http://127.0.0.1:8000/
```

**docker-compose方式运行**
需要安装docker和docker-compose
```
git clone https://gitee.com/wenvki/django-idcops.git
cd django-idcops
docker-compose build
docker-compose up -d
docker-compose exec -T idcops python manage.py collectstatic --noinput
docker-compose exec -T idcops python manage.py migrate
docker-compose exec idcops python manage.py createsuperuser --username admin
# 按提示创建一个超级管理员admin用户和密码
# 访问http://127.0.0.1:8000/
```

#### 二、初始化配置：

1、访问 http://your_ip:8000/
![login](https://gitee.com/wenvki/django-idcops/raw/master/screenshots/0001.png)


2、首次使用，系统还没有数据中心，需新建一个数据中心
![create idc](https://gitee.com/wenvki/django-idcops/raw/master/screenshots/0002.png)


3、自动重定向到首页 http://your_ip:8000/
![visit index](https://gitee.com/wenvki/django-idcops/raw/master/screenshots/0003.png)



#### 三、配置settings.py `~/mysite/idcops_proj/idcops_proj/settings.py`：

```
STATIC_URL = '/static/'

STATIC_ROOT = os.path.join(BASE_DIR, 'static')

MEDIA_URL = '/media/'

MEDIA_ROOT = os.path.join(BASE_DIR, 'media')

AUTH_USER_MODEL = 'idcops.User'

# idcops options

SOFT_DELELE = True

COLOR_TAGS = True

COLOR_FK_FIELD = False

```


# 说明与项目截图

#### 模块说明：

```
[
('syslog', 'log entries'), # 日志记录，核心内容，用于报表统计，日志分析等
('user', '用户信息'),
('idc', '数据中心'),  
('option', '机房选项'), # 机房选项，核心内容 ，系统元数据
('client', '客户信息'),
('rack', '机柜信息'),
('unit', 'U位信息'),
('pdu', 'PDU信息'),
('device', '设备信息'),
('online', '在线设备'),
('offline', '下线设备'),
('jumpline', '跳线信息'),
('testapply', '测试信息'),
('zonemap', '区域视图'),
('goods', '物品分类'),
('inventory', '库存物品'),
('document', '文档资料')
]
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)