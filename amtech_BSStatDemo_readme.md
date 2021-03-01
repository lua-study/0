# BSStatDemo
利用 AOP 编程思想编写的一个埋点收集工具



    /**
     *  对于按钮, 当调用过 addTarget:action:forControlEvents: 方法后将记录此按钮的 touch 事件
     *  事件的名称是 eventKey
     *  对于 UIButton/UITextField/UIViewController 默认 eventKey 分别是
     *  title/placeholder/class name
     */
    [self.testButton setTitle:@"按钮名称" forState:UIControlStateNormal];
    [self.testButton addTarget:self action:@selector(pressButton:) forControlEvents:UIControlEventTouchUpInside];
    /**
     *  除了特定方法外, 还可以设置 needTelemetry 属性告知是否记录该控件 touch 事件
     */
    [self.testSlider setValue:@YES forKey:@"needTelemetry"];
    [self.testSlider setValue:@"自定义名称，默认无名称将不记录" forKey:@"eventKey"];
    /**
     *  默认无名称将不记录
     */
    [self.testSwitch setValue:@YES forKey:@"needTelemetry"];
    
    
    


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)