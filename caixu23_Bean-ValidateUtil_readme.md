# Bean-ValidateUtil
一个简洁的基于注解的Bean字段验证工具

用法说明

 @DataValidate(notNull = true,lengthLimit = "{3,5}",type = Long.class)

  private String type1;

  自定义一个验证规则

实现ValidateInterface接口，参照DigitsImpl.java

使用方法

VResult b= BeanValidateUtil.vali2(finalInfo);


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)