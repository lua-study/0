# cloud-start

#### 版本说明
打包  
maven clean package install

mvn clean package docker:build


docker build -f Dockerfile -t trade-app:v1.0 .  


docker run -d -p 8093:8093 trade-app:v1.0  

docker logs eager_lichterman  

docker logs objective_swirles --tail 1000 -f



java -jar -Xdebug -Xrunjdwp:transport=dt_socket,server=y,suspend=n,address=5005 springboot-test-1.0-SNAPSHOT.jar


交易服务




#### 参与贡献
1. Fork 本仓库
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


#### 码云特技

1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)