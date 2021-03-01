# 计算器

ViewControl代码：

```object-c
//
//  ViewController.m
//  calculator
//
//  Created by 石磊 on 2018/8/14.
//  Copyright © 2018年 石头. All rights reserved.
//

#import "ViewController.h"

// 类扩展
@interface ViewController ()

// 点击计算按钮
- (IBAction)add:(id)sender;
// 表示第一个文本框
@property (weak, nonatomic) IBOutlet UITextField *txtNum01;
// 表示第二个文本框
@property (weak, nonatomic) IBOutlet UITextField *txtNum02;
// 显示计算结果的文本框
@property (weak, nonatomic) IBOutlet UILabel *txtResult;


@end

@implementation ViewController

- (void)viewDidLoad {
[super viewDidLoad];
// Do any additional setup after loading the view, typically from a nib.
}


- (void)didReceiveMemoryWarning {
[super didReceiveMemoryWarning];
// Dispose of any resources that can be recreated.
}


- (IBAction)add:(id)sender {
//测试点击事件
NSLog(@"计算方法被执行");
//获取用户输入的数字
NSString * strNum01 =  self.txtNum01.text;
NSString * strNum02 =  self.txtNum02.text;
int intNum01 = strNum01.intValue;
int intNum02 = strNum02.intValue;
//计算
int intResult = intNum01+intNum02;
//把结果显示到tvResult上
self.txtResult.text = [NSString stringWithFormat:@"%d",intResult];

// 4. 把键盘叫回去
// 谁叫出的键盘, 那么谁就是"第一响应者", 让"第一响应者"辞职, 就可以把键盘叫回去
//    [self.tvNum01 resignFirstResponder];
//    [self.tvNum02 resignFirstResponder];

// 5. 把键盘叫回去的第二种做法
// self.view就表示是当前控制器所管理的那个view（每一个控制器都会管理一个view）
// 这时把键盘叫回去的思路就是：让控制器所管理的view停止编辑，这样的话, 凡是这个view中的子控件叫出的键盘就都回去了。
[self.view endEditing:YES];
}
@end

```




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)