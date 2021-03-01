# android-validate
android轻量级EditText验证框架，支持以下11种验证类型：
- REQUIRED, 是否为空
- EMAIL, 邮箱
- PHONE, 手机号
- REGEX, 正则表达式
- MAX_LENGTH, 最大长度
- MIN_LENGTH, 最小长度
- MAX_VALUE, 最大值
- MIN_VALUE, 最小值
- EQUALS_STRING, 字符串相等
- EQUALS_EDITTEXT, edittext内容相等
- UNIQUE; 唯一性

# gradle配置方式
`compile 'cn.yhq:android-validate:2.0.0'`

# 使用方式
### 1、添加验证器：
```java
ValidateManager validateManager = new ValidateManager();
validateManager.addValidateRequiredItem(editText1, "该项为必填项，不可为空");
validateManager.addValidateEmailItem(editText2, "请输入正确的邮箱");
validateManager.addValidatePhoneItem(editText3, "请输入正确的手机号");
validateManager.addValidateRegexItem(editText4, "^[1-9]\\d*$", "正则表达式不匹配（整数）");
validateManager.addValidateMaxLengthItem(editText5, "该项的长度不可超过5个字符", 5);
validateManager.addValidateMinLengthItem(editText6, "该项的长度不可低于5个字符", 5);
validateManager.addValidateMaxValueItem(editText7, "该项的值不可超过100", 100);
validateManager.addValidateMinValueItem(editText8, "该项的值不可少于100", 100);
validateManager.addValidateEqualsItem(editText9, "该项的值和设定的值不相等", "1");
validateManager.addValidateEqualsItem(editText10, "该项的值和上面的editText的内容不相等", editText9);
List  values = new ArrayList<>();
values.add("1");
validateManager.addValidateUniqueItem(editText11, "输入的值已经存在，请重新输入", values);

```

### 2、开始验证：
```java
 if (validateManager.validate()) {
    Toast.makeText(MainActivity.this, "验证通过", Toast.LENGTH_LONG).show();
 } else {
    Toast.makeText(MainActivity.this, "验证不通过", Toast.LENGTH_LONG).show();
 }
```

### 3、自定义验证处理器
```java
ValidateManager.setValidateHandler(new ValidateManager.IValidateHandler() {
    @Override
    public void onValidateHandler(EditText editText, String validateMessage) {
        Toast.makeText(editText.getContext(), validateMessage, Toast.LENGTH_LONG).show();
    }
});
```

### 4、注册验证器
注意，默认的验证类型为-100 ~ -110，如果不是重新定义这几类的验证器，请不要注册验证类型为-100 ~ -110的验证器，否则会覆盖掉默认的验证器
```java
ValidateManager.register(0, new ValidateManager.IValidator() {
    @Override
    public boolean validate(int validateType, EditText editText, String text, Map  extras) {
        return false;
    }
});
```
```java
validateManager.addValidateItem(editText12, 0, "自定义的验证类型");
 ```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)