# dto-validation
dto 较验

[![Build Status](https://travis-ci.org/actors315/dto-validation.svg?branch=master)](https://travis-ci.org/actors315/dto-validation)  

日常工作中，跟第三方系统对接是常有的事，而这些系统可能并不是同一种语言实现的，因为语言特性不同，总会遇到意想不到的事情。  
比如 php 是弱类型语言，'1'  与 1 是没有区别的，但是在 java 中，这两个就并不相同了。比如 null 与 '' 在 php 中也是相等的，但是在其他语言中，赋值就可能报错。  

这个库主要就是满足这些需要。

## 使用

使用前必须将规则较验实例注入到容器

```php

$container = new \Twinkle\DI\Container([
    'Validate:Required' => \twinkle\dto\validation\annotation\Required::class,
    'Validate:Type' => \twinkle\dto\validation\annotation\Type::class,
    'Validate:Enum' => \twinkle\dto\validation\annotation\Enum::class,
]);
\Twinkle\DI\Tools::setContainer($container);

```

## 示例

```php

/**
 * @Validate # 是否需要较验
 * @var integer # 声明类型
 * @var integer autoConvert=integer # 声明类型，并且尝试自动转换
 * @Required() # 必须字段
 * @Required(default=1) # 字段必须，在字段为null的情况下设置默认值
 * @Enum(1,2,3) # 字段值必须为1,2,3中的一个
 */
```

## Note

为了更好的开发体验，强列建议安装 annotations 插件  
phpstorm(http://plugins.jetbrains.com/plugin/7320-php-annotations)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)