#

一、介绍


XiaoFeiChatBot 基于开源项目ChatterBot和QQBot而成，是一款QQ聊天机器人


二、安装方法


在 Python 3.4/3.5 下使用，用 pip3 安装：


pip3 install chatterbot hug requests pyqrcode pypng Pillow qqbot


三、使用方法


1.下载mongodb-3.4.2


2.启动 ./mongod --dbpath=/root/aiyun/data/ --logpath=/root/aiyun/logs/mongodb.log --logappend


3.下载附件


4.还原数据库 ./mongorestore -d chatterbot-database bak/chatterbot-database


5.启动 start.sh


6.python3 ai.py


四、更新内容


1.实现QQ聊天机器人私聊


2.只有被群内其他成员 @ 时才会回复


3.增加了定时任务，可以定时向好友或群发消息了


4.更改机器人的数据库为高性能、可扩展、易部署、易使用，存储数据非常方便的MongoDB


5.通过 QQ 执行Linux命令来控制你的电脑，目前这个功能还有待完善


6.把机器人的回复时间改为随机时间，这样看起来更像个人在和你聊天


7.新增图灵机器人词库 20000 多条


五、参考资料


XiaoFeiChatBot 基于以下开源项目：


https://github.com/gunthercox/ChatterBot


https://github.com/pandolia/qqbot


六、问题反馈


有任何问题或建议可以发邮件给我 aiyun@zjzm.wang



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)