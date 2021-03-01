 ### 一些简单的说明
 - 所用的外设为乐福衡器有限公司生产的蓝牙体脂秤。
 - 由于需要蓝牙连接，Demo需要真机运行。
 - 如果需要体重值以外的信息需要输入身高、年龄、性别并且光脚上秤。
 - BLE文件夹下的代码对蓝牙的过滤、连接、数据解析做了一些简单的封装，最终外部通过BLEManager类进行调用。
 - HTBodyfat文件夹下的代码是对蓝牙外设拿到的阻抗值进行了一些计算，通过指定的方法传入阻抗值后你将会拿到对应的数据。
 - 所有的控制器都用storyboard创建，使用segue进行的传值。所有的storyboard都放在Main.stroyboard中
 
 ### DEMO的使用
 Demo的主页面如下图
 ![Simulator Screen Shot - iPhone 8 - 2018-07-30 at 16.54.09.png](https://upload-images.jianshu.io/upload_images/3340980-77711ad721df2036.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 
 
 - 点击 **绑定设备** 按钮会跳转到BindingDeviceViewController，在这个控制器在被实例化后会开始扫描附近的外设，并将您的外设做一个记录。
 
 - 点击 **上秤称重** 按钮会跳转到ConnectDeviceViewController， 这个控制器在被实例化后也会开始扫描附近的外设，通过过滤去连接已绑定过的设备。所以只有被绑定过后才能去进行上秤称重，否则无法接收到数据。
 
 - 点击 **设备管理** 按钮会跳转到DeviceListViewController， 这个控制器会用列表的方式展示你在“绑定设备”页面绑定的外设。你可以通过右滑的方式去删除已绑定设备。
 
 - 在“绑定设备”和“上秤称重”页面接收到外设返回的数据后，会自动停止扫描并断开与外设的连接，然后把数据通过回调的方式传回“主页信息”更新体重一栏，具体的数据可以去”数据详情“页查看。
 
 - 点击 **数据详情** 按钮会跳转到BodyDetailViewController，在这个控制器会用列表的方式展示HTBodyfat_NewSDK对象中的属性，如果没有测量到阻抗值这个列表中的数据会为空。
 
 ###BLEManager提供的方法
 BLEManager是一个单例对象，保证你在不同控制器中调用的时候蓝牙的状态是一致的。
 
 ```
 /**
 实例化方法
 
 @return 单例对象
 */
 + (instancetype)shareInstance;
 
 ```
 由于我们的外设是体脂秤所以您必须穿入用户的身体信息才能进行测量，如果您不传入这些信息或者传入的信息有误，将无法得到HTBodyfat_NewSDK对象，只会得到一个BLEProgressDataModel对象。
 
 ```
 /**
 初始化用户的数据
 
 @param height 用户身高  cm
 @param sex 用户性别
 @param unit 用户当前使用的单位
 @param age 用户年龄
 */
 - (void)initWithUserHeight:(NSInteger)height sex:(NSInteger) sex unit:(NSInteger)unit age:(NSInteger)age;
 ```
 
 开始搜索/连接已有设备的方法最终的数据都会在回调中已对象的方式返回，你可以根据自己的需要使用。
 ```
 /**
 开始搜索/连接已有设备
 
 @param isBinding 是否为绑定
 @param progressDataHandle 过程数据回调
 @param lockDataHandle 锁定数据回调
 @param historyDataHandle 历史数据回调
 */
 - (void)startSearchingPeripheralWithIsBinding:(BOOL)isBinding progressDataHandle:(progressDataHandle)progressDataHandle lockDataHandle:(lockDataHandle)lockDataHandle historyDataHandle:(historyDataHandle)historyDataHandle;
 ```
 
 停止搜索
 ```
 /**
 停止搜索
 */
 - (void)stopScan;
 
 ```
 
 重新开启搜索
 ```
 /**
 重新开启搜索
 */
 - (void)reStartScan;
 ```
 
 断开当前链接的蓝牙设备
 ```
 /**
 断开当前链接的蓝牙设备
 
 */
 - (void)disconnectPeripheral:(CBPeripheral *)peripheral;
 ```
 
 BLEManger已经为你做了设备管理的逻辑，当你去连接外设的时候在绑定状态下会过滤掉deviceList中的设备 通过macAddress,在连接状态下会过滤掉非deviceList中的设备 通过macAddress。
 
 通过这个方法你可以拿到绑定设备的列表
 ```
 /**
 绑定设备列表
 */
 + (NSArray   *)deviceList;
 ```
 
 在保存的时候你需要传入一个设备列表的数组，这里主要是考虑到由于你的业务逻辑，可能你需要自己去维护一份设备列表，不论是添加还是删除设备都直接对BLEManager的设备列表进行一次替换。
 ```
 /**
 保存设备到设备列表
 */
 + (void)saveDeviceArr:(NSArray  *)modelArr;
 ```
 
 删除所有设备
 ```
 /**
 删除所有设备
 */
 + (void)deleteAllDeviceArr;
 ```
 
 给当前连接的设备发消息
 ```
 /**
 给当前连接的设备发消息
 
 */
 - (void)writeData:(NSData *)data toPeripheral:(CBPeripheral *)peripheral;
 ```
 
 ###BLEManager的使用
 
 首先先讲一下BLEManager的结构：
 ![image.png](https://upload-images.jianshu.io/upload_images/3340980-98f0ce7eafb6acb5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 BLEManager 作为一个管理类把BLEConnect返回的外设的原始数据经过BLEDataHandle的处理抛到最外层，使用者可以不用关心整个内部的实现过程，同时通过BLEDeviceManager对外设进行管理。
 
 这里主要说一下如何去增加或者修改需要过滤的外设的名称。
 在BLEDefine.h中定义了一些外设的名称。
 ```
 #define kBLEDeviceEnergyScale @"Energy Scale"
 #define kBLEDeviceHealthScale @"Health Scale"
 #define kBLEDeviceADore @"ADORE"
 #define kBLEDeviceLFScale @"LFScale"
 ```
 这些名称在BLEConnectFilter.plist中有对应的数据解析的协议，这个是与硬件工程师已经约定好的，在经过BLEConnectFilter的过滤后，BLEProtocoHandle会使用对应的协议方案对外设返回的原始数据进行组装。如果你需要修改蓝牙名称，在确定是同一套蓝牙协议方案的情况下，直接修改BLEDefine.h和BLEConnectFilter.plist的名称即可。
 ![image.png](https://upload-images.jianshu.io/upload_images/3340980-9e68d8e5c0f6ce90.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 
 具体的方法调用和逻辑可以参考BindingDeviceViewController和ConnectDeviceViewController中的代码。
 
 ```
 - (void)viewDidLoad {
 [super viewDidLoad];
 self.bleConnectStateLabel.text = @"未连接";
 [[BLEManager shareInstance] initWithUserHeight:self.height sex:self.sex unit:self.unit age:self.age];
 [[BLEManager shareInstance] startSearchingPeripheralWithIsBinding:NO progressDataHandle:^(BLEProgressDataModel *progressDataModel, CBPeripheral *peripheral) {
 self.peripheral = peripheral;
 self.currentWeightLabel.text = [UnitTool weight:progressDataModel.weight withUnit:self.unit];
 self.bleConnectStateLabel.text = @"已连接";
 } lockDataHandle:^(BOOL isBodyFatModel, HTBodyfat_NewSDK *bodyFatModel, BLEProgressDataModel *progressDataModel, BLEDeviceModel *deviceModel, CBPeripheral *peripheral) {
 self.peripheral = peripheral;
 self.BodyDataHandler(isBodyFatModel, bodyFatModel, progressDataModel);
 [[BLEManager shareInstance] disconnectPeripheral:self.peripheral];
 [self.navigationController popViewControllerAnimated:YES];
 } historyDataHandle:^(BOOL isBodyFatModel, NSInteger impedance, CGFloat weight, BLEDeviceModel *deviceModel, CBPeripheral *peripheral, NSString *dateStr, BOOL isFinish) {
 }];
 }
 
 - (void)viewWillDisappear:(BOOL)animated{
 [super viewWillDisappear:animated];
 [[BLEManager shareInstance] disconnectPeripheral:self.peripheral];
 }
 ```
 方法调用起来很简单
 1. 初始化用户信息
 2. 扫描外设并且在回调中去处理业务逻辑
 3. 收到锁定数据后断开连接
 
 ```
 [[BLEManager shareInstance] startSearchingPeripheralWithIsBinding:NO progressDataHandle:^(BLEProgressDataModel *progressDataModel, CBPeripheral *peripheral) {
 
 } lockDataHandle:^(BOOL isBodyFatModel, HTBodyfat_NewSDK *bodyFatModel, BLEProgressDataModel *progressDataModel, BLEDeviceModel *deviceModel, CBPeripheral *peripheral) {
 
 } historyDataHandle:^(BOOL isBodyFatModel, NSInteger impedance, CGFloat weight, BLEDeviceModel *deviceModel, CBPeripheral *peripheral, NSString *dateStr, BOOL isFinish) {
 }];
 ```
 上面这个方法中progressDataHandle返回的是称重过程中的数据，lockDataHandle是锁定数据，由于用户可能没有传入身高性别等信息，所以HTBodyfat_NewSDK对象可能是为nil，historyDataHandle是带有历史数据功能的秤才会走的回调，如果你所选的型号支持读取历史数据功能，那么会走这个回调。
 
 
 
 
 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)