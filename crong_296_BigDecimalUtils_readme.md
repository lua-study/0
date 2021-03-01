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
    remain = cal(income).minus(expense);
```    

Other methods currently in this library
------------------------
```java
      is(bigdecimal).eq(four);    // Equal
      is(bigdecimal).gt(two);     // Greater than
      is(bigdecimal).gteq(one);   // Greater than equal
      is(bigdecimal).lt(two);     // Less than
      is(bigdecimal).lteq(two);   // Less than equal
 
      
      cal(bigdecimal).plus(bigdecimal)  // addition
      cal(bigdecimal).minus(bigdecimal)   // subtraction
      cal(bigdecimal).mul(bigdecimal)   // subtraction
      cal(bigdecimal).div(bigdecimal)   // division
      cal(bigdecimal).div(bigdecimal,2)   // division
```
      
      
Currently comparison support only String and BigDecimal:
```java
      is(bigdecimal).eq(bigdecimal);    // BigDecimal and BigDecimal
      is(bigdecimal).eq("1000");        // BigDecimal and String
      is("1000").lt("2000");            // String and String
      is("1000").lt(bigdecimal);        // String and BigDecimal
```
       
Calculation support only String and BigDecimal:
```java
      cal(bigdecimal).minus("500")  // BigDecimal and String
      cal("1000").minus("500")      // String and String
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)