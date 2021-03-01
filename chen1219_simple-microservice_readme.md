>## 这是一个基于SpringCloud的微服务架构项目

>## 部署须知
1. 导入db目录下数据库文件到自己的MySQL服务器
2. 修改配置环境（xxx-service/src/main/resources/application.yml，active值决定启用环境配置文件）
3. 修改连接数据库配置（xxx-service/src/main/resources/application-fat.yml）
4. 修改前端页面连接网关地址（portal-service/src/main/resources/static/js/productList.js和orderList.js）
5. 服务启动顺序：eureka -> mysql -> product,stock,order -> gateway -> portal


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)