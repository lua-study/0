# SOMS

SOMS自动化运维平台

一直想写个运维平台，无奈前端太差（虽然也不懂开发语言），所以没实现。。

还好有不少人共享了各种各样的平台，其中就有OMS运维平台（binbin开源的OMS平台 链接：https://github.com/binbin91/oms）
所以自己拿来捣鼓，根据自己的需求，也算是写了点东西出来(批量管理、文件管理等)
在公司用了段时间后，更新了些代码，并使用了新模板

gentelella:
https://github.com/puikinsh/gentelella


SOMS演示地址：
http://soms.imaojia.com:8080/

User: somsadmin
Passwd: Imjtest89

组件要求查看requirements.txt


### 安装:

安装必备软件

```
yum -y update && yum -y install mariadb mariadb-devel mariadb-server wget epel-release python-devel gcc c++ make openssl openssl-devel passwd libffi libffi-devel
yum -y install salt-master salt-minion salt-api nginx
wget https://bootstrap.pypa.io/get-pip.py
python get-pip.py
```

配置salt-api

```
pip install pyOpenSSL==0.15.1  -i http://pypi.douban.com/simple/ --trusted-host pypi.douban.com
useradd -M -s /sbin/nologin saltapi && echo "password"|/usr/bin/passwd saltapi --stdin
salt-call --local tls.create_self_signed_cert
```

配置salt-master
我这里把soms解压到了/data/wwwroot下

```
cat > /etc/salt/master <<EOF
interface: 0.0.0.0

external_auth:
  pam:
    saltapi:
      - .*
      - '@wheel'
      - '@runner'
      - '@jobs'

rest_cherrypy:
  port: 8000
  ssl_crt: /etc/pki/tls/certs/localhost.crt
  ssl_key: /etc/pki/tls/certs/localhost.key

file_roots:
  base:
    - /data/wwwroot/soms/media/salt

file_recv: True

include: /data/wwwroot/soms/saltconfig/*.conf
EOF
```

配置好后，把服务启起来，并测试salt-api

```
systemctl start salt-master salt-api
curl -sSk https://localhost:8000/login -H 'Accept: application/x-yaml' -d username=saltapi -d password=password -d eauth=pam
```

返回如下信息则配置成功：

```
return:
- eauth: pam
  expire: 1472695867.308063
  perms:
  - .*
  - '@wheel'
  - '@runner'
  - '@jobs'
  start: 1472652667.308062
  token: 99993ca778fa4f31dce472421cbf01d37be936ad
  user: saltapi
```

上面这些操作都完成后就可以部署soms项目了

安装依赖

pip install -r requirements.txt

同步数据库

python manage.py makemigrations
python manage.py migrate

创建管理员

python manage.py createsuperuser

runserver运行检查是否正常

python manage.py runserver 0.0.0.0:8080

如果无法正常运行，请检查以上步骤

或者email：qqing_lai@hotmail.com

PS:

    soms正常运行后，正式上线最好部署django+nginx+uwsgi环境(http://imaojia.com/blog/linux/django-nginx-uwsgi-setup-on-centos/)


目前SOMS运维平台功能比较简单，代码写的也比较烂，欢迎吐槽 -_-||




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)