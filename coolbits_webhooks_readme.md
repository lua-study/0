Webhooks-git.oschina.net
=================================================================
专为git.oschina.net制作的git钩子服务端。  
服务器需要安装nodejs  
然后把这个项目布置到服务器上。  
npm install  
node app.js  
推荐使用 forever 来后台启动进程.  

##app设置   
//自定义参数  
var password = '123123123'; //提交密码  
var releasewords = 'release'; //发布关键字,只有包含关键字的message才会发布到环境中  


##.sh文件设置   
deploy.sh中  
28行 cd /home/www/$PROJECT_NAME  
/home/www/请修改成自己的项目群目录  
会根据请示地址中p的参数,对这个目录下的参数项目进行git pull  


##PUSH钩子设置   
钩子地址:IP/deploy/?p=项目名字.  
密码:自定义


##其它
提供了简单的提交日志功能
./access.log


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)