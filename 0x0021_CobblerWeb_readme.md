# Cobbler Web

#### 项目介绍
该项目主要是用与 系统推送 与环境推送。

#### 软件架构
python3.6
django
webssh


#### 图片示例
![首页显示](https://gitee.com/nineven/CobblerWeb/raw/master/pic/main.png)
![kickstarts2](https://gitee.com/nineven/CobblerWeb/raw/master/pic/kickstarts2.png)
![kickstart](https://gitee.com/nineven/CobblerWeb/raw/master/pic/kickstarts.png)
![脚本1](https://gitee.com/nineven/CobblerWeb/raw/master/pic/s1.png)
![脚本2](https://gitee.com/nineven/CobblerWeb/raw/master/pic/s2.png)
![脚本3](https://gitee.com/nineven/CobblerWeb/raw/master/pic/s3.png)
![system 设置](https://gitee.com/nineven/CobblerWeb/raw/master/pic/system1.png)
![任务显示](https://gitee.com/nineven/CobblerWeb/raw/master/pic/task1.png)
![任务显示2](https://gitee.com/nineven/CobblerWeb/raw/master/pic/task2.png)


#### 安装教程
```
yum install -y epel-release
yum install -y python36 python36-devel git gcc

cd /opt
python3.6 -m venv py3
source /opt/py3/bin/activate

git clone https://gitee.com/nineven/CobblerWeb.git

cd CobblerWeb 
pip install -r requirements.txt

```
 ```
python manage.py makemigrations
```
```
python manage.py migrate
```

#### 启动服务
```
bash start.sh
# 默认登录信息 admin  nineven.
```

###附录


cobbler 安装 可以参考如下[点击](https://blog.dvcloud.xin/2018/12/04/cobbler-%e6%9c%8d%e5%8a%a1%e6%90%ad%e5%bb%ba%e5%8f%8acobbler-api-%e4%bd%bf%e7%94%a8/) 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)