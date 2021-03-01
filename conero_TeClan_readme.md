# Phalcon Tutorial

Phalcon is a web framework for PHP delivered as a C extension providing high
performance and lower resource consumption.

This is a very simple tutorial to understand the basis of work with Phalcon.

Check out a [explanation article][1].

## Get Started

### Requirements

To run this application on your machine, you need at least:

* PHP >= 5.4
* [Apache][2] Web Server with [mod_rewrite][3] enabled or [Nginx][4] Web Server
* Latest stable [Phalcon Framework release][5] extension enabled

## License

Phalcon Tutorial is open-sourced software licensed under the [New BSD License][6]. © Phalcon Framework Team and contributors

[1]: http://docs.phalconphp.com/en/latest/reference/tutorial.html
[2]: http://httpd.apache.org/
[3]: http://httpd.apache.org/docs/current/mod/mod_rewrite.html
[4]: http://nginx.org/
[5]: https://github.com/phalcon/cphalcon/releases
[6]: https://github.com/phalcon/tutorial/blob/master/docs/LICENSE.md



##2016年7月15日： @Hyanghua 关于TeClan项目
>> 下载Phalcon参考实例：
    1.tutorial
    2.invo
>>2016年7月16日
    1.暂时不考虑使用volt视图引擎
>>2016年7月17日/数据库重新修改
    gen_center      家族中心
    gen_zibei       家族字辈     
    gen_node        家族人  
    gen_history     家族事迹

    需要考虑特殊权限
>>2016年7月20日 model(无法连接数据库) bug调试
    利用tutorial，配置测试环境，在cro内建立数据库，用于数据项目对比 
        之前以为是model的命名问题，并执行在项目中建立Test对应数据库名的model，依然报错
        Exception: Call to undefined method Phalcon\Config::tableexists()
        测试结果： tutorial项目运行正常
>>2016年7月23日    家族成员设计/拖动原理
    男子继承链-表
    男子--家庭表(gen_family) : 户主

    拖动原理>>
        只有元素position为absolute、fixed时才可，
        cursor 网页鼠标设置css
>>2016年7月24日    屏幕录像专家
    屏幕录像专家V2016 -可录制电脑操作视频  
>>2016年7月25日    span.width无效          
    span.width默认无效，但可通过 display:block; (强制换行)/display:inline-block;  使其有效

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)