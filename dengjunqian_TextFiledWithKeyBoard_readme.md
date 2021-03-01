    //1.初始化
    [IQKeyBoardManager installKeyboardManager];
    //2.添加一个输入框   并让他不显示
    textFiled = [[UITextField alloc] initWithFrame:CGRectMake(0, 0, 0, 0)];
    [self.view addSubview:textFiled];
    //3.添加键盘上方输入框布局
    [textFiled addTextFiled:^(UITextField *mTextFiled) {
        //点击输入框的回车之后 回调回来的内容
        [[[iToast makeText:[NSString stringWithFormat:@"输入的内容：%@", mTextFiled.text]] setGravity:iToastGravityCenter] show];
        [mTextFiled resignFirstResponder];
    }];
     //4.显示键盘
    [textFiled becomeFirstResponder];

	![img](http://git.oschina.net/gejw0623/TextFiledWithKeyBoard/blob/master/TextFiledWithKeyBoard/screen.jpg)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)