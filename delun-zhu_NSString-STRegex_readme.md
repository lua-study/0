#NSString+STRegex

  一些正则校验，判断邮箱，手机号码，车牌号，身份证号，网址，账号，密码，ip，去掉html格式等。
  

![image](http://git.oschina.net/yanglishuan/NSString-STRegex/raw/master/ScreenShots/screenshot1.png)
![image](http://git.oschina.net/yanglishuan/NSString-STRegex/raw/master/ScreenShots/screenshot2.png)

  // 判断邮箱
isValid = [text isValidEmail];
// 判断手机号码
isValid = [text isValidPhoneNum];
// 判断ip
isValid = [text isValidIP];
// 判断身份证号
isValid = [text isValidIdCardNum];
// 判断账号
isValid = [text isValidWithMinLenth:4 maxLenth:12 containChinese:NO firstCannotBeDigtal:YES];
// 去掉html格式
text = [text removeHtmlFormat];
  

注：其中身份证号验证由张衎友情提供，在此表示感谢。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)