#  JetBrainsLicenseServerforPython
>
这是一个Python语言版的JetBrains License Server模拟器，支持python3，兼容python2.7.（本来不打算支持2的，后来感觉对centos7默认的python版本无奈了，改centos7的默认python比改python代码麻烦多了）
>
使用方法
>
安装所需要的如下两个库

``` 
pip3 install rsa
pip3 install flask
```
>
如果python版本位python2
安装库的代码改为
``` 
pip install rsa
pip install flask
```
>
用cd命令切换到JetBrainsLicenseServer.py所在目录
>
linux版运行
``` 
export FLASK_APP=JetBrainsLicenseServer.py
export FLASK_DEBUG=1
flask run --port 8080 --host 0.0.0.0
```
>
windows版运行
``` 
set FLASK_APP=JetBrainsLicenseServer.py
set FLASK_DEBUG=1
flask run --port 8080 --host 0.0.0.0
```
>
本地搭建的服务器地址设置为
``` 
http://localhost:8080
``` 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)