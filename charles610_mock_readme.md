# Mock
Mock是一个Java实现的，可以模拟任何数据的框架。

# Mock来源

公司技术架构为前后台分类开发，在后端接口没有完成时需要返回模拟数据，测试时也需要模拟数据，于是需要一个可以模拟任意数据的工具，企业开发种从头写自己实现是不现实的，太浪费时间，于是github找了一个适合的进行修改，于是有了现在的mock。

修改自jsonzou的[jmockdata](https://github.com/jsonzou/jmockdata)

再次感谢大佬的源代码，阅读收益良多，也帮我快速解决了数据模拟的问题https://github.com/jsonzou/jmockdata

## 特色
* 支持丰富多样的数据类型模拟，包括：Java基本类型、字符串、枚举、日期、数组、多维数组、集合[List|Set|Map]、枚举、Java对象等
* 支持泛型
* 支持继承
* 支持循环依赖、自依赖(手动开启enabledCircle)
* 支持忽略字段
* 支持改变mockConfig来自定义模拟数据策略
* 支持JDK1.8+，无任何第三方依赖
* 源代码仅有60K，很小


### 基础类型

支持以下基础类型直接模拟

| 描述     | 类型                                       |
| ------ | ---------------------------------------- |
| 基础类型   | ```byte```     ```boolean```     ```char```     ```short```     ```int```     ```long```     ```float```     ```double``` |
| 包装类型包装 | ```Byte```     ```Boolean```     ```Character```     ```Short```     ```Integer```     ```Long```     ```Float```     ```Double``` |
| 常用类型   | ```BigDecimal```        ```BigInteger```        ```Date```        ```String```      枚举 |
| 自定义类型   | 自定义的任意class，同时支持class的互相嵌套，自嵌套，继承 等等类型 |
| 多维数组   | 以上所有类型的多维数组  如：```int[]```      ```int[][]```  ```int[][][]```  .... 等 |

## 快速启动
```java
T t = Mock.mock(T.class);
```

T可以是任意类型，如果T带有泛型，比如T为List ，那么使用如下方式
    
```java
T t = Mock.mock(new TypeKit >() {});
```
TypeKit是一个封装类，目的是封装要获取的泛型类型

其他使用方式，高级模拟方式以及详细使用参考测试代码（标注Maven工程的test包下）

## 详细使用
###基本类型，常用类型，集合（List,Set,Map）类型以及其多维数组类型
```java
    /**
      * java基本类型模拟测试
      */
    @Test
    public void testBasic() {
        //基本类型模拟
        byte byte1 = Mock.mock(byte.class);
        System.err.println(byte1);

        short short1 = Mock.mock(short.class);
        System.err.println(short1);

        int int1 = Mock.mock(int.class);
        System.err.println(int1);

        long long1 = Mock.mock(long.class);
        System.err.println(long1);

        double double1 = Mock.mock(double.class);
        System.err.println(double1);

        float float1 = Mock.mock(float.class);
        System.err.println(float1);

        char char1 = Mock.mock(char.class);
        System.err.println(char1);

        boolean boolean1 = Mock.mock(boolean.class);
        System.err.println(boolean1);

        //基本类型封装类模拟
        Byte byte2 = Mock.mock(Byte.class);
        System.err.println(byte2);

        Short short2 = Mock.mock(Short.class);
        System.err.println(short2);

        Integer int2 = Mock.mock(Integer.class);
        System.err.println(int2);

        Long long2 = Mock.mock(Long.class);
        System.err.println(long2);

        Double double2 = Mock.mock(Double.class);
        System.err.println(double2);

        Float float2 = Mock.mock(Float.class);
        System.err.println(float2);

        Character char2 = Mock.mock(Character.class);
        System.err.println(char2);

        Boolean boolean2 = Mock.mock(Boolean.class);
        System.err.println(boolean2);

        //常用类型模拟
        //字符串
        String string = Mock.mock(String.class);
        System.err.println(string);
        //大精度
        BigDecimal bigDecimal = Mock.mock(BigDecimal.class);
        System.err.println(bigDecimal);
        //大整形
        BigInteger bigInteger = Mock.mock(BigInteger.class);
        System.out.println(bigInteger);
        //日期
        Date date = Mock.mock(Date.class);
        System.out.println(date);
        //枚举
        DayEnum dayEnum = Mock.mock(DayEnum.class);
        System.out.println(dayEnum);
    }

    /**
     * 基本类型的数组类型模拟测试
     */
    @Test
    public void testArray() {

       //基本类型 数组 模拟
        byte[] byte1 = Mock.mock(byte[].class);
        System.err.println(JsonUtil.toStr(byte1));//byte转json 这里做了new string 打印是string
        //循环打印出来
        for (byte b:byte1){
            System.out.println(b);
        }

        short[] short1 = Mock.mock(short[].class);
        System.err.println(JsonUtil.toStr(short1));

        int[] int1 = Mock.mock(int[].class);
        System.err.println(JsonUtil.toStr(int1));

        long[] long1 = Mock.mock(long[].class);
        System.err.println(JsonUtil.toStr(long1));

        double[] double1 = Mock.mock(double[].class);
        System.err.println(JsonUtil.toStr(double1));

        float[] float1 = Mock.mock(float[].class);
        System.err.println(JsonUtil.toStr(float1));

        char[] char1 = Mock.mock(char[].class);
        System.err.println(JsonUtil.toStr(char1));

        boolean[] boolean1 = Mock.mock(boolean[].class);
        System.err.println(JsonUtil.toStr(boolean1));

        //基本类型封装类模拟
        Byte[] byte2 = Mock.mock(Byte[].class);
        System.err.println(JsonUtil.toStr(byte2));

        Short[] short2 = Mock.mock(Short[].class);
        System.err.println(JsonUtil.toStr(short2));

        Integer[] int2 = Mock.mock(Integer[].class);
        System.err.println(JsonUtil.toStr(int2));

        Long[] long2 = Mock.mock(Long[].class);
        System.err.println(JsonUtil.toStr(long2));

        Double[] double2 = Mock.mock(Double[].class);
        System.err.println(JsonUtil.toStr(double2));

        Float[] float2 = Mock.mock(Float[].class);
        System.err.println(JsonUtil.toStr(float2));

        Character[] char2 = Mock.mock(Character[].class);
        System.err.println(JsonUtil.toStr(char2));

        Boolean[] boolean2 = Mock.mock(Boolean[].class);
        System.err.println(JsonUtil.toStr(boolean2));

        //常用类型 数组 模拟
        //字符串
        String[] string = Mock.mock(String[].class);
        System.err.println(JsonUtil.toStr(string));
        //大精度
        BigDecimal[] bigDecimal = Mock.mock(BigDecimal[].class);
        System.err.println(JsonUtil.toStr(bigDecimal));
        //大整形
        BigInteger[] bigInteger = Mock.mock(BigInteger[].class);
        System.out.println(JsonUtil.toStr(bigInteger));
        //日期
        Date[] date = Mock.mock(Date[].class);
        System.out.println(JsonUtil.toStr(date));
        //枚举
        DayEnum[] dayEnum = Mock.mock(DayEnum[].class);
        System.out.println(JsonUtil.toStr(dayEnum));
    }


    /**
     * 基本类型的二维数组模拟测试
     */
    @Test
    public void testArray2() {

        //基本类型 二维数组 模拟
        byte[][] byte1 = Mock.mock(byte[][].class);
        System.err.println(JsonUtil.toStr(byte1));//byte转json 这里做了new string 打印是string

        short[][] short1 = Mock.mock(short[][].class);
        System.err.println(JsonUtil.toStr(short1));

        int[][] int1 = Mock.mock(int[][].class);
        System.err.println(JsonUtil.toStr(int1));

        long[][] long1 = Mock.mock(long[][].class);
        System.err.println(JsonUtil.toStr(long1));

        double[][] double1 = Mock.mock(double[][].class);
        System.err.println(JsonUtil.toStr(double1));

        float[][] float1 = Mock.mock(float[][].class);
        System.err.println(JsonUtil.toStr(float1));

        char[][] char1 = Mock.mock(char[][].class);
        System.err.println(JsonUtil.toStr(char1));

        boolean[][] boolean1 = Mock.mock(boolean[][].class);
        System.err.println(JsonUtil.toStr(boolean1));

        //基本类型封装类模拟
        Byte[][] byte2 = Mock.mock(Byte[][].class);
        System.err.println(JsonUtil.toStr(byte2));

        Short[][] short2 = Mock.mock(Short[][].class);
        System.err.println(JsonUtil.toStr(short2));

        Integer[][] int2 = Mock.mock(Integer[][].class);
        System.err.println(JsonUtil.toStr(int2));

        Long[][] long2 = Mock.mock(Long[][].class);
        System.err.println(JsonUtil.toStr(long2));

        Double[][] double2 = Mock.mock(Double[][].class);
        System.err.println(JsonUtil.toStr(double2));

        Float[][] float2 = Mock.mock(Float[][].class);
        System.err.println(JsonUtil.toStr(float2));

        Character[][] char2 = Mock.mock(Character[][].class);
        System.err.println(JsonUtil.toStr(char2));

        Boolean[][] boolean2 = Mock.mock(Boolean[][].class);
        System.err.println(JsonUtil.toStr(boolean2));

        //常用类型 数组 模拟
        //字符串
        String[][] string = Mock.mock(String[][].class);
        System.err.println(JsonUtil.toStr(string));
        //大精度
        BigDecimal[][] bigDecimal = Mock.mock(BigDecimal[][].class);
        System.err.println(JsonUtil.toStr(bigDecimal));
        //大整形
        BigInteger[][] bigInteger = Mock.mock(BigInteger[][].class);
        System.out.println(JsonUtil.toStr(bigInteger));
        //日期
        Date[][] date = Mock.mock(Date[][].class);
        System.out.println(JsonUtil.toStr(date));
        //枚举
        DayEnum[][] dayEnum = Mock.mock(DayEnum[][].class);
        System.out.println(JsonUtil.toStr(dayEnum));
    }

    /**
     * 基本类型的多维数组测试
     */
    @Test
    public void testArray3() {
        //基本类型 三维数组 模拟
        byte[][][] byte1 = Mock.mock(byte[][][].class);
        System.err.println(JsonUtil.toStr(byte1));//byte转json 这里做了new string 打印是string

        short[][][] short1 = Mock.mock(short[][][].class);
        System.err.println(JsonUtil.toStr(short1));

        int[][][] int1 = Mock.mock(int[][][].class);
        System.err.println(JsonUtil.toStr(int1));

        long[][][] long1 = Mock.mock(long[][][].class);
        System.err.println(JsonUtil.toStr(long1));

        double[][][] double1 = Mock.mock(double[][][].class);
        System.err.println(JsonUtil.toStr(double1));

        float[][][] float1 = Mock.mock(float[][][].class);
        System.err.println(JsonUtil.toStr(float1));

        char[][][] char1 = Mock.mock(char[][][].class);
        System.err.println(JsonUtil.toStr(char1));

        boolean[][][] boolean1 = Mock.mock(boolean[][][].class);
        System.err.println(JsonUtil.toStr(boolean1));

        //基本类型封装类模拟
        Byte[][][] byte2 = Mock.mock(Byte[][][].class);
        System.err.println(JsonUtil.toStr(byte2));

        Short[][][] short2 = Mock.mock(Short[][][].class);
        System.err.println(JsonUtil.toStr(short2));

        Integer[][][] int2 = Mock.mock(Integer[][][].class);
        System.err.println(JsonUtil.toStr(int2));

        Long[][][] long2 = Mock.mock(Long[][][].class);
        System.err.println(JsonUtil.toStr(long2));

        Double[][][] double2 = Mock.mock(Double[][][].class);
        System.err.println(JsonUtil.toStr(double2));

        Float[][][] float2 = Mock.mock(Float[][][].class);
        System.err.println(JsonUtil.toStr(float2));

        Character[][][] char2 = Mock.mock(Character[][][].class);
        System.err.println(JsonUtil.toStr(char2));

        Boolean[][][] boolean2 = Mock.mock(Boolean[][][].class);
        System.err.println(JsonUtil.toStr(boolean2));

        //常用类型 数组 模拟
        //字符串
        String[][][] string = Mock.mock(String[][][].class);
        System.err.println(JsonUtil.toStr(string));
        //大精度
        BigDecimal[][][] bigDecimal = Mock.mock(BigDecimal[][][].class);
        System.err.println(JsonUtil.toStr(bigDecimal));
        //大整形
        BigInteger[][][] bigInteger = Mock.mock(BigInteger[][][].class);
        System.out.println(JsonUtil.toStr(bigInteger));
        //日期
        Date[][][] date = Mock.mock(Date[][][].class);
        System.out.println(JsonUtil.toStr(date));
        //枚举
        DayEnum[][][] dayEnum = Mock.mock(DayEnum[][][].class);
        System.out.println(JsonUtil.toStr(dayEnum));
    }
   
```
### 任意类型
```java
 /**
     * 任意类型
     * 注意TypeReference要加{}才能模拟
     */
    @Test
    public void testTypeRefrence() {
        //模拟基础类型，不建议使用这种方式，参考基础类型章节直接模拟。
        Integer integerNum = Mock.mock(new TypeKit () {
        });
        System.err.println(JsonUtil.toStr(integerNum));
        Integer[] integerArray = Mock.mock(new TypeKit () {
        });
        System.err.println(JsonUtil.toStr(integerArray));
        //模拟集合
        List  integerList = Mock.mock(new TypeKit >() {
        });
        System.err.println(JsonUtil.toStr(integerList));
        //模拟数组集合
        List  integerArrayList = Mock.mock(new TypeKit >() {
        });
        System.err.println(JsonUtil.toStr(integerArrayList));
        //模拟集合数组
        List [] integerListArray = Mock.mock(new TypeKit []>() {
        });
        System.err.println(JsonUtil.toStr(integerListArray));
        //模拟集合实体
        List  basicBeanList = Mock.mock(new TypeKit >() {
        });
        System.err.println(JsonUtil.toStr(basicBeanList));
        //各种组合忽略。。。。map同理。下面模拟一个不知道什么类型的map
        Map >, Map , Double[]>> some = Mock
                .mock(new TypeKit >, Map , Double[]>>>() {
                });
        System.err.println(JsonUtil.toStr(some));
    }
```

### JAVA对象类型

- 模拟bean，被模拟的数据必须是plain bean，底层采用了java自带的内省方法来获取字段和对应的setter方法。

- 支持模拟继承而来的属性。

```java
//模拟Java对象
public class BasicBean {

    //基本类型
    private byte byteNum;
    private boolean booleanNum;
    private char charNum;
    private short shortNum;
    private int integerNum;
    private long longNum;
    private float floatNum;
    private double doubleNum;

    //基本包装类型
    private Byte byteBoxing;
    private Boolean booleanBoxing;
    private Character charBoxing;
    private Short shortBoxing;
    private Integer integerBoxing;
    private Long longBoxing;
    private Float floatBoxing;
    private Double doubleBoxing;

    //基本类型数组
    private byte[] byteNumArray;
    private boolean[] booleanNumArray;
    private char[] charNumArray;
    private short[] shortNumArray;
    private int[] integerNumArray;
    private long[] longNumArray;
    private float[] floatNumArray;
    private double[] doubleNumArray;

    //基本类型二维数组
    private byte[][] byteNumDoubleArray;
    private boolean[][] booleanNumDoubleArray;
    private char[][] charNumDoubleArray;
    private short[][] shortNumDoubleArray;
    private int[][] integerNumDoubleArray;
    private long[][] longNumDoubleArray;
    private float[][] floatNumDoubleArray;
    private double[][] doubleNumDoubleArray;

    //基本包装类型数组
    private Byte[] byteBoxingArray;
    private Boolean[] booleanBoxingArray;
    private Character[] charBoxingArray;
    private Short[] shortBoxingArray;
    private Integer[] integerBoxingArray;
    private Long[] longBoxingArray;
    private Float[] floatBoxingArray;
    private Double[] doubleBoxingArray;

    //基本包装类型二维数组
    private Byte[][] byteBoxingDoubleArray;
    private Boolean[][] booleanBoxingDoubleArray;
    private Character[][] charBoxingDoubleArray;
    private Short[][] shortBoxingDoubleArray;
    private Integer[][] integerBoxingDoubleArray;
    private Long[][] longBoxingDoubleArray;
    private Float[][] floatBoxingDoubleArray;
    private Double[][] doubleBoxingDoubleArray;

    //其他常用类型
    private BigDecimal bigDecimal;
    private BigInteger bigInteger;
    private Date date;
    private String string;
    private DayEnum dayEnum;
    private TimeUnit timeUnit;

    //其他常用类型数组
    private BigDecimal[] bigDecimalArray;
    private BigInteger[] bigIntegerArray;
    private Date[] dateArray;
    private String[] stringArray;
    private DayEnum[] dayEnumArray;

    //其他常用类型二维数组
    private BigDecimal[][] bigDecimalDoubleArray;
    private BigInteger[][] bigIntegerDoubleArray;
    private Date[][] dateDoubleArray;
    private String[][] stringDoubleArray;
    private DayEnum[][] dayEnumDoubleArray;

    //集合、MAP数组
    private List [] listArray;
    private Set [] setArray;
    private Map [] mapArray;

    //集合、MAP二维数组
    private List [][] listDoubleArray;
    private Set [][] setDoubleArray;
    private Map [][] mapDoubleArray;

    //集合、MAP二维数组(内部数组)
    private List [][] listInnerArrayDoubleArray;
    private Set [][] setInnerArrayDoubleArray;
    private Map [][] mapInnerArrayDoubleArray;

    //集合、MAP二维数组(内部二维数组)
    private List [][] listInnerDoubleArrayDoubleArray;
    private Set [][] setInnerDoubleArrayDoubleArray;
    private Map [][] mapInnerDoubleArrayDoubleArray;

    //LIST
    private List  byteBoxingList;
    private List  booleanBoxingList;
    private List  charBoxingList;
    private List  shortBoxingList;
    private List  integerBoxingList;
    private List  longBoxingList;
    private List  floatBoxingList;
    private List  doubleBoxingList;
    private List  bigDecimalList;
    private List  bigIntegerList;
    private List  dateList;
    private List  stringList;
    private List > stringListList;
    private List > stringSetList;
    private List > mapList;

    //数组LIST
    private List  byteBoxingArrayList;
    private List  booleanBoxingArrayList;
    private List  charBoxingArrayList;
    private List  shortBoxingArrayList;
    private List  integerBoxingArrayList;
    private List  longBoxingArrayList;
    private List  floatBoxingArrayList;
    private List  doubleBoxingArrayList;
    private List  bigDecimalArrayList;
    private List  bigIntegerArrayList;
    private List  dateArrayList;
    private List  stringArrayList;

    //二维数组LIST
    private List  byteBoxingDoubleArrayList;
    private List  booleanBoxingDoubleArrayList;
    private List  charBoxingDoubleArrayList;
    private List  shortBoxingDoubleArrayList;
    private List  integerBoxingDoubleArrayList;
    private List  longBoxingDoubleArrayList;
    private List  floatBoxingDoubleArrayList;
    private List  doubleBoxingDoubleArrayList;
    private List  bigDecimalDoubleArrayList;
    private List  bigIntegerDoubleArrayList;
    private List  dateDoubleArrayList;
    private List  stringDoubleArrayList;

    //SET
    private Set  byteBoxingSet;
    private Set  booleanBoxingSet;
    private Set  charBoxingSet;
    private Set  shortBoxingSet;
    private Set  integerBoxingSet;
    private Set  longBoxingSet;
    private Set  floatBoxingSet;
    private Set  doubleBoxingSet;
    private Set  bigDecimalSet;
    private Set  bigIntegerSet;
    private Set  dateSet;
    private Set  stringSet;
    private Set > stringListSet;
    private Set > stringSetSet;
    private Set > mapSet;

    //数组SET
    private Set  byteBoxingArraySet;
    private Set  booleanBoxingArraySet;
    private Set  charBoxingArraySet;
    private Set  shortBoxingArraySet;
    private Set  integerBoxingArraySet;
    private Set  longBoxingArraySet;
    private Set  floatBoxingArraySet;
    private Set  doubleBoxingArraySet;
    private Set  bigDecimalArraySet;
    private Set  bigIntegerArraySet;
    private Set  dateArraySet;
    private Set  stringArraySet;

    //二维数组SET
    private Set  byteBoxingDoubleArraySet;
    private Set  booleanBoxingDoubleArraySet;
    private Set  charBoxingDoubleArraySet;
    private Set  shortBoxingDoubleArraySet;
    private Set  integerBoxingDoubleArraySet;
    private Set  longBoxingDoubleArraySet;
    private Set  floatBoxingDoubleArraySet;
    private Set  doubleBoxingDoubleArraySet;
    private Set  bigDecimalDoubleArraySet;
    private Set  bigIntegerDoubleArraySet;
    private Set  dateDoubleArraySet;
    private Set  stringDoubleArraySet;

    //Map
    private Map  basicMap;
    private Map  keyArrayMap;
    private Map  valueArrayMap;
    private Map  keyValueArrayMap;
    private Map  keyValueDoubleArrayMap;
    private Map , Map > keyListValueMapMap;
    private Map [], Map []> keyArrayListValueArrayMapMap;
    
    //todo 省略了get/set方法
    }
//调用模拟数据的方法模拟Java对象
BasicBean basicBean = Mock.mock(BasicBean.class);
```

### 忽略某个属性

在需要忽略的字段上添加注解@MockIgnore即可
```java

/**
 * @author :  peng.liu
 * @description : 测试忽略 属性 的bean
 * @date :    2018/7/16 10:13
 */
public class IgnoreBean {
    @MockIgnore
    private String ignore;
    private int notIgnore;
    
    //省略get/set方法
}

  /**
     * 测试忽略属性
     */
    @Test
    public void testIgnore() {
        IgnoreBean a = Mock.mock(IgnoreBean.class);
        System.err.println(JsonUtil.toStr(a));;
    }

```


### 更改随机范围
```java
MockConfig mockConfig = new MockConfig()
    .byteRange((byte) 0, Byte.MAX_VALUE)
    .shortRange((short) 0, Short.MAX_VALUE)
    .intRange(0, Integer.MAX_VALUE)
    .floatRange(0.0f, Float.MAX_EXPONENT)
    .doubleRange(0.0, Double.MAX_VALUE)
    .longRange(0, Long.MAX_VALUE)
    .dateRange("2010-01-01", "2020-12-30")
    .sizeRange(5, 10)
    .stringSeed("a", "b", "c")
    .charSeed((char) 97, (char) 98);
BasicBean basicBean = Mock.mock(BasicBean.class, mockConfig);
```

## 高级特性
### 循环依赖

```java
public class AXB {
  private BXA BXA;
  private String name;
  //getter setter省略...
}
public class BXA {
  private AXB AXB;
  private String name;
  //getter setter省略...
}
@Test
public void testCircular() {
   AXB axb = Mock.mock(AXB.class);
   AXB circularAxb = axb.getBXA().getAXB();
   assertSame(axb, circularAxb);
}
```

### 自依赖

```java
public class SelfRefData {

  private Integer id;
  private String name;
  private SelfRefData parent;
  private Map  parentMap;
  private SelfRefData[] parentArray;
  private List  list;
  private List  listArray;
  private List > listListArray;
  private List [] arrayList;

  private SelfRefData[][][] data;
  private Map  mapArray;
  private Map > mapList;
  private Map > mapListArray;
  //getter setter省略...
}
@Test
public void testSelf() {
   SelfRefData selfRefData = Mock.mock(SelfRefData.class);
   assertSame(selfRefData.getParent(), selfRefData);
}
```

### 泛型继承

```java
//定义一个泛型父类
public class GenericData  {
  private A a;
  private B b;
  private C c;
  private A[] aArray;
  private List  bList;
  private Map  map;
  private List [] cArray;
  private Map , List >[] d;
  //getter setter省略...
}

@Test
public void testGenericData() {
    GenericData  genericData = Mock.mock(new TypeReference >() {});
    assertNotNull(genericData);
  }
```
### String类型的特殊处理
目前支持：
1. 返回随机长度的英文字符
2. 返回随机长度的中文（实际是返回随机截取的一段话，种子文件我选用了朱自清的《春》，李白的《将进酒》和《滕王阁序》，在String.text文件中，你可以替换你喜欢的任何汉字，比如你希望用美国独立宣言或者水浒传都没有问题）
3. 返回uuid
预计实现：
1. url 类型，图片类型，http/https类型 其他协议类型
2. 随机生成 人名，地名
3. 生成超长文本，字符串大于65535个字符
4. 生成各种文字的混合体，默认编码utf-8
其他骚操作，以后用到再说吧

#### 加入qq群交流 317896269



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)