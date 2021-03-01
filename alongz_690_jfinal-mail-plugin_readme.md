### 简介
---------------
jfinal-mail-plugin是jfinal的一个邮件发送插件，支持发送普通邮件、与附件邮件，邮件内容支持通过模板生成，同时还支持多个邮件发送源，她继承了Jfinal核心目标“开发迅速，代码量少，学习简单。。。”，只需简单的2行代码即可实现邮件发送！为您节约更多时间，去陪恋人、家人和朋友 :) ，核心代码通过spring-context-support包的邮件模块移植，JavaMailSender对象如何发送邮件可直接参照Spring的邮件发送文档。

###MAVEN导入
```
 
	 cn.fsdev 
	 jfinal-mail-plugin 
	 2.2 
 
```

### 示例
-------------
#### 1、创建邮件配置文件：

> \#邮箱HOST
host=smtp.qq.com
\#协议
protocol=smtp
\#端口
port=465
\#发送邮箱
username=
\#密码
password=
\#权限认证
mail.smtp.auth=true
\#超时时间
mail.smtp.timeout=5000
\#是否是ssl
mail.smtp.ssl.enable=true

#### 2、JFinalConfig中启用插件
> me.add(new MailPlugin(PropKit.use(“mail.properties”).getProperties()));

#### 3、发送内容固定邮件
> 普通邮件：MailKit.send(“收件人”,Arrays.asList(“抄送1″,”抄送2”), “邮件标题”, “邮件内容”);
  附件邮件：MailKit.send(“收件人”,Arrays.asList(“抄送1″,”抄送2”), “邮件标题”, “邮件内容”,Arrays.asList(new File(“附件1”),new File(“附件2”)));

#### 4、发送模板类邮件
插件除了支持内容固定的邮件外，还支撑模板邮件，模板默认使用为Jfinal的IMainRenderFactory的模板
> 普通邮件：
    Map  dataMap = new HashMap ();
    dataMap.put(“var1”, “变量1”);
    dataMap.put(“var2”, “变量2”);
    MailKit.send(“收件人”,Arrays.asList(“抄送1″,”抄送2”), “邮件标题”, “模板路径”,dataMap);

  附件邮件：
    MailKit.send(“收件人”,Arrays.asList(“抄送1″,”抄送2”), “邮件标题”, “模板路径”,dataMap,Arrays.asList(new File(“附件1”),new File(“附件2”)));

#### 5、多个邮件源支持
插件不仅仅支持一个邮件发送源，还可以极速的支持多个邮件发送源
> 1、启动插件是指定发送源名称：me.add(new MailPlugin(“mail2”,PropKit.use(“mail2.properties”).getProperties()));
  2、发送邮件时指定发送源：MailKit.use(“mail2”).send(…);

### 使用环境
-------------
虚拟机环境：JDK1.6+
Jfinal版本：基于2.2编译，理论可支持2.0+

官方网站：[http://www.fsdev.cn/](http://www.fsdev.cn/)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)