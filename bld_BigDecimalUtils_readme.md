How It Work
------------------------
- Import library to your code:
```java
	import static com.sunchp.utils.math.BigDecimalUtils.*;
```

- Doing comparison:
```java
    if(is(income).lt(amount)) {
      // ....
    }else {
      // ...
    }
```

- Do calculation:
```java
    remain = cal(income).minus(amount).result();
```    

Other methods currently in this library
------------------------
```java
      is(income).eq(amount);    // Equal
      is(income).gt(amount);     // Greater than
      is(income).gteq(amount);   // Greater than equal
      is(income).lt(amount);     // Less than
      is(income).lteq(amount);   // Less than equal
 
      
      cal(income).plus(amount)  // addition
      cal(income).minus(amount)   // subtraction
      cal(income).mul(amount)   // multiply
      cal(income).div(amount)   // division
      cal(income).div(amount,2)   // division
```
      
      
Currently comparison support only String and BigDecimal:
```java
      is(bigdecimal).eq(bigdecimal);    // BigDecimal and BigDecimal
      is(bigdecimal).eq("1000");        // BigDecimal and String
      is("1000").lt(bigdecimal);        // String and BigDecimal
      is("1000").lt("2000");            // String and String
```
       
Calculation support only String and BigDecimal:
```java
      cal(bigdecimal).minus(bigdecimal)  // BigDecimal and BigDecimal
      cal(bigdecimal).minus("500")  // BigDecimal and String
      cal("500").minus(bigdecimal)  // String and BigDecimal
      cal("1000").minus("500")      // String and String
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)