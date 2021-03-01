# flsak_demo
python flask demo

- 官方中文文档  http://dormousehole.readthedocs.io/en/latest/
- 官方教程 http://dormousehole.readthedocs.io/en/latest/tutorial/layout.html
- 代码片段 http://flask.pocoo.org/snippets/
## 运行应用

- 在 Linux and Mac 下：
```
export FLASK_APP=flaskr
export FLASK_ENV=development
flask run
```
- 在 Windows 下，使用 set 代替 export ：
```
set FLASK_APP=flaskr
set FLASK_ENV=development
flask run
```

- 在 Windows PowerShell 下，使用 $env: 代替 export ：
```
$env:FLASK_APP = "flaskr"
$env:FLASK_ENV = "development"
flask run
```

## 初始化数据库文件
```
set FLASK_APP=flaskr
set FLASK_ENV=development
flask init-db
```


使用 pip 在虚拟环境中安装项目。

```
pip install -e .
```

这个命令告诉 pip 在当前文件夹中寻找 setup.py 并在 编辑 或 开发 模式下安装。编辑模式是指当改变本地代码后，只需要重新项目。比如改变了项目 依赖之类的元数据的情况下。




## 构建和安装
```
pip install wheel
python setup.py bdist_wheel  # 构建一个 wheel 发行文件
pip install flaskr-1.0.0-py3-none-any.whl
export FLASK_APP=flaskr
flask init-db  # venv/var/flaskr-instance 作为实例文件夹
```


## 环境
```
ubuntu flask 环境配置 https://www.jianshu.com/p/5b73444eb47d
sudo apt-get install python-setuptools
sudo easy_install pip 或 sudo apt-get install python-pip
sudo pip install virtualenv
my_flask root$ virtualenv venv   网站目录下创建虚拟环境
my_flask root$ source venv/bin/activate （进入虚拟环境）
sudo apt-get install build-essential python3.6-dev（安装uWSGI需要的依赖包, 用来编译的）
(venv)my_flask root$ pip install uwsgi
deactivate  退出依赖环境
```

## 服务器配置
https://www.cnblogs.com/zhangjpn/p/6876412.html?utm_source=itdadao&utm_medium=referral

https://jingyan.baidu.com/article/ce43664937ac0a3772afd362.html

https://blog.csdn.net/lileihappy/article/details/79580291

http://uwsgi-docs-zh.readthedocs.io/zh_CN/latest/Nginx.html


> 注意: 备份nginx的default配置后删除, 其它配置才能生效

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)