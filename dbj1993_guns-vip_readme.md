# Guns企业版

---

## 分支说明

| 分支名称 | 说明  | 长期支持 |
| :---: | :---: | :---: | 
| maseter | 主分支，Guns企业版的核心分支，使用过程中都以master为主 | 是 |
| multi | 多数据源的分支，如果使用多数据源您可参考commit `632c91b9`来集成多数据源配置，也可以通过文档`https://www.stylefeng.cn/doc/guns#/`来查看如何集成 | 否 |
| sso | 集成DCA单点登录服务器的示例，您也可以通过单点登录SSO相关的文档查看如何集成`https://www.stylefeng.cn/doc/sso` | 否 |

**长期支持说明：**长期支持分支是作者长期更新的分支，推荐您的项目都基于长期支持分支之上来做，其他分支是为了实现某些功能的临时分支，不建议项目基于此分支开发。

## 项目模块介绍

为了方便项目之后的升级，现在把项目拆分成了四个模块，guns-base,guns-sys-guns-vip-gen不建议您在此基础上修改上面的任何内容，您修改后可能会升级后出现问题，您的业务代码尽量都在guns-vip-main，或者新建模块进行开发

| 模块名称 | 说明 |
| :---: | :---: |
| guns-base | guns的基础模块 | 
| guns-base-email | 邮件发送模块 | 
| guns-base-sms | 短信发送模块（对接阿里云短信） | 
| guns-base-timers | 分布式任务调度执行器 | 
| guns-sys | guns系统管理的基础业务模块 |
| guns-vip-gen | guns代码生成器模块 |
| guns-vip-main | 主启动模块，也是您的业务的编写的地方 |



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)