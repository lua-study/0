# RW_DropdownMenu

### Import
导入头文件DropdownMenu.h

### How To Use
实现初始化
- (id)initDropdownWithButtonTitles:(NSArray*)titles andLeftListArray:(NSArray*)leftArray andRightListArray:(NSArray *)rightArray;
- 例如：
- DropdownMenu *dropdown = [[DropdownMenu alloc] initDropdownWithButtonTitles:_titleArray andLeftListArray:_leftArray andRightListArray:_rightArray];
   dropdown.delegate = self;   //此句的代理方法可返回选中下标值
   [self.view addSubview:dropdown.view];

### Delegate
//实现代理，返回选中的下标，若左边没有列表，则返回0。left为左边选中下标，right为右边选中下标
- (void)dropdownSelectedLeftIndex:(NSString *)left RightIndex:(NSString *)right; {
    NSLog(@"%s : You choice %@ and %@", __FUNCTION__, left, right);
}


### Demo
![image](https://github.com/Ryan-Wong-iOS/RW_DropdownMenu/raw/master/RW_DropdownMenu/demo.gif)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)