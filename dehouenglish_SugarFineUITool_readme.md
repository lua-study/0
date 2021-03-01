# SugarFineUI代码生成工具

#### 介绍
使用sqlsugar+fineui生成数据底层代码和页面代码。包含常用的字符串拼接等工具和网站等

#### 使用手册
> 备用地址  https://www.jianshu.com/p/0901d8dde2c6


#### 演示地址
>   http://1024todo.cn/Admin/Login.aspx


### 本工具简介
使用的SqlSugar 4.X，FineuiPro 框架，生成基本的页面和架构，适用于中小型项目快速开发。建议使用Vs2017，mssql数据库，Framework4.5以上的版本。
##### 关于sqlsugar：[http://www.codeisbug.com/Doc/8](http://www.codeisbug.com/Doc/8)
vs项目引用 ，在nuget中搜索并获取。

##### 关于FineuiPro：
由于版权的问题，请移步到知识星球上获取FineuiPro。[https://wx.zsxq.com/mweb/views/topicdetail/topicdetail.html?topic_id=244445115451141&user_id=48812121128128&share_from=ShareToWechat](https://wx.zsxq.com/mweb/views/topicdetail/topicdetail.html?topic_id=244445115451141&user_id=48812121128128&share_from=ShareToWechat)

###### SugarFineUI项目中，需要自己引用FineuiPro，本文省略此步骤。

> SugarFineUI开源地址 [https://gitee.com/sundayisblue/SugarFineUITool](https://gitee.com/sundayisblue/SugarFineUITool)


### 使用手册

1. 先生成SqlSugar实体。不想直接生成代码到项目中，怕覆盖原有代码，建议生成代码到其他位置，手动加入项目中。
![生成SqlSugar实体](https://gitee.com/uploads/images/2019/0423/184641_01f21ac7_436641.png)


2. 手动将生成的Enties文件放入到项目指定的位置

![Enties文件手动放入项目中](https://gitee.com/uploads/images/2019/0423/184641_353554a8_436641.png)

3. 生成FineuiPro页面代码，如图所示：
* 先在右边的数据库栏，连接数据库，选择要生成的表。 
* 点击生成简单代码按钮，在指定的位置生成代码。
* 可以在下面的显示单页代码按钮，查看生成代码。

![生成FineuiPro页面](https://gitee.com/uploads/images/2019/0423/184641_6c797343_436641.png)

4. admin是fineui代码，Enties是sqlsugar生成的orm实体

![生成的Fineui代码和Enties代码](https://images.gitee.com/uploads/images/2019/0423/094630_517485a4_436641.png)

5. 将admin放入到webTest 项目中(此项目只是用于测试和演示)，并转换为web应用程序。
![将生成的fineui代码放入演示环境](https://images.gitee.com/uploads/images/2019/0423/094630_9a59ed67_436641.png)

6. 运行生成的fineui代码。

![运行代码的演示效果](https://images.gitee.com/uploads/images/2019/0423/094625_e0568fd4_436641.png)


7. 以上步骤是dbfirst，先创建数据库，根据数据结构生成项目数据底层和fineui页面。SugarFineUI 暂时只支持mssql生成代码。如果你想用其他的数据库生成页面代码，请使用[反射实体]功能(又叫ModelFirst功能)，同样先有sqlsugar实体，也就是Enties层。如果你想显示Enties的注释内容，如下图，设置生成注释文件xml。需要重新生成解决方案。


![设置Enties生成注释xml文件](https://gitee.com/uploads/images/2019/0423/184641_9179e3fc_436641.png)

8. 反射实体(ModelFirst) 使用方式：同fineuipro生成代码类似，先反射dll文件，xml非必填。反射成功后，可以生成简单代码，和显示单页代码。步骤参考上面 “生成FineuiPro页面代码” (步骤3)。

![ModelFirst功能页面](https://gitee.com/uploads/images/2019/0423/184641_c8820c0e_436641.png)

### 【字符串操作工具】
> https://gitee.com/sundayisblue/SugarFineUITool/wikis/%E5%9C%A8%E7%BA%BF%E5%B7%A5%E5%85%B7%E4%BD%BF%E7%94%A8%E6%89%8B%E5%86%8C


#### QQ群：275110998  作者QQ:971131282

# 比SugarFineUI高级开发框架，BoYuan框架。只要赞助作者￥200即可获取BoYuan源码，赞助者请加下作者QQ:971131282。
> BoYuan开发框架，功能点更多更强大。实现页面权限或页面+button权限的后台框架，并有完善的异常拦截写入日志功能。
项目为webform开发模式，fineuipro + sqlsugar，简单的service分层架构。
配有代码生成工具和其他利于编程的工具，优秀的编码体验，层次分明，简单易学，从而实现快速开发的目的，适用于中小型项目开发。

boyuan框架，示例
> https://www.jianshu.com/p/dfaf63439744

| BoYuan开发框架捐赠者   |  QQ  |
|  ----  | ----  |
| Dd| 1***654 |
| Sunny  | 2******003 |
| 空气会说谎  | 1******108 |
| 赵*伟  | 1******178 |
| 岐  | 4*****478 |
| XianRen_Vip  | 5****515 |

#### 如果觉得对您有所帮助，欢迎您捐赠

 

 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)