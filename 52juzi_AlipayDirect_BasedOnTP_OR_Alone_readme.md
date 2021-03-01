# AlipayDirect_BasedOnTP_OR_Alone
 一、说明 
0、 项目经过完整测试！可放心使用！    
1、基于最新 Thinkphp3.2.3 开发而成。    
2、虽然基于TP开发而成，但是代码里面的支付宝类可以单独出来使用。    
3、本人学生一枚，如果代码有不好的地方，希望您指出。    
 二、使用方法 
0、 使用非常简单！     
1、在 config.php 中写上自己的支付宝PID 、KEY、和邮箱账号；    
2、在 Controller/AlipayController 中重写相关订单业务逻辑（比如订单状态更新啊什么的）就行了。具体可以看里面的注释。  
 三、关于独立出来使用 
1、把Common/Lib/Alipay文件夹下的Alipay.class.php文件独立出来。同时更改里面的 toAlipay 方法。里面有 $para['notify_url'] 和 $para['return_url'] 这里的URL需要重新填写；还有 $para['partner']、$para['seller_email'] 这里的配置项需要填写，以及类中的其他配置项有关参数都要重新写。    
2、其他的业务逻辑可以参照 AlipayController 去写。（第二步，使用方法）    
3、请将根目录下面的 cacert.pem 同时独立出来，这是支付宝的证书。否则return 或者 notify 将验证失败。订单状态将更新失败
 四、如果有什么问题，可以ISSUES出来。感谢您的使用！请务必保留版权信息 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)