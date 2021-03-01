# jquery-validate 2.1.1

>适应mvvm，规则可变，多个验证规则组合，不显示的项不验证，只有输入项的正确性验证（ui的改变需要在事件函数中处理）。

##一、规则分类
1. 必须输入；
2. 固定格式：
 - 长度限制； 
 - 数值(整数小数，最大最小值，几位小数)；
 - 电话号码；
 - 身份证；
 - 银行卡；
 - 日期（时间）；
3. ajax验证。

检查顺序按照分类顺序进行。

##二、指令
1. 必须输入：  va-rules = "need";
2. 固定格式：
 -  va-rules = "len(expr)"; //expr 表达式: >0 <=10  
 -  va-rules = "num(expr,decimal)";//decimal 几位小数 大于等于0
 -  va-rules = "telephone";
 -  va-rules = "bankcard"; //银行卡号
 -  va-rules = "idcard"; //身份证号
3. ajax验证：  va-rules = "ajax(url)" va-para="query:aaa,type:0"; //参数(格式key:value)
4. 其他指令
 -  va-name = "姓名";// 提示：姓名不能为空。 没有则通过配置tipsNameSelector取

##三、验证方式
1. 规则1、2在输入时进行校验，实时提醒；
2. 规则1、3在失去焦点时进行验证；
3. 在验证全部的时候，将所有项全部全部规则重新验证一次。


##四、使用介绍
1. 初始化（同时支持AMD加载，和标签引人两种形式）
2. 全局的通用配置（定义一个全局变量vaConfig，在插件初始化的时候会读取该配置
3. 单个表单个性化配置


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)