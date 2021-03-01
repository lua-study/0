### dingtalk-robot

一个用Java打造的方便钉钉群机器人推送消息的轮子，其实并没有多大的创新，只是把我们常用的一些场景给集成封装了下。设计的时候参考了下面几个开源项目的设计思路

- [小柒2012/spring-boot-webhook](https://gitee.com/52itstyle/spring-boot-webhook)
- [xiaoyixie/spring-boot-dingtalk-robot-starter](https://gitee.com/xiaoyixie/spring-boot-dingtalk-robot-starter)
- [钉钉官方JavaSDK 0.9.0](https://download.alicdn.com/dingtalk-desktop/sdk/dingtalk-chatbot-sdk-0.9.0.zip)

### API文档
- [钉钉官方Wiki文档](https://ding-doc.dingtalk.com/doc#/serverapi2/qf2nxq)
- [本程序API文档，待继续完善](https://apidoc.gitee.com/snowheart/dingtalk-robot/)

### 贡献者列表

- Alex Hu

### HelloWorld

starter工程仅依赖SpringBoot的`spring-boot-autoconfigure`和`spring-boot-starter-web`模块，使用方法同样简单。

1.在pom文件中引入依赖，当前版本`1.0.3.RELEASE`

```        
 
    cn.snowheart 
    spring-boot-dingtalk-robot-starter 
    ${dingtalk-robot-version} 
 
```

2.在application.properties中配置钉钉机器人的WebHook地址
```
dingtalk.robot.access-token=7eb0673858d5b8636cc4189a708517478d3444f25fe887aef73c7bf99756127f
```

3.在应用中注入`DingTalkRobotClient`之后，即可启动调用钉钉机器人的WebHook服务了。

```
@Autowired
private DingTalkRobotClient dingTalkRobotClient;
```

### TODO List
1. 补充完善使用手册及API文档
2. 支持通过配置方式创建多个`DingTalkRobotClient`
3. 完善Demo模块程序，做一个可视化页面
...

### Note
如果你发现了程序BUG或者有其他好的建议，可以通过发邮件[**sxjwzxlwx@yeah.net**]或者Issues的方式联系我，不胜感激。

请以1.0.2.RELEASE版本起使用，1.0.1.RELEASE及之前版本存在引用依赖问题，无法使用。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)