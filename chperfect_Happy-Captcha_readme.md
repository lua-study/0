 

![](https://img.shields.io/badge/Name-HappyCaptcha-brightgreen) ![](https://img.shields.io/badge/Version-1.0.1-brightgreen) ![](https://img.shields.io/badge/JDK-JDK1.8-brightgreen) ![](https://img.shields.io/badge/License-Apache2.0-brightgreen) ![](https://img.shields.io/badge/Author-ramostear-brightgreen)

___



## 前言

Happy Captcha是一款易于使用的Java验证码软件包，旨在花最短的时间，最少的代码量，实现Web站点的验证码功能。Happy Captcha完全遵循Apache 2.0开源许可协议，你可以自由使用该软件，如您在使用Happy Captcha时发现软件的任何缺陷，欢迎随时与我联系。

Happy Capthca的源代码已托管到Github和Gitee，你可以访问下面的链接获取更多信息：

- Github: https://github.com/ramostear/Happy-Captcha
- Gitee: https://gitee.com/ramostear/Happy-Capthca

如果你想快速体验Happy Captcha的功能，可通过下列方式获取Happy-Captcha依赖：

**Maven**

```xml
 
   com.ramostear 
   Happy-Captcha 
   1.0.1 
 
```

**Gradle**

```tex
implementation 'com.ramostear:Happy-Captcha:1.0.1'
```



## 一、展示

Happy Captcha提供了图片和动画两种展现形式，验证码内容包括中文(收录3500个常用汉字)，阿拉伯数字(0~9)，中文数字(零至九)，中文大写数字(零至玖)，数字与字母混合(0~9-a~z-A~Z)，数字与小写字母混合(0~9-a~z)，数字与大写字母混合(0~9-A~Z)，纯小写字母，纯大写字母，大小写字母混合以及运算表达式(阿拉伯数字运算表达式和中文运算表达式)等12种类型。

| CaptchaType       | IMAGE                                                  | ANIMATION                                               |
| ----------------- | ------------------------------------------------------ | ------------------------------------------------------- |
| CHINESE           | ![](https://images.gitee.com/uploads/images/2020/0517/225738_0be49a75_535045.gif)           | ![](https://images.gitee.com/uploads/images/2020/0517/225738_20c5bb26_535045.gif)           |
| NUMBER            | ![](https://images.gitee.com/uploads/images/2020/0517/225738_59c1302f_535045.gif)            | ![](https://images.gitee.com/uploads/images/2020/0517/225738_fac3bfa7_535045.gif)            |
| NUMBER_ZH_CN      | ![](https://images.gitee.com/uploads/images/2020/0517/225738_2a3b9171_535045.gif)      | ![](https://images.gitee.com/uploads/images/2020/0517/225738_40de5eb7_535045.gif)      |
| NUMBER_ZH_HK      | ![](https://images.gitee.com/uploads/images/2020/0517/225739_eaa2cca9_535045.gif)      | ![](https://images.gitee.com/uploads/images/2020/0517/225739_66ef9c93_535045.gif)      |
| DEFAULT           | ![](https://images.gitee.com/uploads/images/2020/0517/225738_3970646f_535045.gif)           | ![](https://images.gitee.com/uploads/images/2020/0517/225739_d1c7587e_535045.gif)           |
| WORD              | ![](https://images.gitee.com/uploads/images/2020/0517/225739_8f23ce12_535045.gif)              | ![](https://images.gitee.com/uploads/images/2020/0517/225739_b6a15158_535045.gif)              |
| WORD_LOWER        | ![](https://images.gitee.com/uploads/images/2020/0517/225739_aa79a497_535045.gif)        | ![](https://images.gitee.com/uploads/images/2020/0517/225739_79a09721_535045.gif)        |
| WORD_UPPER        | ![](https://images.gitee.com/uploads/images/2020/0517/225739_3773817d_535045.gif)        | ![](https://images.gitee.com/uploads/images/2020/0517/225740_af6e369e_535045.gif)        |
| WORD_NUMBER_LOWER | ![](https://images.gitee.com/uploads/images/2020/0517/225740_643b2b54_535045.gif) | ![](https://images.gitee.com/uploads/images/2020/0517/225741_08d33c90_535045.gif) |
| WORD_NUMBER_UPPER | ![](https://images.gitee.com/uploads/images/2020/0517/225740_bc2e2722_535045.gif) | ![](https://images.gitee.com/uploads/images/2020/0517/225740_cb31b28d_535045.gif) |
| ARITHMETIC        | ![](https://images.gitee.com/uploads/images/2020/0517/225740_cdf968f0_535045.gif)        | ![](https://images.gitee.com/uploads/images/2020/0517/225740_31c9abf9_535045.gif)        |
| ARITHMETIC_ZH     | ![](https://images.gitee.com/uploads/images/2020/0517/225740_1822d84d_535045.gif)     | ![](https://images.gitee.com/uploads/images/2020/0517/225740_3970e89c_535045.gif)     |



## 二、安装

如果你的项目使用的是Maven进行依赖管理，你只需向pom.xml文件添加下面的配置即可：

```xml
 
   com.ramostear 
   Happy-Captcha 
   1.0.1 
 
```

Gradle用户则可以通过引入如下的配置获取Happy Captcha:

```tex
implementation 'com.ramostear:Happy-Captcha:1.0.1'
```



## 三、使用

HappyCaptcha在设计时力求过程的简洁，在默认情况下，你只需要书写一行代码即可生成漂亮的验证码图片。下面是HappyCaptcha的使用示例：

```java
@Controller
public class HappyCaptchaController{
    @GetMapping("/captcha")
    public void happyCaptcha(HttpServletRequest request,HttpServletResponse response){
        HappyCaptcha.require(request,response).build().finish();
    }
}
```

对于HappyCaptcha而言，只有request和response是必须提供的参数，其余参数都可以使用缺省值。

> 在默认情况下，HappyCaptcha生成的验证码以图片形式展现，内容为0~9-a~z-A~Z的字符随机组合，字符长度为5，图片宽度为160，高度为50，字体为微软雅黑。



## 四、校验

用户输入的验证码校验是一个必不可少的环节，HappyCaptcha内置了对用户输入的验证码校验功能。下面是验证码校验示例：

```java
@Controller
public class CaptchaController{
 
    @PostMapping("/verify")
    public String verify(String code,HttpServletRequest request){
        //Verification Captcha
        boolean flag = HappyCaptcha.verification(request,code,true);
        if(flag){
            //Other operations...
        }
    }
}
```

> 如果在校验过程中需要忽略字母大小写，第三个参数设置为true，如果需要强校验，则设置为false。



## 五、清理

当验证码被使用后，你可以通过HappyCaptcha类种的remove()方法将Session中存放的验证码清理掉。下面是清理验证码的代码示例：

```java
@Controller
public class HappyCaptchaController{
    
    @GetMapping("/remove/captcha")
    public void removeCaptcha(HttpServletRequest request){
     	HappyCaptcha.remove(request);   
    }
}
```

> 除HappyCaptcha提供的默认方法，你也可以在需要操作的地方，手动清理Session中存放的验证码，HappyCaptcha验证码的Key为“happy-captcha”。



## 六、高级特性

通过前面的内容，我们已经了解到如何快熟的安装并使用HappyCaptcha生成验证码。在接下的内容当中，将介绍HappyCaptcha更详细的内容。

### 6.1 style()

HappyCaptcha提供两种验证码展现形式：图片和动画。默认的展现形式为图片，可以通过style()方法修改默认值。style()方法的值由CaptchaStyle类提供，可供选择的值有IMG和ANIM。style()使用示例如下：

```java
HappyCaptcha.require(request,response)
    	    .style(CaptchaStyle.ANIM)
            .build().finish(); 
```

> 若展现形式为图片，则style(CaptchaStyle.IMG)可以省略。



### 6.2 type()

HappyCaptcha一共提供了12种验证码类型，你可以自由选择其中的一种类型作为验证码的内容形式。默认情况下，验证码使用数字和大小写字母的混合形式。验证码类型值由CaptchaType类提供，内容如下表：

| 值                | 说明                                 |
| ----------------- | ------------------------------------ |
| DEFAULT           | 数字、大小写字母随机组合             |
| ARITHMETIC        | 加、减、乘算数运算表达式             |
| ARITHMETIC_ZH     | 中文简体加、减、乘算数运算表达式描述 |
| CHINESE           | 常见汉字（3500个）随机组合           |
| NUMBER            | 0~9数字随机组合                      |
| NUMBER_ZH_CN      | 中文数字（零至九）随机组合           |
| NUMBER_ZH_HK      | 中文繁体数字（零至玖）随机组合       |
| WORD              | 大小写字母随机组合                   |
| WORD_LOWER        | 小写字母随机组合                     |
| WORD_UPPER        | 大写字母随机组合                     |
| WORD_NUMBER_LOWER | 数字、小写字母随机组合               |
| WORD_NUMBER_UPPER | 数字、大写字母随机组合               |

type()使用示例如下：

```java
HappyCaptcha.require(request,response)
    		.type(CaptchaType.CHINESE)
    		.build().finish();
```



### 6.3 length()

length()方法用于设置验证码字符长度，默认情况下缺省值为5。你可以通过以下方式对验证码字符长度进行控制：

```java
HappyCaptcha.require(request,response)
    		.length(6)
    		.build().finish();
```



### 6.4 width()

width()方法可对验证码图片的宽度进行调节，默认的缺省值为160。使用方式如下：

```java
HappyCaptcha.require(request,response)
    		.width(180)
    		.build().finish();
```



### 6.5 height()

同width()方法一样，height()方法用于设置验证码图片的高度，默认缺省值为50。使用方式如下：

```java
HappyCaptcha.require(request,response)
    		.height(60)
    		.build().finish();
```



###  6.6 font()

如果你想改变验证码的字体，可通过font()方法进行设置，默认缺省字体为微软雅黑。HappyCaptcha内置了四种字体，可以通过Fonts类进行调用。

```java
HappyCaptcha.require(request,response)
    		.font(Fonts.getInstance().zhFont())
    		.build().finish();
```



### 6.7 链式调用

上面介绍了如何修改单个配置，HappyCaptcha支持链式调用，可同时对验证码的多个属性进行设置。例如：

```java
@GetMapping("/captcha")
public void captcha(HttpServletRequest req,HttpServletResponse res){
    HappyCaptcha.require(req,res)
        		.style(CaptchaStyle.ANIM)			//设置展现样式为动画
        		.type(CaptchaType.CHINESE)			//设置验证码内容为汉字
        		.length(6)							//设置字符长度为6
        		.width(220)							//设置动画宽度为220
        		.height(80)							//设置动画高度为80
        		.font(Fonts.getInstance().zhFont())	//设置汉字的字体
        		.build().finish();      			//生成并输出验证码
}
```

> 若验证码的类型为ARITHMETIC或ARITHMETIC_ZH,可省略验证码长度的设置。算术运算表达式的长度为5。



## 结束语

Happy Captcha参考了一些优秀的验证码框架设计，同时引用了一些第三方的编码类，在此统一表示感谢！如果你觉得Happy Captcha对你有所帮助,请作者喝杯咖啡吧~~



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)