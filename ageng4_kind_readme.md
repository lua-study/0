#kind
kind-permission
Spring+SpringMVC+MyBatis+Shiro+MySQL+Redis+Maven+EasyUI+Bootstrap实现的通用权限管理系统 ,参考了一些优秀的开源项目.

### 项目结构

- kind-perm-commmon 项目基础架构,常用工具封装
- kind-perm-core 权限核心逻辑
- kind-perm-web web页面相关
- kind-session 基于redis的分布式session实现
- kind-perm-wx  微信端用户嵌入
- kind-perm-home 首页功能
- kind-perm-api  手机端数据接口

### 技术使用

- spring
- 持久化使用mybatis
- mvc控制使用springmvc
- 页面框架使用easyui+bootstrap
- 数据库mysql，连接池使用druid
- 缓存redis，客户端使用jedis
- JSON工具fast-json

###  特点

- 主要是java核心类库的使用，以及jdk 1.7的一些新特性
- 环境依赖
- 安装jdk 1.7
- 安装Maven3
- 安装MySQL5.5以上版本
- 安装Redis
- 部署说明

###  开发工具
- eclipse

初始化kind-perm-web项目db目录下sql脚本; 说明：导入到数据库后， 默认用户名admin,密码：123456
![输入图片说明](http://git.oschina.net/uploads/images/2017/0307/140100_6c2f64cc_799182.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0307/140112_3b5a4bbd_799182.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0307/140121_dc5f0057_799182.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0307/140132_7a9fb7dc_799182.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0307/140143_d20fbfbc_799182.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0307/140153_122ee0da_799182.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0307/140202_5082f72d_799182.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0307/140211_5c0ff269_799182.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0307/140221_e03747c6_799182.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0307/140230_945b3324_799182.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0307/140238_3ae87edd_799182.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0307/140249_f88828a0_799182.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0307/140258_563911e3_799182.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0307/140313_555520f8_799182.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0307/140330_fddfa130_799182.png "在这里输入图片标题")


###2017-03-06
版本诞生

###2017-03-07
增加了验证码和netty模块

###2017-03-08
netty集成成功，并增加了测试功能

###2017-03-13
代码生成器提交
http://git.oschina.net/zhengzhoujava/kind_generate

###2017-08-31
更新api项目 加入swagger2，
1.jetty 针对不同的jdk版本更改对应的版本
2.jetty 访问由http://127.0.0.1/  更改为http://127.0.0.1/a 
其实我也不想 只是swagger2要求的路径必须有个跟项目 
![输入图片说明](https://git.oschina.net/uploads/images/2017/0831/111418_6dadf0d9_464000.png "1.png")


本团队经营的技术公众号 欢迎小伙伴

![输入图片说明](https://gitee.com/uploads/images/2018/0328/162153_8fff0627_464000.png "屏幕截图.png")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)