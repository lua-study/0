# jcode

#### 项目介绍
一个灵活的jboot, jfinal项目生成代码maven插件。

#### 软件架构
软件架构说明


#### 安装教程

1. git clone git@gitee.com:aduan/jcode.git
2. cd jcode
3. mvn install

#### 使用说明

1. 配置

```xml
 
     io.jcode 
     codegen 
     1.0-SNAPSHOT 
     
         
             
                 generate 
             
             validate 
         
     
     
         mysql 
         jdbc:mysql://127.0.0.1:3306/demo?useUnicode=true&amp;characterEncoding=utf-8 
         root 
         123456 
         tb_user 
     
 
```

2. 命令行
```
mvn codegen:generate -Dtype=jboot -DbasePackage=cn.demo -DcodeType=ALL -DtablePrefix=tb_ -DexcludeTables=tb_user,tb_product
```

3. xxxx

#### 参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request

#### 参考和引用

> [jboot](https://gitee.com/fuhai/jboot)
    
> [jfinal](https://gitee.com/jfinal)

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