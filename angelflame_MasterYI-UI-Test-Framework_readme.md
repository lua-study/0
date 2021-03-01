# MasterYI UI Test Framework
易大师UI自动化测试框架

 **_当前版本：0.4.1beta_**  
 **_更新日期：2019-01-11_**   


码云地址：https://gitee.com/xuwangcheng/MasterYI-UI-Test-Framework  
更新日志: [易大师UI自动化测试框架-更新日志](https://gitee.com/xuwangcheng/MasterYI-UI-Test-Framework/wikis/pages?title=%E6%9B%B4%E6%96%B0%E6%97%A5%E5%BF%97&parent=)  
框架详细使用说明请参考：https://gitee.com/xuwangcheng/MasterYI-UI-Test-Framework/wikis/pages  

## 项目介绍

![22](https://images.gitee.com/uploads/images/2018/1024/145756_bff03bfc_431003.png "屏幕截图.png") &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![4444](https://images.gitee.com/uploads/images/2018/1024/150236_2e04418c_431003.png "屏幕截图.png")  
`QQ群号：468324085  加群验证：易大师`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`公众号：测试无极之道`  

 

 **基于PageObject模型进行测试代码编程的UI自动化测试框架，元素定位、业务逻辑、测试数据分离;底层由selenium-java框架支持，使用yaml文件定义元素定位和用例执行规则。** 
 
 **主要功能：**  
- [yaml文件定义元素信息，方便阅读、编写和维护](https://gitee.com/xuwangcheng/MasterYI-UI-Test-Framework/wikis/pages?title=%E5%85%83%E7%B4%A0%E5%AE%9A%E4%B9%89&parent=%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)；  
- [基于PageModel模型编写测试业务代码，代码复用性高、易理解，灵活](https://gitee.com/xuwangcheng/MasterYI-UI-Test-Framework/wikis/pages?title=PageModel%E7%B1%BB&parent=%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E);  
- [使用数据工厂生产测试数据，分离业务代码和测试数据](https://gitee.com/xuwangcheng/MasterYI-UI-Test-Framework/wikis/pages?title=%E6%95%B0%E6%8D%AE%E6%A8%A1%E5%9E%8B%EF%BC%88%E6%B5%8B%E8%AF%95%E6%95%B0%E6%8D%AE%E7%94%9F%E6%88%90%EF%BC%89&parent=%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)；
- [默认实现了多款不同的测试报告处理器，用户可实现自定义的报告处理器](https://gitee.com/xuwangcheng/MasterYI-UI-Test-Framework/wikis/pages?title=%E6%B5%8B%E8%AF%95%E6%8A%A5%E5%91%8A%E5%A4%84%E7%90%86%E5%99%A8&parent=%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)；
- 使用yaml定义测试集（测试套件）信息，可组合使用不同测试用例方法，可指定测试报告处理器（可带参数）等；
- [邮件推送测试结果和测试报告附件](https://gitee.com/xuwangcheng/MasterYI-UI-Test-Framework/wikis/pages?title=%E6%B5%8B%E8%AF%95%E6%8A%A5%E5%91%8A%E5%A4%84%E7%90%86%E5%99%A8&parent=%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)；
- [分布式执行](https://gitee.com/xuwangcheng/MasterYI-UI-Test-Framework/wikis/pages?title=%E5%88%86%E5%B8%83%E5%BC%8F%E6%89%A7%E8%A1%8C&parent=%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)；
- [内置定时执行器](https://gitee.com/xuwangcheng/MasterYI-UI-Test-Framework/wikis/pages?title=%E5%AE%9A%E6%97%B6%E6%B5%8B%E8%AF%95%E4%BB%BB%E5%8A%A1&parent=%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)；
- [集成spring boot，可对接任何自动化管理系统或平台，对外提供用例查询、测试执行、报表数据查询等接口](https://gitee.com/xuwangcheng/MasterYI-UI-Test-Framework/wikis/pages?title=API%E6%8E%A5%E5%8F%A3&parent=%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)；
- 同一个测试用例可以在同一次测试中配置不同类型的浏览器进行测试；
- [持久化测试报告数据到sqlite数据库，可通过页面查询历史记录并下载测试报告文件](https://gitee.com/xuwangcheng/MasterYI-UI-Test-Framework/wikis/pages?title=%E6%8C%81%E4%B9%85%E5%8C%96%E6%B5%8B%E8%AF%95%E6%95%B0%E6%8D%AE%E5%88%B0sqlite&parent=%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)
- 封装了验证码识别,文件上传,嵌套frame切换等复杂操作;
- java语言编写，熟悉java编程的可快速上手。


在开发过程中参考了以下优秀的自动化测试框架的某些思路或思想，在此感谢：  
- [Sweetest-小而美的自动化测试框架](https://github.com/tonglei100/sweetest)
- [Bee-有赞测试团队开发的自动化测试框架](https://segmentfault.com/a/1190000015057723)  

框架使用或者借鉴了以下开源工具：
- [功能强大的java工具包Hutool](https://gitee.com/xuwangcheng/hutool)
- [自动化测试报告ZTest](https://github.com/zhangfei19841004/ztest)  


## 环境要求
系统: windows  
jdk >= 1.7    
浏览器： chrome >=68  
ide: Eclipse 

你需要了解以下知识：
-  [java编程基础](https://www.java.com/zh_CN/)   
- [自动化测试框架selenium](http://www.51testing.com/zhuanti/selenium.html) 
- [yaml](https://www.jianshu.com/p/97222440cd08)

## 快速开始
 **通过以下简单的百度搜索示例来了解该框架如何使用：** 
1.  Clone框架代码到本地  

2.  导入到eclipse中为Maven项目 

3. 在项目根目录下的config/element目录下新建baidu.yaml，在此文件中定义相关页面元素的定位规则： 

![baidu.yaml](https://images.gitee.com/uploads/images/2018/1015/180007_24b29a9a_431003.png "屏幕截图.png") 

4. 在com.dcits.test包下新建包baidu.data、baidu.page、baidu.usecase，分别表示测试数据、测试页面、测试用例

![1](https://images.gitee.com/uploads/images/2018/1015/180218_95d5645e_431003.png "屏幕截图.png")

5. 在page包下新建两个PageModel类，类名需要同baidu.yaml中定义的页面名称相同，同时需要继承BasePage类，如下：

![2](https://images.gitee.com/uploads/images/2018/1015/180431_2ba9cc4c_431003.png "屏幕截图.png")

6. 分别在两个PageModel类中定义相关的PageElement对象，对象名称也需要同baidu.yaml定义的元素名称相同：

![3](https://images.gitee.com/uploads/images/2018/1015/180623_faf66970_431003.png "屏幕截图.png")
![4](https://images.gitee.com/uploads/images/2018/1015/180638_790245b7_431003.png "屏幕截图.png")

7. 在PageModel类中定义相关业务方法，如上图

8. 在usecase包下新建Baidu的测试类，新建baidu搜索的测试方法，同时在方法上加上UseCase注解

![5](https://images.gitee.com/uploads/images/2018/1015/180917_84cb0c5e_431003.png "屏幕截图.png")

9. 如图所示，右键Run运行Baidu测试用例

![6](https://images.gitee.com/uploads/images/2018/1015/183344_c4b9926d_431003.png "屏幕截图.png")

10. 下图为测试日志，在根目录下的report目录下会生成一个html报告

![7](https://images.gitee.com/uploads/images/2018/1015/183457_58884c3c_431003.png "屏幕截图.png")
![8](https://images.gitee.com/uploads/images/2018/1022/101939_b5be5809_431003.png "屏幕截图.png")




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)