# 基于DFA的JAVA敏感词过滤

#### 项目介绍
基于DFA的JAVA敏感词过滤
DFA实现思路如下：
1：DFA采用Map的hash机制，将敏感词单个拆分，以第1个字符为key，其他值依旧使用map相连，形成了大map套用小map。
2：遍历需要过滤的字符串，获取每一个字符，根据get(key)来检测是否为敏感词。

#### 软件架构
软件架构说明


#### 安装教程

1. 下载代码
2. 使用IntelliJ IDEA打开
3. 运行demo


#### 参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)