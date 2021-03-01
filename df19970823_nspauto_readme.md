# nspauto 自动化测试项目

#### 介绍
niushop 自动化测试项目，包含了 niushop 的 WebUI 自动化测试 和 WebApi 自动化测试方案

#### 软件架构
- 使用 python 作为编程语言

- 使用 pytest 作为测试框架

- 使用 selenium 作为底层的 WebUI 库

- 使用 requests 作为底层的 WebApi 库

- 使用 yaml 作为业务组织的配置文件

- 使用 csv 存储测试用例使用的数据

- 使用 allure 作为报告输出的工具

- 具体的项目结构如下

  ```shell
  nspauto\: pycharm 的项目文件根目录
  |_ .idea\: pycharm 的项目配置目录 
  |_ base\: 底层支持库，可以直接用，一般不需要修改
  	|_ __init__.py: base 包的构造方法
  		|_ build_driver()
  		|_ build_request()
  		|_ Csv
  		|_ Json
  		|_ Path
  		|_ Yaml
  		|_ Db
  		|_ BoxDriver：建议调用的 selenium 底层库
  		|_ BoxRequest：建议调用的 requests 底层库
  		|_ Logger: 建议调用的 logging 底层库，做日志
  	|_ box.py: 底层的库封装
  		|_ _BoxDriver: 封装 selenium 的底层库，不建议直接调用
  		|_ _BoxRequest: 封装 requests 的底层库，不建议直接调用
  	|_ helper.py
  		|_ _CsvHelper
  		|_ _JsonHelper
  		|_ _PathHelper
  		|_ _YamlHelper
  		|_ _DbHelper		
  	|_ infra.py
  		|_ _Logger ：封装的 Logging 底层库
  		
  |_ case\: 测试用例脚本
  	|_ __init__.py: case 包的构造方法
  		|_ WebCase
  		|_ ApiCase
  		|_ _BaseCase: 是上面两个类的基类，不要直接用
  		
  |_ page\: 系统业务组织
  	|_ __init__.py: page 包的构造方法
  		|_ Page
  		|_ Api
  		|_ _BasePage: 是上面两个类的基类，不要直接用
  		
  |_ report\: 报告输出
  	|_ allure\: 存储 allure 的报告源文件
  	|_ log\：存储的 Logger 生成的 日志文件
  |_ usage\: 用法介绍
  |_ install.bat\: 部署使用项目之前，需要运行的 windows 脚本：安装所有的 python 依赖
  |_ main.bat\: 运行测试的脚本
  |_ requirements.txt\: 项目需要的所有 python 依赖
  
  ```

  


#### 安装教程

1. 安装 Python

2. 安装 PyCharm

3. 安装 chromedriver.exe 、geckodriver.exe 至少一个

4. 运行 install.bat

   

#### 使用说明

1. 建议用 fork
3. git clone



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