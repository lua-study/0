# Django开发知识点

## 将应用放到统一的apps包下

1、首先创建多个应用，之后将应用移到apps目录下
2、在settings文件中进行配置

```python
import sys
import os
BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))
# 加入以下语句
sys.path.insert(0, os.path.join(BASE_DIR, 'apps'))
```

## 扩展官方的User表

1、继承django.contrib.auth.models中的AbstractUser

```python
from django.db import models
from django.contrib.auth.models import AbstractUser
class UserProfile(AbstractUser):
    nickname = models.CharField(max_length=30, default='', verbose_name='昵称')
    birthday = models.DateField(null=True, verbose_name='生日')
    gender = models.CharField(choices=(('male', '男'), ('female', '女')), max_length=6, default='male', verbose_name='性别')
    address = models.CharField(max_length=100, default='', verbose_name='地址')
    mobile = models.CharField(max_length=11, null=True, blank=True, verbose_name='手机号')
    avatar = models.ImageField(upload_to='images/avatar/%Y/%m', default='image/avatar/default.png', max_length=100, verbose_name='头像')

    class Meta:
        verbose_name = '用户信息'
        verbose_name_plural = verbose_name

    def __str__(self):
        return self.username
```

2、在项目的settings文件中加入
```python
AUTH_USER_MODEL = 'users.UserProfile'
# 模块名.模型类名
```

## 将系统的语言改为中国

```python
# 在settings文件中修改如下

# 设置语言
LANGUAGE_CODE = 'zh-hans'
# 设置时区
TIME_ZONE = 'Asia/Shanghai'
# 如果设为True则Django在往数据库存储时间的时候会存储UTC时间
USE_TZ = False
```

## 安装xadmin

1、到github上下载最新的源码包将文件夹中的xadmin拷贝到extra_app文件夹中
并设置extra_app为source_root,并在settings文件中追加包扫描路径
```python
import os
import sys

BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))
sys.path.insert(0, os.path.join(BASE_DIR, 'apps'))
sys.path.insert(1, os.path.join(BASE_DIR, 'extra_app'))
```

2、安装xadmin的相关依赖

```text

django-import-export
six
future
httplib2
django-crispy-forms >=1.6.0 (For xadmin crispy forms)
django-reversion ([OPTION] For object history and reversion feature, please select right version by your django, see changelog )
django-formtools ([OPTION] For wizward form)
xlwt ([OPTION] For export xls files)
xlsxwriter ([OPTION] For export xlsx files)

```

3、将xadmin和crispy-forms配置到settings文件的应用清单中

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    # 注意，一定要放到自己的应用之前，否则无法扫描到自己的应用
    'xadmin',
    'crispy_forms',
    'users',
    'courses',
    'organization',
    'operation'
]
```

4、在urls文件中替换掉原来的路由

```python
from django.conf.urls import url
import xadmin

urlpatterns = [
    url(r'^xadmin/', xadmin.site.urls),
]
```

5、在每个应用中编写adminx.py文件，将模型注入到后台管理中
```python

import xadmin
from .models import EmailVerifyRecord, Banner


class EmailVerifyRecordAdmin(object):
    pass


class BannerAdmin(object):
    pass


xadmin.site.register(EmailVerifyRecord, EmailVerifyRecordAdmin)
xadmin.site.register(Banner, BannerAdmin)
```

## 为xadmin增加主题功能

在任意应用的adminx.py中加入重启服务器即可

```python
import xadmin
from xadmin import views

class BaseSetting(object):
    # 开启主题功能
    enable_themes = True
    # 开启主题选择功能
    use_bootswatch = True
    
xadmin.site.register(views.BaseAdminView, BaseSetting)
```

## 配置xadmin的页头、页脚以及侧边栏的收起

在任意应用的adminx.py中加入重启服务器即可

```python
import xadmin
from xadmin import views
class GlobalSetting(object):
    # 设置页头
    site_title = 'PY学院后台管理系统'
    # 设置页脚
    site_footer = 'PY学院'
    # 设置侧边栏可以收起和展开
    menu_style = 'accordion'
xadmin.site.register(views.CommAdminView, GlobalSetting)
```

## 设置应用名称为中文

1、在每个应用下会有apps.py文件，在下面配置verbose_name

```python
from django.apps import AppConfig


class CoursesConfig(AppConfig):
    name = 'courses'
    verbose_name = '课程管理'

```

2、在当前应用下的__init__.py文件中进行初始化

```python
default_app_config = 'courses.apps.CoursesConfig'
```

## 重载Django中默认的登录验证方法

1、首先建立自定义的验证类

```python
from django.contrib.auth.backends import ModelBackend
from django.db.models import Q
from users.models import UserProfile

# 自定义验方法
class CustomBackend(ModelBackend):
    def authenticate(self, username=None, password=None, **kwargs):
        try:
            # 这里的username可以是手机邮箱等
            user = UserProfile.objects.get(Q(username=username)|Q(email=username))
            if user.check_password(password):
                return user
        except Exception as e:
            return None
```

2、在settings文件中进行配置

```python
# 配置自定义登录验证
AUTHENTICATION_BACKENDS = {
    'users.views.CustomBackend'
}

```

3、进行调用

```python
def post(self, request):
    username = request.POST.get('username')
    password = request.POST.get('password')
    user = authenticate(username=username, password=password)
    if user:
        login(request, user)
        return redirect('/')
    else:
        return render(request, 'login.html', {'error': '用户名或密码错误'})
```

## Django中邮件的发送

1、在settings文件中添加如下配置

```python
EMAIL_HOST = 'smtp.163.com'
EMAIL_PORT = 25
EMAIL_HOST_USER = 'jyx15221613915@163.com'
EMAIL_HOST_PASSWORD = 'password'
EMAIL_USER_TLS = False
EMAIL_FROM = 'jyx15221613915@163.com'
```

2、编写一个发送邮件的工具类

```python
from django.core.mail import send_mail

# 直接调用Django内置发送邮件的方法进行邮件的发送
send_status = send_mail(email_title, email_body,EMAIL_FROM, [email])
```

## Django完成文件上传

1、在model中配置相关的字段
2、在settings文件中进行配置

```python
MEDIA_URL = '/upload/'
MEDIA_ROOT = os.path.join(BASE_DIR, 'upload')
```

## Django中配置上传文件的访问

1、在模板中使用
```python
{{MEDIA_URL}}加上上传文件的路径
```

2、在settings中配置

```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR, 'templates')]
        ,
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
                # 加入以下才能在模板中使用{{MEDIA_URL}}
                'django.template.context_processors.media'
            ],
        },
    },
]
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)