# 高性能EL表达式解析框架 jfireEL

## 使用场景

EL 表达式解析，在一些涉及到动态规则配置的场合使用较多。比如工作流引擎中的外部规则注入，比如 Spring 框架中的 SpEL 解析等等。jfireEL 框架支持常见的 EL 表达式，诸如四则运算，数组元素获取，链表元素获取，Map 键值对获取，属性获取，方法调用，级联调用，支持获取类定义，枚举定义，支持获取对象等等。

相比于 SpringEL，jfireEL 在表达上更为简洁，比如对于 SpringEL，一个变量属性级联对比的表达式可以写为`vars['home'].bool(vars['person'].getAge() + '12' != vars['value'])`，而jfireEL 的写法直接为`home.bool(person.getAge() + '12' != value)`。显然 jfireEL 的可读性更高。

欢迎加入技术交流群186233599讨论交流，也欢迎关注笔者公众号：风火说。
## 性能测试

使用 EL 表达式`vars['home'].bool(vars['person'].getAge() + '12' != vars['value'])`对jfireEL，BeetlEL，SpringEL 三款框架进行性能对比验证。在进入测试之前均预热相同次数确保初始化完毕。三款框架性能对比如下

![](https://markdownpic-1251577930.cos.ap-chengdu.myqcloud.com/20200208145713.png)

## 使用方式

首先引入Maven依赖，如下

```xml
 
     com.jfirer 
     jfireEl 
     1.0 
 
```

在代码中使用时，首先进行EL 表达式的解析，而后使用这个外部参数就可以对表达式进行求值。

```java
int[] array = new int[]
{
    1, 2, 3, 4
};
Map   vars = new HashMap   ();
vars.put("array", array);
Expression lexer = Expression.parse("array[2]");//使用静态方法parse解析字符串形式的EL表达式，得到一个表达式实例。该表达式是一个并发安全的实例，可以供后续反复的并发的调用。一次生成即可，无需反复生成。
assertEquals(3, lexer.calculate(vars));//外部参数通过Map的形式传递。使用方法calculate根据给定的参数计算得到表达式的值
```

在 EL 表达式中，如果一个字符串使用`''`进行包围，则被认为是一个字符串；否则的话，可以被认定为变量名，方法名，参数名，具体某个枚举的名称，视上下文的情况而定。

jfireEL 使用 Map 作为参数的载体，其 Key 的值就是变量名，value 对应的就是变量值。

## 使用示例

具体的代码使用方法可以参见如下示例。

### [] 获取元素支持

jfireEL 支持使用`[]`对数组元素，List，Map进行属性的获取，比如下面的表达式都是正确且合法的。

**获取数组元素**

```java
int[] array = new int[]
{
    1, 2, 3, 4
};
Map   vars = new HashMap   ();
vars.put("array", array);
Expression lexer = Expression.parse("array[2]"); //EL 表达式解析
assertEquals(3, lexer.calculate(vars)); //EL 表达式执行
```

**获取List中元素**

```java
List   list = new ArrayList   ();
list.add("1212");
list.add("13");
Map   vars = new HashMap   ();
vars.put("list", list);
Expression lexer = Expression.parse("list[1]");
assertEquals("13", lexer.calculate(vars));
```

**获取Map键值**

```java
Map   map = new HashMap   ();
map.put("1", "12");
Map   vars = new HashMap   ();
vars.put("map", map);
vars.put("age", "1");
Expression lexer = Expression.parse("map['1']");
assertEquals("12", lexer.calculate(vars));
Expression lexer2 = Expression.parse("map[age]");
assertEquals("12", lexer2.calculate(vars));
```

### 四则运算支持

四则运算，加减乘除，求余的支持如下

```java
Expression lexer = Expression.parse("1+4/2");
assertEquals(3, lexer.calculate(null)); //对于不需要注入参数计算的场合，入参可以直接为null，不影响运算
Expression lexer = Expression.parse("5-(4-1)");
assertEquals(2, lexer.calculate(null));
Expression lexer = Expression.parse("1*2-1");
assertEquals(1, lexer.calculate(null));
```

### 对象属性获取和类属性获取支持

支持使用`.`进行对象属性获取。而如果要获取静态类的属性，支持使用`T(ClassName)`的形式获取静态类，再使用`.`来获取对应的属性。两者的代码如下

```java
public class PropertyTest extends TestSupport
{
    public static int age = 12;
    //对象属性获取
    @Test
    public void test()
        {
            Expression lexer = Expression.parse("home.person.age");
            //home 是一个对象，包含一个对象属性 person，age是person中的一个数字属性
            assertEquals(person.age, lexer.calculate(vars));
            lexer = Expression.parse("home.person.age", Functional.build().setPropertyFetchByUnsafe(true).setRecognizeEveryTime(false).toFunction());
            assertEquals(person.age, lexer.calculate(vars));
        }
        
    //类属性获取
    @Test
    public void test2()
    {
        //PropertyTest 就是测试类本身，使用T()包围表明这是一个类的全限定名
        int result = Expression.parse("T(PropertyTest).age").calculate();
        assertEquals(age, result);
    }
}
```

上面的对象属性获取可以看到，jfireEL 框架**支持级联操作**。

### 三元表达式支持

jfireEL 支持 expression？value1:value2 这种形式的三元表达式，具体代码如下

```java
assertEquals(1, Expression.parse("2>1?1:2").calculate());
assertEquals(1, Expression.parse("3-2+1>1?1:2").calculate());
assertEquals(1, Expression.parse("3-2+1>1?2-1:2").calculate());
assertEquals(2, Expression.parse("3-2+1  vars = new HashMap   ();
Map   param = new HashMap   ();
param.put("b", false);
vars.put("map", param);
assertEquals(2, Expression.parse("map['b']?3:1*2").calculate(vars));
assertEquals(4, Expression.parse("(map['b']?3:2)*2").calculate(vars));
```

### 方法调用获取

方法调用也是使用`.`作为开始符号，和属性获取不同的是，其需要使用`()`作为结束符号，并且可以根据情况，支持入参填入。具体代码如下

```java
Expression lexer = Expression.parse("home.person.getAge()");
assertEquals(person.age, lexer.calculate(vars));
Expression lexer = Expression.parse("home.personAge2(person.getAge()+2)");//方法调用支持入参，并且支持在入参中执行计算
assertEquals(person.getAge() + 2, lexer.calculate(vars));
```

### 枚举类支持

jfireEL 支持获取具体的枚举实例，也获取类属性的方式相同，代码如下

```java
public class EnumTest
{
    enum Name
    {
        dd;
    }

    @Test
    public void test()
    {
        Expression lexer = Expression.parse("T(EnumTest$Name).dd");
        assertEquals(Name.dd, lexer.calculate());
    }
}
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)