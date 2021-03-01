# CSharp代码规范

- https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/inside-a-program/coding-conventions
# 一、命名规约
## （一）命名风格
1.  【强制】代码中的命名严禁使用拼音与英文混合的方式，更不允许直接使用中文的方式。
说明：正确的英文拼写和语法可以让阅读者易于理解，避免歧义。注意，即使纯拼音命名方式
也要避免采用。
> 正例：test / consume  
> 反例：ceshi / tongbu

2. 【强制】类名使用 UpperCamelCase 风格，必须遵从驼峰形式，但以下情形例外：DO / BO /
DTO / VO / AO  

> 正例：MarcoPolo / UserDO / XmlService / TcpUdpDeal / TaPromotion  
> 反例：macroPolo / UserDo / XMLService / TCPUDPDeal / TAPromotion

3. 【强制】方法名统一使用 UpperCamelCase 风格，必须遵从
驼峰形式。  
> 正例： Fetch / GetUserInfo / ReadWbs  
> 反例： getUserInfo / createReserveNo / buildParameter

4. 【强制】参数名、成员变量、局部变量都统一使用 lowerCamelCase 风格，必须遵从
驼峰形式。  
> 正例：GetApplicatonInfo(int applicationId) / var localInfo / private int sapSystemId  

5. 【强制】常量命名全部大写，单词间用下划线隔开，力求语义表达完整清楚，不要嫌名字长。
> 正例：MAX_STOCK_COUNT  
> 反例：MAX_COUNT

6. 【强制】抽象类命名使用 Abstract 或 Base 开头；异常类命名使用 Exception 结尾；测试类
命名以它要测试的类的名称开始，以 Test 结尾

7. 【强制】中括号是数组类型的一部分，数组定义如下：String[] args;
反例：使用 String args[]的方式来定义。

8. 【强制】杜绝完全不规范的缩写，避免望文不知义。
反例：AbstractClass“缩写”命名成 AbsClass；condition“缩写”命名成 condi，此类随
意缩写严重降低了代码的可阅读性。

9. 【推荐】为了达到代码自解释的目标，任何自定义编程元素在命名时，使用尽量完整的单词
组合来表达其意。  
> 正例：从远程仓库拉取代码的类命名为 PullCodeFromRemoteRepository。  
> 反例：变量 int a; 的随意命名方式。

10. 接口命名以I开头，接口以名词形式出现
> 正例：ISapOperator  
> 反例：ISapOperate

11. 【推荐】如果模块、接口、类、方法使用了设计模式，在命名时体现出具体模式。
说明：将设计模式体现在名字中，有利于阅读者快速理解架构设计理念。
> 正例：  
public class OrderFactory;  
public class LoginProxy;  
public class ResourceObserver;  

12. 【参考】各层命名规约：  
- A) Service/DAO 层方法命名规约
    - 1） 获取单个对象的方法用 Get 做前缀。
    - 2） 获取多个对象的方法用 List 做前缀。
    - 3） 获取统计值的方法用 Count 做前缀。
    - 4） 插入的方法用 Save/Insert 做前缀。
    - 5） 删除的方法用 Remove/Delete 做前缀。
    - 6） 修改的方法用 Update 做前缀。
    - 
- B) 领域模型命名规约
    - 1） 数据对象：xxxDO，xxx 即为数据表名。
    - 2） 数据传输对象：xxxDTO，xxx 为业务领域相关的名称。
    - 3） 展示对象：xxxVO，xxx 一般为网页名称。
    - 4） POJO 是 DO/DTO/BO/VO 的统称，禁止命名成 xxxPOJO。
    

12. 【推荐】一个类一个文件，且文件名与类名保持一至

13. 【推荐】其它补充
    - 尽量保证类，方法，变量的命名的可读性
    - 尽量保证不要用缩写的名称
    - 如果要在变量长度与可读性之间做取舍，优先选择可读性
    - 从别的项目拷贝代码后保证方法名称与当前项目匹配
    - 很多程序员喜欢争论代码风格。别否认哦，类似的话题总能吵起来。Bill Sourour 认为：代码风格没有绝对的对错，只要团队代码风格统一就行了。Bill 觉得比较安全的做法：① 通过工具自动规范代码风格；② 参照名声好的大公司使用的代码风格。
    - 
## （二）常量定义

1.  【推荐】不要使用一个常量类维护所有常量，按常量功能进行归类，分开维护。
> 说明：大而全的常量类，非得使用查找功能才能定位到修改的常量，不利于理解和维护。  
> 正例：缓存相关常量放在类 CacheConsts 下；系统配置相关常量放在类 ConfigConsts 下。

2.  【推荐】常量的复用层次有五层：跨应用共享常量、应用内共享常量、子工程内共享常量、包
内共享常量、类内共享常量。
    - 1） 跨应用共享常量：放置在二方库中，通常是 client.dll 中的 constant 目录下。
    - 2） 应用内共享常量：放置在一方库中，通常是 modules 中的 constant 名称空间下。
    - 3） 子工程内部共享常量：即在当前子工程的 constant 名称空下。
    - 4） 包内共享常量：即在当前项目下单独的 constant 名称称空间下。
    - 5） 类内共享常量：直接在类内部 private static readonly 定义。
    -

## （三）代码格式
1. 【强制】注释的双斜线与注释内容之间有且仅有一个空格。
> 正例：// 注释内容，注意在//和注释内容之间有一个空格。

2. 【推荐】方法体内的执行语句组、变量的定义语句组、不同的业务逻辑之间或者不同的语义
之间插入一个空行。相同业务逻辑和语义之间不需要插入空行。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)