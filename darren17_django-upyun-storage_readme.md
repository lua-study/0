django-upyun
=============

django storage for [又拍云存储](http://upyun.com)

## INSTALL

```sh
$ pip install django-upyun-storage
```

## USAGE

修改 `settings.py`

```python
UPYUN_BUCKET = "空间名称"
UPYUN_ACCOUNT = "操作员用户名"
UPYUN_PASSWORD = "操作员密码"
STATICFILES_STORAGE = 'django_upyun.storage.UpYunStorage'
```

### 将静态文件上传到又拍云CDN

```sh
$ python manage.py collectstatic
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)