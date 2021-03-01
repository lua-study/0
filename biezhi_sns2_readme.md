#  SNS
1. 请安装并运行rabbitMQ(相关配置在application.properties中)
2. 请安装并运行Redis(相关配置在application.properties中)
3. 相关api请访问/swagger-ui.html

# 使用
1. 上面依赖软件安装和运行完毕后执行FeedApplication即可 Init中的数据会被初始化（项目关闭后数据会消失）
2. 图片上传需要修改QiNiu中的 AK和SK

初始化管理员:
username:fpf
password:fpf

初始化用户:
username:wl
password:wl

username:wd
password:wd

api使用流程
1. 在swagger-ui.html 中 Post 请求 /api/tokens 点击对应格式的json字符串输入账号密码
2. 在/api/me进行用户相关的操作需要在操作时添加token信息(用户id_用户Token)注意用下划线拼接(不要有空格)

3. ![20170719150043953616365.png](http://oivs8obu7.bkt.clouddn.com/20170719150043953616365.png)
4. ![20170719150043958374512.png](http://oivs8obu7.bkt.clouddn.com/20170719150043958374512.png)
5. ![20170719150043961539214.png](http://oivs8obu7.bkt.clouddn.com/20170719150043961539214.png)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)