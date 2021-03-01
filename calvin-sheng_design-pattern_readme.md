## Java策略模式在电商项目中的使用

**背景**：随着电商网站业务的发展，会有越来越多的用户。我们会将用户分为新用户，老用户，VIP用户和MVP用户。对于不同的用户类型，商品的购买折扣和邮费也有所不同。那么如何避免在service中写大量的if/else来判断用户类型，这就是本篇笔者要介绍的，策略模式的落地使用。



### 一、了解策略模式

**（1）定义**

   定义一系列的算法，把它们一个个封装起来，并且使它们可相互替换。

**（2）类图**

![](https://images.gitee.com/uploads/images/2020/0102/165950_dddc77f3_880818.png)

**（3）使用场景**

- 多个类只有在算法或行为上稍有不同的场景； 

- 算法需要自由切换的场景；

-  需要屏蔽算法规则的场景。  				 			 		

    						 					 				 			 		

### 二、策略模式的代码实现

本篇主要是介绍策略模式的使用，对于代码中商品原价，邮费等暂时写死，实际项目中一般都是通过接口获取。

**（1）定义一个策略接口**

```java
package com.calvin.design.service;

import java.math.BigDecimal;
import java.util.Map;
import java.util.concurrent.ConcurrentHashMap;
import javax.annotation.PostConstruct;

/**
 * @Title ICustomerPriceStrategy
 * @Description
 * @author calvin
 * @date: 2020/1/2 3:36 PM 
 */
public interface ICustomerPriceStrategy {

    Map  map = new ConcurrentHashMap<>();

    /**
     * 获取客户价格
     * @param originalPrice 原价
     * @return
     */
    BigDecimal getCustomerPrice(BigDecimal originalPrice);

    /**
     * 获取邮费
     * @return
     */
    BigDecimal getShippingFee();

    /**
     * 获取客户类型
     * @return
     */
    String getCustomerType();

		/**
     * 初始化map，key为用户类型，value为具体的Strategy
     */
    @PostConstruct
    default void init() {
        map.put(getCustomerType(), this);
    }

}
```

**（2）定义常量**

```java
package com.calvin.design.constants;

/**
 * @Title CustomerTypeConstans
 * @Description 客户类型常量
 * @author calvin
 * @date: 2020/1/2 3:31 PM 
 */
public class CustomerTypeConstans {

    public static final String NEW = "新客户";

    public static final String OLD = "老客户";

    public static final String VIP = "VIP客户";
    
    public static final String MVP = "MVP客户";

}
```

**（3）策略接口实现类**

分别定义新用户，老用户，VIP用户及MVP客户的策略接口实现类。本篇只列举新用户及VIP用户。

```java
package com.calvin.design.service.impl;

import com.calvin.design.constants.CustomerTypeConstans;
import com.calvin.design.service.ICustomerPriceStrategy;
import java.math.BigDecimal;
import org.springframework.stereotype.Service;

/**
 * @Title NewCustomerPriceStrategyImpl
 * @Description 新用户策略
 * @author calvin
 * @date: 2020/1/2 3:42 PM 
 */
@Service
public class NewCustomerPriceStrategyImpl implements ICustomerPriceStrategy {

    /**
     * 获取客户价格
     * @param originalPrice 原价
     * @return
     */
    @Override
    public BigDecimal getCustomerPrice(BigDecimal originalPrice) {
        return originalPrice;
    }

    /**
     * 获取邮费
     * @return
     */
    @Override
    public BigDecimal getShippingFee() {
        return new BigDecimal(10.11);
    }

    /**
     * 获取客户类型
     * @return
     */
    @Override
    public String getCustomerType() {
        return CustomerTypeConstans.NEW;
    }
}
```

```java
package com.calvin.design.service.impl;

import com.calvin.design.constants.CustomerTypeConstans;
import com.calvin.design.service.ICustomerPriceStrategy;
import java.math.BigDecimal;
import org.springframework.stereotype.Service;

/**
 * @Title NewCustomerPriceStrategyImpl
 * @Description VIP用户策略
 * @author calvin
 * @date: 2020/1/2 3:42 PM 
 */
@Service
public class VipCustomerPriceStrategyImpl implements ICustomerPriceStrategy {

    /**
     * 获取客户价格
     * @param originalPrice 原价
     * @return
     */
    @Override
    public BigDecimal getCustomerPrice(BigDecimal originalPrice) {
        return originalPrice.multiply(new BigDecimal(0.7).setScale(2, BigDecimal.ROUND_HALF_UP));
    }

    /**
     * 获取邮费
     * @return
     */
    @Override
    public BigDecimal getShippingFee() {
        return new BigDecimal(8.88);
    }

    /**
     * 获取客户类型
     * @return
     */
    @Override
    public String getCustomerType() {
        return CustomerTypeConstans.VIP;
    }
}
```

**（4）定义上下文类，做具体的逻辑运算**

```java
package com.calvin.design.context;

import com.calvin.design.constants.CustomerTypeConstans;
import com.calvin.design.service.ICustomerPriceStrategy;
import java.math.BigDecimal;

/**
 * @Title CustomerPriceContext
 * @Description 用户类型价格上下文
 * @author calvin
 * @date: 2020/1/2 3:52 PM 
 */
public class CustomerPriceContext {

    private ICustomerPriceStrategy customerPriceStrategy;

    public CustomerPriceContext(String customerType) {
        this.customerPriceStrategy = ICustomerPriceStrategy.map.get(customerType);
        if (customerPriceStrategy == null) {
            customerPriceStrategy = ICustomerPriceStrategy.map.get(CustomerTypeConstans.NEW);
        }
    }

    /**
     * 在上下文类中计算不同用户类型对应的价格和邮费之和
     * @param originalPrice
     * @return
     */
    public String getTotalPrice(BigDecimal originalPrice) {
        System.out.println("进行一些前置处理");
        BigDecimal price = customerPriceStrategy.getCustomerPrice(originalPrice);
        price = price.add(customerPriceStrategy.getShippingFee()).setScale(2, BigDecimal.ROUND_HALF_UP);
        System.out.println("进行一些后置处理");
        return price.toPlainString();
    }
}
```

**（5）定义controller**

```java
package com.calvin.design.controller;

import com.calvin.design.context.CustomerPriceContext;
import java.math.BigDecimal;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

/**
 * @Title CustomerPriceController
 * @Description 不同客户类型定价不同
 * @author calvin
 * @date: 2020/1/2 3:33 PM 
 */

@RestController
@RequestMapping("customer")
public class CustomerPriceController {

    private static final BigDecimal originalPrice = new BigDecimal(7000.00).setScale(2, BigDecimal.ROUND_HALF_UP);

    /**
     * 根据客户类型，返回对应的价格
     * @param customerType
     * @return
     */
    @GetMapping("price")
    public String customerPrice(@RequestParam String customerType) {
        CustomerPriceContext customerPriceContext = new CustomerPriceContext(customerType);
        return customerPriceContext.getTotalPrice(originalPrice);
    }
}
```

**（6）测试**

浏览器输入：[http://localhost:8020/customer/price?customerType=新用户](http://localhost:8020/customer/price?customerType=新用户)

![输入图片说明](https://images.gitee.com/uploads/images/2020/0102/174002_f03bfd5c_880818.png "222.png")



当输入：[http://localhost:8020/customer/price?customerType=VIP用户](http://localhost:8020/customer/price?customerType=VIP用户)

![输入图片说明](https://images.gitee.com/uploads/images/2020/0102/173950_41123734_880818.png "111.png")

### 三、总结

基于上面的测试，可以看到已经实现了根据不同用户类型，从而计算价格及邮费等逻辑。这就是策略模式在电商项目的一个落地使用的案例。当然任何东西都有两面性，有好也有坏，我们也需要了解策略模式的优缺点。

**1、优点**

-  算法可以自由切换。  						 						 							
- 避免使用多重条件判断。  						 						 							
- 扩展性良好【 (1) 策略模式提供了对“开闭原则”的完美支持，用户可以在不修改原有系统的基 础上选择算法或行为，也可以灵活地增加新的算法或行为。 (2) 算法的使用就和算法本身分开，符合“单一职责原则”; (3) 策略模式提供了一种算法的复用机制，由于将算法单独提取出来封装在策略类中，因此不同的环境类可以方便地复用这些策略类。】  						 					 				 			 		

**2、缺点**

- 客户端必须知道所有的策略类，并自行决定使用哪一个策略类。这就意味着客户端必须理解 这些算法的区别，以便适时选择恰当的算法。换言之，策略模式只适用于客户端知道所有的算法或行为的情况。
- 策略模式将造成系统产生很多具体策略类，任何细小的变化都将导致系统要增加一个新的具体策略类。
- 无法同时在客户端使用多个策略类，也就是说，在使用策略模式时，客户端每次只能使用一个策略类，不支持使用一个策略类完成部分功能后再使用另一个策略类来完成剩余功能的情况。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)