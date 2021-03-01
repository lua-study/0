#MyNotes
实现截屏效果：
![Note1.gif](http://upload-images.jianshu.io/upload_images/1397676-5eec9ef4ede674e3.gif?imageMogr2/auto-orient/strip)
###2017.3.16号周四
####上午：继续学习IOS的基础知识,准备做一个小的demo，逐步完善起来，算是给自己的一点压力吧。
###加油持之以恒
1.遇到的第一个问题就是怎么在UIBarButtonItem的一个button触发编辑的动作。
关联一个按钮的触发动作如下所示：
```objc
- (IBAction)editCell:(id)sender {
    if (_editButton.tag == 0) {
        [self.tableView setEditing:true animated:true];
        _editButton.title = @"Done";
        _editButton.tag = 1;
        [_editButton titleTextAttributesForState:UIControlStateNormal];
    }else{
        [self.tableView setEditing:false animated:true];
        _editButton.tag = 0;
        _editButton.title = @"Edit";
        [_editButton titleTextAttributesForState:UIControlStateNormal];
    }
}
```
2.又遇到一个问题就是editButton.title修改不了，不知道问题在哪里，最后通过修改State状态进行改变了。
####下午：
遇到的问题有：1.视图之间的调整
2.视图之间的数据传递
这里又有一个概念混淆了`[self dismissViewControllerAnimated:true completion:`这个只是适用于模态视图的关闭。
那么如果不是模态视图，我要关闭当前的视图，返回之前的视图并且传值怎么办。
3.现在另一个问题是NavigationController的push出来的视图，我该怎么关闭，怎么传值
关闭有的是pop的方式，传值用的NSNotificationCenter广播的方式
```objc
//NSDictionary *dict =[NSDictionary dictionaryWithObject:self.label.text forKey:@"username"];
 NSDictionary *dict = @{@"content":_contentField.text};
    [[NSNotificationCenter defaultCenter]postNotificationName:@"GetInformation" object:nil userInfo:dict];
    [self.navigationController popViewControllerAnimated:true];
```
4.点击空白处隐藏键盘，或者点击return也要隐藏键盘
```objc
//添加手势动作来控制隐藏键盘
//点击手势
    UITapGestureRecognizer *tapGestureRecognizer = [[UITapGestureRecognizer alloc] initWithTarget:self action:@selector(keyboardHide:)];
    //设置成NO表示当前控件响应后会传播到其他控件上，默认为YES。
    tapGestureRecognizer.cancelsTouchesInView = NO;
    //将触摸事件添加到当前view
    [self.view addGestureRecognizer:tapGestureRecognizer];
-(void)keyboardHide:(UITapGestureRecognizer*)tap{
    [ _contentField endEditing:YES ];
}
//点击return隐藏键盘
-(BOOL)textFieldShouldReturn:(UITextField *)textField{
    [_contentField resignFirstResponder];
    return TRUE;
```
IOS的数据持久化总结
>
 "应用程序包"
 Documents
 Library
 -----Caches
 -----Preferences
 tmp

####属性列表文件
属性列表文件是一种xml文件，可能是数组或者字典。
NSDictionary字典类
```objc
NSDictionary *dict = @{@"name":@"chen"};
_dictData = [NSDictionary dictionaryWithContentsOfFile:plistPath];
_dictData = [[NSDictionary alloc]initWithContentsOfFile:plistPath];
[dict writeToFile:plistPath atomically:TRUE]
```
NSArray数组类
```objc
NSArray *array = @[@"123", @"456", @"789"];
_arr = [NSArray arrayWithContentsOfFile:plistPath];
_arr = [[NSArray alloc]initWithContentsOfFile:plistPath];
 [array writeToFile:plistPath atomically:TRUE]
```
####应用程序包的文件获取方式：
```objc
NSString *path = [[NSBundle mainBundle] bundlePath];
NSLog(@"%@", path);
//获取plist的文件
NSString *plistPath = [[NSBundle mainBundle] pathForResource:@"province_city" ofType:@"plist"];
_dictData = [[NSDictionary alloc]initWithContentsOfFile:plistPath];
```
####Documents的文件获取方式,iTunes同步该应用时会同步此文件夹中的内容，适合存储重要数据
```objc
NSString *path = NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES).firstObject;
NSLog(@"%@", path);
//获取plist的文件
```
####Library/Caches: iTunes不会同步此文件夹，适合存储体积大，不需要备份的非重要数据
```objc
NSString *path = NSSearchPathForDirectoriesInDomains(NSCachesDirectory, NSUserDomainMask, YES).firstObject;
NSLog(@"%@", path);
```
####tmp: iTunes不会同步此文件夹，系统可能在应用没运行时就删除该目录下的文件
```objc
NSString *path = NSTemporaryDirectory();
  NSLog(@"%@", path);
```
创建构造函数的方法Person *person = [[self alloc]init];
不能使用原来self = [super init];
原因是xcode会检测当前的代码命名，如果不是以init开头的就会报错，因此对于要创建静态的对象的方法只能使用如下的方式：
```objc
@interface Person : NSObject{
    NSString *name;
    NSInteger age;
}
+(instancetype)personWithName:(NSString *)name Age:(NSInteger)age;
@interface Person : NSObject
@property (nonatomic,strong) NSString *name;
@property(nonatomic,assign)NSInteger age;
+(instancetype)personWithName:(NSString *)name Age:(NSInteger)age;
@end

```
静态构造函数的使用方法
```objc
+(instancetype)personWithName:(NSString *)name Age:(NSInteger)age{
    Person *person = [[self alloc]init];
    person.name = name;
    person.age = age;
    return person;
}
```
###2017.3.31号周五
####下午
更新cocoapod的问题
```shell
➜  MyNotes git:(master) ✗ gem update cocoapods
Updating installed gems
Updating cocoapods
ERROR:  While executing gem ... (Gem::DependencyError)
    Unable to resolve dependencies: cocoapods requires fourflusher (~> 2.0.1), gh_inspector (~> 1.0)
```
###2017.4.1号周六
####上午：cocoapods更新的问题继续
查到一种解决办法感觉不错，因为gem源的问题，可是还是不行呢[url](http://blog.csdn.net/zxw_xzr/article/details/61198972)
```shell
➜  MyNotes git:(master) ✗ gem sources --remove https://ruby.taobao.org/
https://ruby.taobao.org/ removed from sources
➜  MyNotes git:(master) ✗ gem sources -l
*** CURRENT SOURCES ***

https://gems.ruby-china.org
➜  MyNotes git:(master) ✗ sudo gem install cocoapods
Password:
ERROR:  While executing gem ... (Gem::DependencyError)
    Unable to resolve dependencies: cocoapods requires cocoapods-core (= 1.2.0), cocoapods-downloader ( = 1.1.3), cocoapods-trunk ( = 1.1.2), molinillo (~> 0.5.5), xcodeproj ( = 1.4.1), fourflusher (~> 2.0.1), gh_inspector (~> 1.0), ruby-macho (~> 0.2.5)
➜  MyNotes git:(master) ✗ sudo gem uninstall -n /usr/local/bin cocoapods       
Remove executables:
	pod, sandbox-pod

in addition to the gem? [Yn]  y
Removing pod
Removing sandbox-pod
Successfully uninstalled cocoapods-0.39.0
➜  MyNotes git:(master) ✗ gem list --local | grep cocoapods
cocoapods-core (0.39.0)
cocoapods-downloader (0.9.3)
cocoapods-plugins (0.4.2)
cocoapods-search (0.1.0)
cocoapods-stats (0.6.2)
cocoapods-trunk (0.6.4)
cocoapods-try (0.5.1)
➜  MyNotes git:(master) ✗ sudo gem uninstall -n /usr/local/bin cocoapods-core
Successfully uninstalled cocoapods-core-0.39.0
➜  MyNotes git:(master) ✗ sudo gem uninstall -n /usr/local/bin cocoapods-downloader
Successfully uninstalled cocoapods-downloader-0.9.3
➜  MyNotes git:(master) ✗ sudo gem uninstall -n /usr/local/bin cocoapods-plugins
Successfully uninstalled cocoapods-plugins-0.4.2
➜  MyNotes git:(master) ✗ sudo gem uninstall -n /usr/local/bin cocoapods-search
Successfully uninstalled cocoapods-search-0.1.0
➜  MyNotes git:(master) ✗ sudo gem uninstall -n /usr/local/bin cocoapods-stats 
Successfully uninstalled cocoapods-stats-0.6.2
➜  MyNotes git:(master) ✗ sudo gem uninstall -n /usr/local/bin cocoapods-trunks
➜  MyNotes git:(master) ✗ sudo gem uninstall -n /usr/local/bin cocoapods-trunk 
Successfully uninstalled cocoapods-trunk-0.6.4
➜  MyNotes git:(master) ✗ sudo gem uninstall -n /usr/local/bin cocoapods-try  
Successfully uninstalled cocoapods-try-0.5.1
➜  MyNotes git:(master) ✗ sudo gem install cocoapods -V
Getting SRV record failed: DNS result has no information for _rubygems._tcp.gems.ruby-china.org
403 Forbidden
ERROR:  While executing gem ... (Gem::RemoteFetcher::FetchError)
    bad response Forbidden 403 (https://gems-ruby-china.b0.upaiyun.com/quick/Marshal.4.8/cocoapods-1.2.0.gemspec.rz)
这里必须翻墙啊。同志们
➜  MyNotes git:(master) ✗ pod --version
1.2.0
```
万能的翻墙软件蓝灯啊，要不然还是无法更新。到此我们cocoapods算是又复活了，开心
发现能够通过自己的力量去解决一个棘手的问题是多么开心的一件事.
又遇到了一个问题：
```shell
➜  MyNotes git:(master) ✗ pod install
Analyzing dependencies
[!] The dependency `FMDB (~> 2.6)` is not used in any concrete target.
```
通过搜索找到了解决办法，原因是因为cocoapods更新到最新版本以后，在Podfile文件中需要使用新的语法说明[url](http://blog.csdn.net/sjl_leaf/article/details/50506057)：
```objc
source 'https://github.com/CocoaPods/Specs.git'
platform:ios,'8.4'
def pods
 pod 'FMDB', '~> 2.6'
end
target 'MyNotes'
 pods
end
```
###2017.4.5号周三
####上午：继续学习IOS的相关知识点cocoapods和sqlite3
对于需要在当前进程中重复使用的实例，我们可以将该实例对象放在interface中，实例化方法放在对象方法中。
```objc
@interface FMDBDao(){
    FMDatabase *database;
}
@end
-(void)openDatabase{
    //设置文件名
    NSString *path = [NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES).firstObject stringByAppendingString:DBFILE_NAME];
    database = [FMDatabase databaseWithPath:path];
```
###2017.4.6号周四
####上午：继续晚上我的NOTE应用
这里想要模仿apple应用中的备忘录的功能app，需要存储在sqlite3中，并且进行分类，那么就涉及到两张表note表和type表，他们之间是有关联关系的。
设计表的时候需要预留字段，并且预留字段要有默认值设计
```sql
#define CREAT_TABLE_TYPE @"CREATE TABLE IF NOT EXISTS type(
cid integer primary key autoincrement, 
typename text,
note1 text default ' ',
note2 text default ' ')"
```
下面这两种的实现方式有什么不同之处呢？
```objc
@interface FMDBDao(){
FMDatabase *database;
}

@interface FMDBDao()
@property(nonatomic,strong) FMDatabase *database;
@end
```
###2017.4.7号周五
继续完善note应用的sqlite3存储
1.需要使用UIAlertController输入文件框，类似如下样式所得
![1416966955321003.png](http://upload-images.jianshu.io/upload_images/1397676-04e08669bba57ef6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2.并且需要验证输入的字符是否符合我们要求的规则，如果符合规则那么我们还需要传值给调用的controller来存储这个值，这里有一篇不错的文章[url](http://www.cocoachina.com/ios/20141126/10320.html)
```objc
UIAlertController *alertController = [UIAlertController alertControllerWithTitle:@"新建文件夹" message:@"请为此文件夹输入名称" preferredStyle:UIAlertControllerStyleAlert];
    [alertController addTextFieldWithConfigurationHandler:^(UITextField *textField){
        textField.placeholder = @"名称";
        //验证输入文字是否为空
        [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(alertTextFieldDidChange:) name:UITextFieldTextDidChangeNotification object:nil];
    }];
    UIAlertAction *cancelAction = [UIAlertAction actionWithTitle:@"取消" style:UIAlertActionStyleCancel handler:nil];
    UIAlertAction *saveAction = [UIAlertAction actionWithTitle:@"存储" style:UIAlertActionStyleDefault handler:^(UIAlertAction *action) {
        UITextField *fileName = alertController.textFields.firstObject;
        //传递数据
        NSDictionary *dict = @{@"filenName":fileName};
        [[NSNotificationCenter defaultCenter] postNotificationName:@"GetTypeInformation" object:nil userInfo:dict];
    }];
    [alertController addAction:cancelAction];
    [alertController addAction:saveAction];

//验证输入的信息是全的。
- (void)alertTextFieldDidChange:(NSNotification *)notification{
    UIAlertController *alertController = (UIAlertController *)self.presentedViewController;
    if (alertController) {
        UITextField *name = alertController.textFields.firstObject;
        UIAlertAction *saveAction = alertController.actions.lastObject;
        saveAction.enabled = name.text.length > 2;
    }
}
```
3.sqlite3所在的路径在哪里？还有命令如何操作？
3、输入 " cd /data/data/包名.项目名称（小写）/databases/ " （如： cd /data/data/com.keqi.test/databases/）进入项目文件所在的存储路径
　　4、可通过" ls "命令去查看该目录下的文件
　　5、输入" sqlite3 + 数据库名.db " (如：  " sqlite3 BookStore.db ") 打开数据库
　　6、可输入 " .table " 查看数据库中存在哪些表
　　7、可输入" .schema ' 查看建表语句
　　8、通过SQL查询语句 " select * from 表名 " （如：" select * from  Book "）
```shell
➜  ~ cd /Users/chen/Library/Developer/CoreSimulator/Devices/7CE01895-E381-400B-A704-E3B1D5F1E4A7/data/Containers/Data/Application/CFC6F06E-E6B3-4B0F-892D-4BA661CAAD5A/Documents
➜  Documents ls
Noteslist.plist
➜  Documents cd ..
➜  CFC6F06E-E6B3-4B0F-892D-4BA661CAAD5A sqlite3 DocumentsFMDB.sqlite 
SQLite version 3.8.5 2014-08-15 22:37:57
Enter ".help" for usage hints.
sqlite> .table
note  type
sqlite> select * from type
   ...> ;
1|test||
2|chen||
sqlite> 
```
4.sql语句不精通啊，内连接和外连接的区分真的适用于不同的场景啊，
原来的写法没法查出数据来，自己想了好多办法最后发现，原来一条数据就可以搞定了
```sql
//这是错误的写法，默认是交叉查询取并集的结果。
#define QUERY_TABLE_TYPE @"select a.tid,a.tname,count(b.cid) as num from type a , note b on a.tid = b.tid group by a.tid"
//这个是正确的方式：
#define QUERY_TABLE_TYPE @"select a.tid,a.tname,count(b.cid) as num from type a LEFT JOIN note b on a.tid = b.tid group by a.tid"
```
5.NSDictionary里面不能放整数类型吗？好奇怪啊，只能通过数据转换来处理。
```objc
 Note *note = [[Note alloc]initWithContent:dict[@"content"] andTid:[dict[@"tid"] integerValue]];
```
6.当我添加完成了一个类别下面的备忘了以后，我还想反向刷新我的tableview的list值。
做法就是再添加一个通知来接受添加备忘的响应。
```objc
//反向刷新list
    [[NSNotificationCenter defaultCenter]addObserver:self selector:@selector(reloadtableView) name:@"FreshInformation" object:nil];
```![输入图片说明](http://git.oschina.net/uploads/images/2017/0408/095524_7f43a9cf_370055.gif "在这里输入图片标题")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)