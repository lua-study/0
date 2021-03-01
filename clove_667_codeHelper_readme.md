[TOC]
# MSP_CODE_HELPER

# 1.项目介绍
MSP项目代码助手  

# 2.软件架构
springboot实现mybatis插件功能 自定义生成想要的类

# 3.使用说明
> application.yml
- 1、配置数据源 `datasource`
> table.properties
- 1、配置表名 `table`
- 2、配置表是否按商户分表 `splitByEnt`
- 3、配置需要生成的各个类的路径  如`provider=com.fingard.rh.fgmsp.transmanage.provider.query`
- 4、配置是否需要统计金额 `needStatistics`
- 5、配置接口地址 `interfaceAddress`
- 6、配置作者 `author`
> 启动
- 1、检查`GenerateFactory`中的`build()`方法
- 2、`init`方法为配置文件项
- 3、具体的`build`方法决定生成的文件
- 4、确认无误后运行`CodeHelperApplicationTests`中的`build()`方法

# 4.参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request

# 5.联系作者
785041502@qq.com
Clove丶
     
# 6.说明文档
springboot 自定义日志图案
http://patorjk.com/software/taag/#p=display&f=X992&t=CodeHelp

# 7.备注
目前尚未完全开发完毕，目前仅生成到service层
```
剩余api、provider、controller以及extBean
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)